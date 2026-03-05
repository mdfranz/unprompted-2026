# Defensive AI to Combat AI Attacks

To combat the rising speed and scale of AI-assisted attackers—who are now capable of executing operations like an 8-minute escalation from stolen credentials to full AWS admin—defenders are deploying autonomous AI systems across the entire security lifecycle. Rather than relying solely on static signatures, the industry is shifting toward multi-agent architectures to discover zero-days, automate threat hunting, map threat intelligence, and trap adversaries based on behavioral anomalies.

**1. Autonomous Vulnerability Discovery & Remediation (AppSec)**
AI is moving beyond finding shallow bugs to replicating the deep reasoning of expert vulnerability researchers.
*   **Deep Zero-Day Hunting:** Systems like Google’s "Big Sleep" use an agentic reasoning loop equipped with debuggers, code browsers, and Python interpreters to formulate and test hypotheses, successfully finding deeply embedded memory safety bugs in mature projects like the Linux kernel and SQLite. Similarly, AISLE's AI system recently discovered 12 zero-days in OpenSSL, some of which had been hiding for decades.
*   **Scaling with Multi-Scanner Validation:** TrendAI’s FENRIR system scales this capability to an organizational level by using a multi-stage cascade that combines static analysis tools with two tiers of LLM validation. This architecture eliminates over 90% of false positives before human review, allowing the AI to generate proofs-of-concept and validate exploits in Docker sandboxes.
*   **Exploiting Logic and Auth Flaws:** Traditional scanners fail at finding bespoke business logic and access control (AuthN/AuthZ) flaws. Security firms like XBOW are using AI agents to navigate web applications with low-privilege credentials and attempting to produce high-privilege responses. A secondary "validator" AI checks if the agent successfully reverse-engineered the application's state, eliminating false positives.
*   **Automated Remediation:** Instead of just finding bugs, AI is being used to fix them. Google’s CodeMender acts as an end-to-end patching engine that generates patch candidates, fuzzes the code to ensure functionality isn't broken, and performs formal verification to prove the vulnerability is remediated.

**2. Accelerating Threat Hunting and SOC Operations**
Security Operations Centers (SOCs) are overwhelmed by telemetry, so organizations are using AI orchestrators to navigate massive data schemas.
*   **Multi-Agent Query Generation:** At Datadog, the "Hunting Copilot" utilizes a multi-agent framework to translate a threat hunter's natural language hypothesis into complex log queries. It automatically explores the schema of massive data sources, executes the queries against real logs via a Model Context Protocol (MCP) server, and iteratively refines syntax errors. 
*   **Autonomous Alert Triage:** Wiz has deployed fully autonomous AI agents in production that investigate cloud and Kubernetes threats from the initial alert all the way to a verdict, processing thousands of investigations daily at 10x the speed of human analysts. 
*   **Incident Triage Engines:** For internet-scale data leaks, responders are moving from simple scrapers to multi-agent triage engines that can parallelize victimology and automate the analysis of leaked secrets and their impact.

**3. Graph-Driven Threat Intelligence**
Threat intelligence reports are too dense to parse manually at scale. AI agents are being deployed to traverse complex knowledge graphs to extract actionable intelligence. 
*   An LLM agent can start at a pivot point (e.g., a specific threat actor like APT28) and walk the graph to find related malware, aliases, and specific ingress tools used in historical campaigns.
*   Systems like TrendAI's MIMIR use dozens of autonomous agents to constantly monitor vulnerability disclosures (N-days). When a vendor advisory drops, the agents scan the code commits and automatically generate detection rules (like Sigma or YARA) for the SOC.

**4. Behavioral Anomaly Detection & "Active Trapping"**
Because AI-assisted attackers operate at machine speed but lack context about a target's internal environment, their attacks exhibit a behavioral "accent" that defenders can exploit.
*   **Topology and Identity Traps:** Defenders are deploying realistic "honey tokens" (fake credentials and repositories) that match internal naming conventions. Because a fast-moving AI attacker cannot differentiate real infrastructure from fake infrastructure, it will inevitably touch these traps, generating a zero-false-positive alert.
*   **Enforcing Environmental Context:** Defenders can build "cheap verifiers" that trigger alerts anytime an entity attempts to assume a role or clone a repository that does not strictly conform to the organization's unique, organic naming conventions—which the attacker's AI training data cannot predict.
*   **Multi-Layered Baselining & Auto-Containment:** Security teams at organizations like Salesforce are establishing behavioral baselines that monitor activity across three layers: the User, the Agent, and the Organization. By pushing these baselines to a high-speed cache, the system can perform real-time inference. If anomalous behavior hits a critical threshold, the system initiates auto-containment—instantly revoking tokens or locking down the

# Cat and Mouse of AI Security

The "cat-and-mouse" analogy describes the endless, fundamentally futile cycle of defenders (the cat) deploying reactive guardrails to catch evolving, sophisticated AI attacks (the mouse). In the context of generative AI security, this analogy is used to illustrate the failure of trying to secure Large Language Models (LLMs) through prompt filtering, and to argue for a paradigm shift toward structural security.

The sources develop this analogy by breaking down why the "cat" is always a step behind and how the industry can escape the chase:

**The Mechanics of the Game (The Guardrail Fallacy)**
Nicolas Lidzborski explains that playing cat-and-mouse with threat actors is a losing game because it relies on reactive, syntactic filtering—what he calls the "Guardrail Fallacy". Defenders attempt to build a wall, but attackers easily bypass it using semantic and multimodal shifts:
*   **Static Filters Fail:** Defenders write blocklists or regular expressions, but attackers easily defeat them using simple textual obfuscation like Base64, Hex strings, or ROT13 encoding, which the LLM understands but the filter misses.
*   **ML Classifiers are Fragile:** Defenders deploy secondary Machine Learning classifiers to catch bad prompts, but attackers bypass these by swapping synonyms, adding adversarial suffixes, or translating the payload into low-resource languages.
*   **Multimodal Evasion:** Attackers bypass text-only filters entirely by hiding malicious instructions inside image metadata or using Optical Character Recognition (OCR) evasion. 

Because the LLM's interface is natural language rather than deterministic code, attackers can continuously invent new evasion techniques, ensuring the reactive defender remains "always a step behind". 

**The Vicious Cycle of Evaluation**
Ilia Shumailov develops the analogy further, describing a "cat-and-mouse cycle" of unprincipled defenses that currently haunts the AI industry. He notes that the industry is stuck in a loop where defenses are evaluated on static, held-out datasets and appear highly secure. However, once pushed to production, attackers break these systems within hours using stronger, general attacks like genetic algorithms. This traps the industry in a vicious cycle: "we can't build good defenses because we don't have good attacks, and we don't know how good our attacks are because we don't have good defenses". 

**Escaping the Chase**
The consensus among the presenters is that the AI security industry must fundamentally abandon the cat-and-mouse game. 
*   **Structural Enforcement:** Lidzborski argues for a shift away from prompt engineering and filtering toward a "semantic sandbox". Rather than trying to filter every bad word or malicious intent, organizations should implement structural boundaries, such as stripping hidden text before the LLM sees it, and using stateful policy engines that deterministically forbid an agent from taking a dangerous action (like making a web request) after it has accessed sensitive data.
*   **Principled Guarantees:** Shumailov argues that the industry must move beyond probabilistic anomaly detection and deploy AI with principled, non-probabilistic security guarantees. By implementing mechanisms akin to Control Flow Integrity (CFI) in traditional software—which mathematically force the agent to follow a fixed control flow regardless of the data it ingests—defenders can definitively break the cat-and-mouse cycle.