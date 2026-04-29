# Agent Communication Protocols (acp) Proposed Charter

The Agent Communication Protocols (acp) Working Group will work on defining protocol building blocks for enabling interoperability for AI Agent applications across the Internet. An AI agent is an autonomous, adaptive intelligent software system that uses AI models to complete a specific task. AI Agents often interact with users via chat or voice, performing tasks based on the flow of the conversation. To complete tasks on behalf of a human user or another AI agent, they can independently make decisions, execute actions, and interact with other AI agents and tools.

With the expansion of communication over the Internet between AI Agents and external resources that can be tools or other AI Agents, reliable communications across platforms and vendors becomes increasingly important. The role of the acp working group is to facilitate such interoperability so that tools and agents can be provided by multiple vendors.

# Key Considerations

There are several considerations that are unique to AI Agent applications that need to be addressed while working on developing the building blocks:

- AI Agents act as autonomous software entities that need to be authenticated independently of the users they represent. Establishing verifiable agent identity that is distinct from user identity is a prerequisite for meaningful authorization and accountability. 

- Interactions of AI Agents with users, other AI Agents, and tools can be long-lived, utilize significant amounts of context across various modes (text, audio, video), and require very low latency (including fast barge/interruption times). This introduces new considerations around reliability, transport session management, and data transport.

- To protect data exchanged between AI Agents (and between AI Agents and tools) over potentially untrusted networks, particularly when handling sensitive information (such as personal data or conversational context), mechanisms are required to establish and verify identity, ensure confidentiality, integrity, authenticity of the exchanged data, selective disclosure and delegated authorization across AI Agent chains. This introduces new considerations around protocol-level security and privacy mechanisms.

Since AI agents can operate independently, and their LLMs can hallucinate, including the hallucination of tool use. This introduces risk when an AI Agent erroneously performs actions on a user's behalf. Techniques for mitigation—primarily through verifiable user approvals are critical.

The scope of the working group is agent-to-agent and agent-to-tools communication protocols. The working group will document common use-cases to derive requirements for the protocol.

# Deliverables

The working group will produce the following standards track and informational documents:

1. An AI Agent session protocol for creation and maintenance of long-lived sessions between AI agents, or between AI agents and tools. These sessions allow for the bidirectional exchange of data, incuding model context, tool call results, and chat messages.

This protocol will facilitate highly scalable and reliable session management, able to survive network and server failures while supporting gracefully recovery. It is capable of concurrently exchanging real-time data (such as voice), semi-real-time data like chat, and non-real-time data like tool call inputs and outputs in the sessions.

This protocol is a expected to be a foundational building block on top of which additional protocols can be built. It is anticipated that the AI Agent session protocol will utilize modern IETF application transfer protocols, such as webtransport or MOQ, based on the anticipated use cases. The protocol must also be usable by other application layer protocols with the appropriate layering and extension points enabling its adoption by any application. Examples of protocols that can utilize this include the existing defacto agent communication protocols such as the MCP and A2A protocols being worked on by the Linux Foundation. 


2. A protocol that allows an AI Agent to obtain and exchange authorization tokens with fine-grained, behavior-driven scopes bound to the specific operations that the AI Agent is permitted to perform on behalf of the user. Unlike traditional OAuth scopes which enumerate static resource permissions, agent authorization must account for dynamic behavioral boundaries, including conditional and context-dependent privileges that may vary across interactions.

Any extensions to OAuth protocol mechanisms required to support agent authorization (e.g., new grant types, token structures, or authorization data types) are expected to be developed within the OAuth working group. This deliverable focuses on defining the agent-specific integration profile: how existing and emerging OAuth mechanisms are composed and applied in AI agent scenarios, including the confirmation and evidence requirements described above. This deliverable will also address selective disclosure mechanisms that enable agents to reveal capabilities contextually, with cryptographic verification of presented claims independent of transport security. This includes privacy-preserving presentations that prevent correlation across different interaction contexts.

3. A mechanism for enabling human users to confirm operations invoked by AI agents acting on their behalf. This confirmation operation is performed by the agent orchestration layer of the AI Agent and therefore protects against hallucination and unintended actions. It is capable of working across multiple use cases, including a single AI Agent, or when using multiple AI Agents connected by the Agent-to-Agent protocol. It can be used to confirm any kind of operation, which includes invoking a REST API, calling a tool via MCP, or transferring to another AI Agent. It must provide cryptographic attestation of what the user has confirmed, enabling non-repudiation and auditable evidence trails. It might be simply a feature of the protocol defined in 2.

4. Framework, use cases and requirements

Foundational work will be documented through a set of one or more informational Internet-Drafts. These will outline the functional blocks, their relationships, and mechanisms for structured, semi-structured, and multi-modal information exchange. These include:

    Common use cases focused on Agent-to-agent and Agent-to-tool communications in order to verify suitability of the protocols developed.

    Gap analysis and requirements based on the examination of existing de facto protocols implemented in open-source projects.

    Protocol binding requirements specifying how agent protocols map onto shared transport infrastructure, including namespace conventions enabling multiple protocols (A2A, MCP, etc.) to coexist, and backward compatibility considerations for existing deployments.

# Coordination

This working group is expected to closely coordinate with other related IETF working groups, such as oauth, webbotauth, wimse, webtrans, moq, quic, and tsvwg on common topics. The group is also expected to maintain close communication with open-source projects running under the Linux Foundation.


# Out of Scope

The following topics are explicitly out of scope for this working group:

- Discovery of AI agents
    
- Definition of AI models, agent reasoning algorithms, or tool-specific business logic.

- Standardization of agent behavior, decision-making, or planning semantics.

- AI agent behavioral security (e.g., preventing the AI model itself from hallucinating, though mitigating the impact of hallucinations via protocol-level user confirmation is in scope).

# TENTATIVE: (Depends on buy in from relevant open source communities)

x. Agent-to-Agent (A2A) Protocol (S)
An Agent-to-Agent protocol that allows one AI Agent to invoke the services of another AI Agent. This protocol will allow for the exchange of user messages, including voice, video, images, and chat. It will provide basic lifecycle management, enabling the establishment, update, and termination of the services of the downstream agent. It is anticipated that this protocol would build upon existing industry work, including the MCP and A2A protocols currently under the auspices of the Linux Foundation.