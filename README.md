[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/cohumanspace-digimon-engine-badge.png)](https://mseep.ai/app/cohumanspace-digimon-engine)

# 👾 Digimon Engine

<div align="center">
  <img src="./assets/digimon-engine.png" alt="Digimon Engine Banner" width="100%" />
</div>

</p>
<p align="center">
<a href="https://x.com/damndotfun">🐦 Twitter</a>
<span>&nbsp;&nbsp;|&nbsp;&nbsp;</span>
<a href="https://t.me/+iW4XMrHPc-5mMzhh">📢 Telegram</a>
<span>&nbsp;&nbsp;|&nbsp;&nbsp;</span>
<a href="https://www.digimon.tech/">🌐 Website</a>
<span>&nbsp;&nbsp;|&nbsp;&nbsp;</span>
<a href="https://docs.digimon.tech/digimon">📙 Documentation</a>
</p>

- [Documentation](https://docs.digimon.tech/digimon): Learn how to use Digimon Engine to build your own games
- [Community](https://docs.digimon.tech/digimon/community/welcome-aboard-digimon-trainers): Join the community to get help and share your games
- [Sample Game: DAMN](https://damn.fun): Play the sample game built with Digimon Engine
  - [DAMN on X Live Stream](https://x.com/damndotfun/live): Watch the live stream of the game
  - [Solana AI Hackathon Demo](https://www.youtube.com/watch?v=NNQWY-ByZww): Watch the demo of the game and the engine

# 🌍 README Translations
[English](./README.md) | [简体中文](./README.zh-CN.md) | [繁體中文](./README.zh-TW.md) | [한국어](./README.ko-KR.md) | [日本語](./README.ja-JP.md) | [Deutsch](./README.de-DE.md) | [Français](./README.fr-FR.md) | [Português](./README.pt-BR.md) | [Italiano](./README.it-IT.md) | [Español](./README.es-ES.md) | [Русский](./README.ru-RU.md) | [Türkçe](./README.tr-TR.md) | [Polski](./README.pl-PL.md)

# Overview
## Digimon Engine: Multi-Agent, Multi-Player Framework for AI-Native Games and Agentic Metaverse
Digimon Engine is an open-source gaming platform similar to Unreal Engine for AI gaming. It supports social and financial AI Agents, enabling immersive AI-native gameplay. We are preparing to onboard new games featuring AI Agent NPCs. Our aim is to create an AI agent framework to build a Westworld-like environment.

## MCP Server Overview

Seamless integration with **external clients**, **LLMs**, and **AI agents**, combining architectures from **MCP protocol**, **DAMN.FUN SDK**, and **Digimon Engine**. This includes building webhooks and new REST API endpoints for external game/agent creation, ownership, and wallet connectivity.  

<div align="center">
  <img src="./assets/mcp-server.png" alt="MCP Server Banner" width="100%" />
</div>

- Key components of the MCP architecture:  
  - **Hosts, Clients, Servers**: Modular design for scalability.  
  - **Transport Models**: STDIO (Standard Input/Output) + SSE (Server-Sent Events) for real-time communication.  
  - **Language & Runtime**: TypeScript for MCP Server core logic.  
  - **Deployment**: Docker for containerized, environment-agnostic scaling.


## Architecture Overview

- Agents: Each monster/agent has a unique identity and motivations, roaming the world, talking, and forming relationships. In the future, agents would reference prior interactions—extracted from a vector database (Pinecone) of memory embeddings—so every conversation and decision is informed by past encounters (persistence memory).

- Game Engine: Orchestration system schedules agent activities, handles “Run Agent Batch” tasks, and manages collisions. Whenever two monsters’ paths are predicted to cross, the engine groups them and triggers a conversation sequence. After tasks wrap up, agents become available again for new scheduling, ensuring continuous world activity without manual intervention.

- Event Logs: An append-only record tracks everything—agents’ paths, conversation timestamps, and who spoke to whom. Before starting a new path, monsters consult their event logs to predict future collisions. If they haven’t chatted with an intersecting agent recently, they initiate dialogue. The Event Logs also stores all conversation transcripts and coordinates for accurate context recall and memory embedding.

- Memory & Vector Database: After conversations or reflective moments, agents summarize their experiences and store them as vector embeddings (mxbai-embed-large). These embeddings can be retrieved later and filtered for relevance, injecting past context directly into the prompt for the next conversation.

- One of the core challenges in game engine design is keeping latency low while scaling to more players and agents. That’s why DAMN introduces a compressed state (HistoryObject) to efficiently track and replay movement. Each engine tick (~60/sec) logs numeric fields (like position), then at the end of each step (1/sec) we store a compressed “history buffer.” The client fetches both current values and this replay-able buffer, rendering smooth animations without any jumps. Impact: for players and agents, this design delivers fluid gameplay—no stutters or choppy animations. Behind the scenes, it’s a streamlined approach that keeps performance high, stays reliable, and scales seamlessly for more AI-driven characters.

- Instead of relying on existing game engine (ex: Unity or Godot), DAMN uses a custom AI-native game engine built from scratch (written in Typescript). AI agents and human players are treated identically—no second-class NPCs. Every tick, the engine updates the entire world in memory, giving AI the same power to move, interact, and engage as humans. This leads to more organic, dynamic worlds where AI isn’t just following scripts but genuinely participating in the gameplay. 


- Design Overview: 
1. Scheduler periodically triggers a new simulation step.
2. The engine loads game data from the database into memory.
3. Both AI agents and players submit actions or decisions, all handled in one unified loop. 
4. After applying the game’s rules, the engine computes a “diff” of changes and saves it back to the database.

Further details can be found in the [Architecture Overview](https://docs.digimon.tech/digimon/digimon-engine/architecture-overview).


# 💰 Launch a AI native game with Digimon Engine:


## The 1st Game built with Digimon Engine: DAMN (https://damn.fun)
![DAMN](./assets/damn-logo.png)
- The AI-native game that is damn fun! 
- [DAMN on X Live Stream](https://x.com/damndotfun/live): Watch the live stream of the game

# Quick Start

### Prerequisites

- [npm 11.0.0](https://www.npmjs.com/get-npm)
- [node 23.3.0](https://nodejs.org/en/download/)

### Community & Contact

- [GitHub Issues](https://github.com/CohumanSpace/digimon-engine/issues). Best for: bugs you encounter using Digimon Engine, and feature proposals.
- [Telegram](https://t.me/+iW4XMrHPc-5mMzhh). Best for: sharing your applications and hanging out with the community.

## Contributors

<a href="https://github.com/CohumanSpace/digimon-engine/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=CohumanSpace/digimon-engine" alt="Contributors" />
</a>

