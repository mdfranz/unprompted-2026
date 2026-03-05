# Governance

The transition to Agentic AI requires a fundamental shift in how organizations approach governance. Traditional enterprise security was built for static, deterministic software with clear boundaries. However, autonomous agents act dynamically, requiring governance to evolve at the same velocity as the AI itself.

Here is a summary of the primary challenges and opportunities in governing AI agents and applications, based on the sources:

### **Major Governance Challenges**

*   **Pace of Innovation vs. Review Cycles:** AI adoption and feature velocity outpace traditional enterprise procurement and security review cadences. Vendors ship new capabilities weekly, meaning the management plane and enterprise controls often lag dangerously behind the tools' capabilities.
*   **Blurred Boundaries & Non-Determinism:** AI agents collapse traditional control planes (endpoint, network, cloud, SaaS) into a single action. An agent can generate code, make system calls, and execute network requests in one non-deterministic execution loop, making static rule-based governance ineffective.
*   **Shadow AI and Visibility Sprawl:** If governance is too restrictive, employees bypass it by using personal credit cards for unauthorized AI tools (Shadow AI), leaving the enterprise with zero visibility and an expanding attack surface. Because "you cannot govern what you cannot see," obtaining visibility is a primary hurdle.
*   **Accountability and Liability:** As agents operate with increasing autonomy, it becomes difficult to anchor accountability. Determining who is responsible for an agent's hallucination or a vulnerability introduced by "vibe-coded" applications—the developer, the platform, or the user—remains a legally murky area.
*   **Kinetic Risk in Physical AI:** Existing governance frameworks like the NIST AI RMF or EU AI Act fail when applied to embodied/physical AI (like robotics or drones). In physical AI, human-in-the-loop oversight is too slow to stop irreversible damage, as errors manifest as kinetic force before humans can intervene.
*   **Approval Fatigue:** Relying heavily on humans to review and approve every high-stakes agentic action (Plan-Validate-Execute) can quickly lead to "review fatigue" and rubber-stamping, defeating the purpose of the control.

### **Opportunities and Modern Governance Strategies**

Despite these challenges, organizations have the opportunity to build foundational governance that scales securely alongside innovation. 

*   **Tiered, Cross-Functional Risk Ownership:** Governance can no longer be solely an IT or Security problem. Organizations are seeing success by establishing cross-functional Enterprise AI Steering Committees (including Legal, HR, IT, and Business Execs) to shift from reactive IT approvals to proactive, business-level risk ownership. FFF Enterprises, for example, successfully implemented a tiered model: an executive committee for high-risk use cases, a Center of Excellence for standardized practices, and domain-level boards for low-risk needs.
*   **Constrain Execution, Not Innovation:** The goal of governance is not to block AI, which only encourages shadow usage, but to bound its execution authority. Opportunities lie in utilizing capability-based authorization, sandboxing, and strict network egress reviews to ensure an agent cannot do more than what the user authorized, even if it hallucinates.
*   **Feature-Based and Granular Enablement:** Organizations have the opportunity to govern at the feature level rather than the product level. For example, a company can enable core AI chat and tenant-contained collaboration, while gating high-risk features like autonomous web research or unverified third-party integrations until proper controls are established.
*   **Controlled Experimentation Zones:** Governance teams can safely enable innovation by building specific, isolated environments for AI experimentation, complete with test tenants and synthetic data, so developers can test workflows without risking production systems.
*   **Standardized Intake and Rationalization:** Organizations can streamline governance by creating structured intake processes and scorecards that evaluate the true business value versus the risk of proposed AI projects. Furthermore, centralizing AI procurement allows companies to rationalize tools, eliminating redundant applications to reduce the attack surface.
*   **Improving Systems of Record:** If governed correctly, some AI agents provide a net benefit to enterprise risk management. For example, properly secured AI notetakers offer the opportunity to finally serve as reliable, impartial systems of record for incident response and corporate decision-making.