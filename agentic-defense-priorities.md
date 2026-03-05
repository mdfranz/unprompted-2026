# Agentic Defense Layers/Priorities


**Priority 1: Structural Authorization and Execution Boundaries (The Ultimate Failsafe)**
Because probabilistic content filters will eventually be bypassed, the most effective defenses isolate the agent at the execution layer. Even if an agent is successfully compromised via prompt injection, these controls mathematically or structurally freeze its blast radius,.
*   **Subtractive Delegation (Warrants):** Instead of relying on static identity roles, treat agent authority as ephemeral, cryptographic warrants. These warrants are task-scoped, tied to a specific tool and holder, and naturally expire. Crucially, as an orchestrator agent delegates tasks to sub-agents, the capabilities, constraints, and time-to-live can only shrink (Monotonic Attenuation), guaranteeing a compromised sub-agent cannot escalate privileges,.
*   **Strict Egress Controls:** To break the "lethal trifecta" (untrusted content + private data + external communication), organizations must tag agentic services and proxy their connections out of sandboxes,. CI-time checks should mandate strict egress reviews, ensuring agents cannot independently ship harvested data to arbitrary internet destinations,.
*   **Deterministic Policy Engines (Cedar):** Use fast, verifiable policy languages like Cedar to act as a tamper-proof Reference Monitor,. This allows for stateful, cross-turn policy enforcement, such as tracking "tainted" data provenance (e.g., PII) and dynamically blocking the agent from calling a network tool if that sensitive data is in its context.
*   **Capability Bounding & Memory Isolation:** Restrict agents with explicit per-agent tool allowlists and scoped permissions (e.g., READ vs. WRITE),. Furthermore, isolate agent memory into distinct namespaces so cross-contamination between tasks is minimized,.

**Priority 2: The "Plan-Validate-Execute" Paradigm & Auto-Containment**
Autonomy must be broken when an agent attempts a sensitive, irreversible action (e.g., a production write, sharing data externally, or broadcasting communications),.
*   **Human-in-the-Loop Interception:** Implement a checkpoint where high-stakes actions are paused and a verifiable human identity must explicitly approve the business justification before execution,,. To prevent "approval fatigue" and rubber-stamping, utilize batching queues and optimistic writes with easy revert capabilities,.
*   **Real-Time Execution Auto-Containment:** Instead of relying on slow, complex log parsing, establish statistical baselines of "normal" behavior based on simple telemetry (e.g., API invocation counts, sensitive asset rarity),. If an agent hits a critical deviation threshold in real-time, the system should automatically kill the session, revoke the token, or lock down the specific tool skill before a SOC analyst even reviews it,.

**Priority 3: Advanced Observability and Active Traps**
Defenders hold the home-field advantage. By laying traps and properly linking telemetry, you can spot hijacked agents during their discovery phase.
*   **Identity Multiplexing:** Standard logs are insufficient because they separate "User Action" from "Agent Logic". You must inject the `botId`, `sessionContext`, and `traceId` into every execution log so you can explicitly tie autonomous system calls back to the invoking human and spot "abuse of legitimate agency",.
*   **Honey Tokens and Topology Traps:** Deploy fake identities, canaries, and credentials that perfectly match your internal naming conventions. Because a hijacked AI operates at machine speed and lacks contextual awareness, it will inevitably touch these fake assets or attempt to query non-existent resources,,. This provides a zero-false-positive, deterministic alert,.
*   **Context-Aware Trimming:** When an agent's context window fills up, ensure that permission denials, blocked Server-Side Request Forgery (SSRF) attempts, and security warnings are "pinned" and survive trimming. Otherwise, an attacker can simply wait for the context to clear and retry the exact same exploit,.

**Priority 4: Input/Output Hardening and Defense-in-Depth (The "Soft" Guardrails)**
While attackers can obfuscate syntax to bypass filters, layered input/output sanitization remains a critical frontline defense to reduce the sheer volume of noise,.
*   **Pre-Processing & Visible Content Only:** Strip out HTML comments, hidden text, and invisible elements before the LLM ever sees the prompt. If the user can't see it, the agent shouldn't parse it,.
*   **Layered Classification Pipelines:** Use a tiered approach to evaluate inputs. Start with cheap string-matching (e.g., YARA rules), fall back to semantic similarity checks, and route complex/untrusted inputs through fine-tuned ML classifiers or an LLM backstop to catch novel prompt injection strategies,,,.
*   **Structural Prompt Hierarchy:** Use non-dictionary "Sentinel Tokens" to encapsulate untrusted data, and embed repeated prompt reinforcement (anchors) to constantly refocus the LLM on its core instructions and tell it to ignore imperative commands found in the data payload.
*   **Output Sanitization:** Dynamically scrub markdown, trace and verify URLs through Safe Browsing classifiers to block malicious redirects, and scrub ungrounded URLs to prevent the agent from fulfilling hallucinated exfiltration requests.

**Priority 5: Underlying Infrastructure & Model Baselines**
*   **Upgrade to Frontier Models:** The resistance to prompt injection improves dramatically with the newest models. For example, moving from Opus 4.5 to Opus 4.6 dropped injection success rates from over 16% to under 3%,.
*   **Confidential Computing:** Run orchestration layers, Retrieval-Augmented Generation (RAG), and MCP servers inside hardware-attested Confidential Virtual Machines (CVMs) to protect memory and prevent data tampering from malware or privileged insiders,.
