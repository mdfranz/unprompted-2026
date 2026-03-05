# Agentic AI Security and Defense

This repository contains a collection of research, strategies, and architectural patterns for securing autonomous AI agents and building "AI-native" security operations. The documentation explores the shift from reactive guardrails to structural security, the evolution of the Agentic SOC, and the governance of autonomous systems.

## 📑 Contents

### Documentation
*   **[Agentic Defense Priorities](agentic-defense-priorities.md)**: A multi-layered framework for defending agentic systems, prioritizing structural authorization, execution boundaries, and "Plan-Validate-Execute" paradigms over simple prompt filtering.
*   **[Ideal Agentic Organization](agentic-org.md)**: A vision for Level 3 AI-native enterprises, covering culture shifts, modular agent fleets (using MCP), and compounding expertise through skills repositories. Includes insights from the Trail of Bits transition.
*   **[Defensive AI vs. AI Attacks](attack-vs-defend.md)**: An analysis of how defenders are using autonomous vulnerability discovery, multi-agent threat hunting, and behavioral "active traps" to combat machine-speed attackers.
*   **[The Cat and Mouse of AI Security](attack-vs-defend.md#cat-and-mouse-of-ai-security)**: Explores the "Guardrail Fallacy" and the need for principled, non-probabilistic security guarantees to break the cycle of reactive defenses.
*   **[Blue Team & Agentic SOC](blue-team.md)**: A deep dive into multi-agent orchestrator-expert frameworks, field discovery via Model Context Protocol (MCP), and building automated threat knowledge graphs.
*   **[Governance](governance.md)**: Challenges in governing non-deterministic agents, managing "Shadow AI," and strategies for feature-based enablement and tiered risk ownership.

### Visuals
*   **Intent Detection**: Concepts for identifying malicious intent within agentic reasoning loops.
*   **Prompt Injections**: Illustrating the mechanics of injection attacks and the failure of syntactic filters.
*   **Agentic SOC**: Architectural diagrams for modern, agent-augmented Security Operations Centers.

## 🛠 Key Concepts

*   **Subtractive Delegation (Warrants)**: Treating agent authority as ephemeral, task-scoped cryptographic grants that naturally expire and monotonically attenuate.
*   **Model Context Protocol (MCP)**: The standard for securely connecting agents to internal data and tools.
*   **Plan-Validate-Execute**: A safety paradigm where high-stakes actions are paused for human-in-the-loop verification.
*   **Structural Sandboxing**: Moving defense from the "soft" prompt layer to the "hard" execution and network egress layers.

---
*Note: This documentation is part of the Unprompted 2026 research series on the future of autonomous agent security.*
