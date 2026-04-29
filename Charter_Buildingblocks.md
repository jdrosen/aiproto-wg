Introduction and Group Overview

The AI Agent Protocols (aiproto) Working Group is about defining protocols enabling interoperability for AI Agent applications on the Internet. AI agents are a class of software applications that make use of a Large Language Model (LLM) to act autonomously to accomplish a task on behalf of a user. AI Agents often interact with users via chat or voice, performing tasks based on the flow of the conversation. For an AI Agent to perform its task, it needs to interact with resources on the Internet. It may invoke tools - which are typically APIs that allow the AI Agent to obtain information or perform actions. It may also interact with other AI Agents, delegating tasks to them. 

The usage of tools and the connection to other AI Agents introduces a need for interoperability, so that these tools and agents can be provided by vendors different from the one that has developed the AI Agent itself. The role of the aiproto working group is to facilitate such interoperability.

Several considerations arise which are unique to AI Agent protocols, which are a focus of activity for protocol development:

* AI Agents act as autonomous software entities that need to be authenticated independently of the users they represent. Establishing verifiable agent identity - distinct from, but associated with, user identity - is a prerequisite for meaningful authorization and accountability. The working group will coordinate with the webbotauth working group and leverage existing frameworks such as workload identity for this purpose.

* LLMs can hallucinate, including hallucination of tool use. This can result in risk to users when an AI Agent erroneously performs actions on their behalf. Consequently, techniques for hallucination mitigation - primarily through approvals from users - are critical

* Interactions between users and agents, and between agents, can be long lived, and make use of the exchange of significant amounts of context. This introduces new considerations around reliability and data transport. 

* Data exchanged between users, agents, and tools can contain private information, such as personally identifiable information (PII) and payment information. Ensuring this data is adequately protected is important

* Conversations between an end user and an AI Agent need to work using voice, and be very low latency. This includes extremely fast barge times (also known as interruption). These properties also need to work when that collaboration happens between agents as well


The working group will produce the following standards track deliverables:

(1) A standards track AI Agent session protocol for creation and maintenance of long-lived sessions between AI agents, or between AI agents and tools that have long-lived operation. These sessions allow for the bidirectional exchange of data, incuding model context, tool call results, and chat messages. The protocol will facilitate highly scalable and reliable session management, able to survive network and server failures while gracefully recovering. It is capable of exchanging real-time data (such as voice), semi-real-time data like chat, and non-real-time data like tool call inputs and outputs, all concurrently during the session. 

This protocol is a foundational layer ontop of which additional protocols can be built. It is anticipated that the AI Agent session protocol will make use of modern IETF application transfer protocols, such as webtransport or MOQ, based on the anticipated use cases. The protocol must also be usable by other application-layer protocols, whether defined within or outside the IETF, with the appropriate layering enabling its adoption by any application

(2) An Agent-to-Agent protocol that allows one AI Agent to invoke the services of another AI Agent. This protocol will allow for the exchange of user messages from the end user, including voice, video, images and chat. It will provide basic lifecycle management, enabling the establishment, update, and termination of the services of the downstream agent. This A2A protocol will make use of the AI Agent session protocol, and be the first application specified on top of it. It is anticipated that this protocol would build upon existing industry work on agent-to-agent communication, including the MCP and A2A protocol currently under the auspices of the Linux Foundation, while incorporating requirements identified through the IETF standardization process.

(3) A protocol that allows an AI Agent to obtain and exchange authorization tokens with fine-grained, behavior-driven scopes bound to the specific operations that the AI Agent is permitted to perform on behalf of the user. Unlike traditional OAuth scopes which enumerate static resource permissions, agent authorization must account for dynamic behavioral boundaries, including conditional and context-dependent privileges that may vary across interactions.

The protocol must include a mechanism for human users to confirm operations invoked by AI agents acting on their behalf, as an integral part of the authorization flow. This confirmation capability protects against hallucination by requiring explicit user approval before sensitive operations are executed, and applies across use cases including single-agent and multi-agent workflows. It must provide cryptographic attestation of what the user has confirmed, enabling non-repudiation, and support auditable evidence trails for post-hoc verification of what was confirmed, by whom, and under what context.

Any extensions to OAuth protocol mechanisms required to support agent authorization (e.g., new grant types, token structures, or authorization data types) are expected to be developed within the OAuth working group. This deliverable focuses on defining the agent-specific integration profile: how existing and emerging OAuth mechanisms are composed and applied in AI agent scenarios, including the confirmation and evidence requirements described above.

The aiproto working group is expected to work closely with the webbotauth group, and make use of its output for any cases where it is necessary to authenticate an AI Agent. 

