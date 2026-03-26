Introduction and Group Overview

The AI Agent Protocols (aiproto) Working Group is about defining protocols enabling interoperability for AI Agent applications on the Internet. AI agents are a class of software applications that make use of a Large Language Model (LLM) to act autonomously to accomplish a task on behalf of a user. AI Agents often interact with users via chat or voice, performing tasks based on the flow of the conversation. For an AI Agent to perform its task, it needs to interact with resources on the Internet. It may invoke tools - which are typically APIs that allow the AI Agent to obtain information or perform actions. It may also interact with other AI Agents, delegating tasks to them. 

The usage of tools and the connection to other AI Agents introduces a need for interoperability, so that these tools and agents can be provided by vendors different from the one that has developed the AI Agent itself. The role of the aiproto working group is to facilitate such interoperability.

Several considerations arise which are unique to AI Agent protocols, which are a focus of activity for protocol development:

* LLMs can hallucinate, including hallucination of tool use. This can result in risk to users when an AI Agent erroneously performs actions on their behalf. Consequently, techniques for hallucination mitigation - primarily through approvals from users - are critical

* Interactions between users and agents, and between agents, can be long lived, and make use of the exchange of significant amounts of context. This introduces new considerations around reliability and data transport. 

* Data exchanged between users, agents, and tools can contain private information, such as personally identifiable information (PII) and payment information. Ensuring this data is adequately protected is important

* Conversations between an end user and an AI Agent need to work using voice, and be very low latency. This includes extremely fast barge times (also known as interruption). These properties also need to work when that collaboration happens between agents as well


The working group will produce the following standards track deliverables:

(1) A standards track AI Agent session protocol for creation and maintenance of long-lived sessions between AI agents, or between AI agents and tools that have long-lived operation. These sessions allow for the bidirectional exchange of data, incuding model context, tool call results, and chat messages. The protocol will facilitate highly scalable and reliable session management, able to survive network and server failures while gracefully recovering. It is capable of exchanging real-time data (such as voice), semi-real-time data like chat, and non-real-time data like tool call inputs and outputs, all concurrently during the session. 

This protocol is a foundational layer ontop of which additional protocols can be built. It is anticipated that the AI Agent session protocol will make use of modern IETF application transfer protocols, such as webtransport or MOQ, based on the anticipated use cases. The protocol must also be usable by non-IETF protocols, like the Model Context Protocol (MCP) or Agent-to-Agent (A2A) protocol, with the appropriate layering enabling its usage by any application

(2) An Agent-to-Agent protocol that allows one AI Agent to invoke the services of another AI Agent. This protocol will allow for the exchange of user messages from the end user, including voice, video, images and chat. It will provide basic lifecycle management, enabling the establishment, update, and termination of the services of the downstream agent. This A2A protocol will make use of the AI Agent session protocol, and be the first application specified on top of it. It is anticipated that this protocol would be a next-gen version of the A2A protocol currently under the auspices of the Linux Foundation, building upon that foundation. 

(3) A protocol for enabling human users to confirm operations invoked by AI agents acting on their behalf. This confirmation operation is performed by the agent orchestration layer of the AI Agent and therefore protects against hallucination. It is capable of working in many different use cases, including a single AI Agent, or when using multiple AI Agents connected by the Agent-to-Agent protocol. It can be used to confirm any kind of operation, which includes invoking of a REST API, calling a tool via MCP, or even transferring to another AI Agent with the Agent-to-Agent protocol. It must provide cryptographic attestation of what the user has confirmed, enabling non-repudation. 

(4) A protocol that allows an AI Agent to obtain and exchange OAuth tokens with extremely limited scopes, bound to the specific operations that the AI Agent is permitted to perform on behalf of the user. {NOTE: this might be better done in the OAuth working group}

The aiproto working group is expected to work closely with the webbotauth group, and make use of its output for any cases where it is necessary to authenticate an AI Agent. 

