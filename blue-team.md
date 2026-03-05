# Blue Deep Deep Dive
# Blue Team and AI


**Deep Dive: The Agentic Security Operations Center (SOC)**

The transition from traditional SOCs to "Agentic SOCs" involves shifting from static playbooks to digital teammates that can reason, plan, and execute within existing infrastructure.

*   **Evolution from Single Agents to Multi-Agent Orchestrators:** 
    Early attempts at AI threat hunting often relied on single agents. For example, Datadog’s V1 "Hunting Copilot" generated hypotheses and queries fast, but suffered a 25% syntax error rate and aggressive, noisy hypothesis production. To fix this, they shifted to a multi-agent **"Orchestrator-Expert" framework** paired with reasoning models like GPT-o1. The orchestrator manages the investigation, expert sub-agents gather specific documentation (e.g., AWS CloudTrail vs. GCP Audit Logs), and a Datadog Agent wrapper executes and iteratively refines queries directly against the telemetry. 
*   **Data-Driven Field Discovery via MCP:** 
    A major realization at Datadog was that documentation is often insufficient for writing accurate queries due to custom, varying log schemas across 450 days of telemetry. They shifted the AI's focus to **field discovery**—letting the agent run broad queries, sample the actual log values via a Model Context Protocol (MCP) server, and iteratively refine its syntax. The Datadog MCP server returns concise corrections when queries fail, which boosted syntax accuracy by 17% (up to 92%).
*   **Integrating with Existing Infrastructure:**
    Firms like Salesforce emphasize that an Agentic SOC does not require replacing existing tools. They built their agentic layer directly on top of their existing Security Orchestration, Automation, and Response (SOAR) platform, which already had 257 Python integrations.
*   **"Digital Teammates" and Agent Cards:**
    Salesforce treats their AI agents as first-class team members operating in Slack alongside humans. Each agent is governed by an **"Agent Card"** that strictly defines its persona, objectives, token limits, allowed capabilities (tools), and PII masking rules to prevent scope creep. 
    *   *Workflow Example:* When a threat intel report is shared in Slack, a "Normalizer" agent extracts the Indicators of Compromise (IOCs). A "Hunt Planning" agent then formulates a hypothesis and builds a plan to search the SIEM. After a human explicitly approves the potentially high-risk actions, specialist agents automatically write detection rules, contain affected hosts via CrowdStrike, and spin up incident command channels.

**Deep Dive: AI-Powered Threat Intelligence (TI)**

Threat intelligence is historically bottled up in unstructured, dense OSINT reports (taking humans 10+ minutes to read) or stripped of context in raw indicator feeds. AI is being used to bridge this gap by converting unstructured text into highly contextual, queryable formats.

*   **Building the Threat Knowledge Graph:**
    Palo Alto Networks uses multi-step LLM extraction to convert dense reports into semi-structured knowledge graphs. From a single medium-length report, the AI can extract over 100 distinct entities and relationships. To do this reliably, a "skeleton extractor" acts as a router, identifying valuable information and sending it to specialized extraction components. 
*   **Self-Correcting MITRE Framework Mapping:**
    Because LLMs often suffer from "fuzzy recall" when trying to map observed behaviors to specific MITRE ATT&CK techniques, the extraction pipeline uses a multi-step verification process. The LLM extracts the attacker behavior, generates candidate MITRE patterns, reads the actual MITRE knowledge base entries, and then corrects itself to land on the precise, authoritative attack pattern. 
*   **Agent-Driven Multi-Hop Traversal:**
    Once the knowledge graph is built, AI agents navigate it exactly like human researchers. If a user asks, "What vulnerabilities does APT28 exploit, and who else is exploiting them?", the agent starts at the APT28 node, looks up known aliases, hops to the associated vulnerabilities, and then performs a second hop to identify other threat actors linked to those same vulnerabilities. The agent outputs a full investigation graph, citing specific nodes so every claim is grounded in curated reports rather than LLM hallucinations.
*   **Automated Rule Generation at Scale:**
    Other organizations, like TrendAI, deploy massive multi-agent systems (like their MIMIR platform, featuring 23+ autonomous LangGraph agents) to constantly stream and ingest CVEs, vendor advisories, and CISA alerts. These agents automatically classify the threats across 52 sub-verticals and actively generate ready-to-deploy Sigma, Snort, and YARA detection rules, directly feeding active zero-day hunting priorities.
