The AI Agent Protocols (ai-agent-proto) Working Group is about defining a protocol framework enabling various interactions between AI Agents over a secure multiplexed transport. AI agent is an autonomous, adaptive intelligent software system that uses AI models to complete a specific task. To complete the task on behalf of a human user or another AI agent, it makes decisions, executes actions, and interacts with other AI agents and tools. Unlike traditional software workloads that follow fixed execution paths, an AI Agent dynamically determines at run time which actions to take, which tools to invoke, and which agents to collaborate with, based on reasoning over its goals and context.

With the expansion of communication over the Internet between AI Agents and external resources (tools, AI Agents), communication reliability across platforms and vendors becomes increasingly important. The role of this working group is to facilitate such interoperability.

Several considerations arise which are unique to AI Agent protocols, which are a focus of activity for protocol development:

* AI Agents possess unique and differentiated skills that play a significant role in supporting collaborative tasks, which brings new considerations for how these specialized capabilities can be leveraged to, the selection of AI agents, initiate communication and facilitate cross-domain interactions even within enterprise intranet and on the Internet.

* Interactions of AI Agents with other AI Agents and tools can be long lived, make use of the exchange of significant amounts of context across various modes of communication (such as text, audio, and video interactions), and may require very low latency. 
This introduces new considerations around reliability, transport session management, and data transport.

* To protect data exchanged between AI Agents (and between AI Agents and tools) over potentially untrusted networks, particularly when handling sensitive information (such as personal data or conversational context), mechanisms are required to establish and verify identity, ensure confidentiality, integrity, authenticity of the exchanged data and delegated authorization across AI Agent chains. This introduces new considerations around protocol-level security and privacy mechanisms.

The scope of the working group is the agent-to-agent and agent-to-tools communication protocols. The working group will work on describing use cases for this scope and deriving the protocol requirements from the use cases.

The working group will also define the framework for agent-to-agent and agent-to-tool interactions, describe the associated protocol suite, and outline the framework’s functional blocks, their relationships, and mechanisms for structured, semi-structured, and multi-modal information exchange to support collaborative tasks across domains. It will also address session management for agents, including setup, updates, and termination related to task execution.

The following topics are explicitly out of scope for this working group:
*	Definition of AI models, agent reasoning algorithms, tool-specific business logic, AI agent behavioral security (e.g., agent Hallucination), or AI agent result validation.
*	Standardization of agent behavior, decision-making, or planning semantics.


The working group will produce the following deliverables:

1) Groundwork will be documented through a set of informational Internet-Drafts, which include the following key components:
* Use cases focusing on Agent-to-agent communications, Agent-to-tool communications.

* A gap analysis and requirements document that examines existing defacto protocols implemented in open-source project(s), and derives necessary protocol requirements.

2) A standard track AI Agent protocol framework overview: 

This work encompasses defining a framework by identifying key  building blocks and detailing the protocol suite for interoperable Agent-to- agent/Agent-to-tool communications. This framework document is intended as an architectural overview and will identify areas for subsequent protocol specification work. This protocol framework will enable the AI Agents to select and collaborate with other AI Agents on the Internet (deployed in various interconnected domains and ecosystem) to execute simple or complex tasks. It will allow multi-modal collaboration, i.e., using varied data formats such as text, images, video, audio, and structured data with exchange of multi-modal contexts. It will provide timed (short or long-lived) session management, enabling the establishment, update, context handling, and termination of the services of interacting agents and tools in a secure and privacy preserving way.

The working group will consider existing defacto agent communication protocols and frameworks (such as the A2A protocol currently or MCP protocols specified under the auspices of the Linux Foundation) to achieve this objective.

This working group is expected to closely coordinate with other related IETF working groups, such as Web Authorization Protocol (OAuth), webbotauth, WIMSE, on security considerations, WebTransport, MoQ, QUIC, TSVWG on data transport and Int INT area, OPS area for discovery. If the working group needs any changes to or extensions of protocols specified by other working groups, those issues will be raised with the relevant working groups for decisions on how best to handle them. The group is also expected to have close communication with opensource projects running under Linux Foundation. 
