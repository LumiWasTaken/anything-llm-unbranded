<a name="readme-top"></a>

<p align="center">
    <b>AnythingLLM: A private ChatGPT to chat with <i>anything!</i></b>. <br />
    An efficient, customizable, and open-source enterprise-ready document chatbot solution.
</p>

<p align="center">
    <b>Unbranded Version from Lumi</b> <br />
    Features include: <br />
    - Telemetry Disabled by Default <br />
    - Survey Removed (more removed telemetry) <br />
    - Github Links Removed <br />
    - Misleading "Support" Button Removed (it just opens an email... wow)

    The rest of this Readme has been left unchanged.
</p>



A full-stack application that enables you to turn any document, resource, or piece of content into context that any LLM can use as references during chatting. This application allows you to pick and choose which LLM or Vector Database you want to use as well as supporting multi-user management and permissions.

![Chatting](https://github.com/Mintplex-Labs/anything-llm/assets/16845892/cfc5f47c-bd91-4067-986c-f3f49621a859)

<details>
<summary><kbd>Watch the demo!</kbd></summary>

[![Watch the video](/images/youtube.png)](https://youtu.be/f95rGD9trL0)

</details>

### Product Overview

AnythingLLM is a full-stack application where you can use commercial off-the-shelf LLMs or popular open source LLMs and vectorDB solutions to build a private ChatGPT with no compromises that you can run locally as well as host remotely and be able to chat intelligently with any documents you provide it.

AnythingLLM divides your documents into objects called `workspaces`. A Workspace functions a lot like a thread, but with the addition of containerization of your documents. Workspaces can share documents, but they do not talk to each other so you can keep your context for each workspace clean.

Some cool features of AnythingLLM

- **Multi-user instance support and permissioning**
- Multiple document type support (PDF, TXT, DOCX, etc)
- Manage documents in your vector database from a simple UI
- Two chat modes `conversation` and `query`. Conversation retains previous questions and amendments. Query is simple QA against your documents
- In-chat citations linked to the original document source and text
- Simple technology stack for fast iteration
- 100% Cloud deployment ready.
- "Bring your own LLM" model.
- Extremely efficient cost-saving measures for managing very large documents. You'll never pay to embed a massive document or transcript more than once. 90% more cost effective than other document chatbot solutions.
- Full Developer API for custom integrations!

### Supported LLMs, Embedders, and Vector Databases

**Supported LLMs:**

- [Any open-source llama.cpp compatible model](/server/storage/models/README.md#text-generation-llm-selection)
- [OpenAI](https://openai.com)
- [Azure OpenAI](https://azure.microsoft.com/en-us/products/ai-services/openai-service)
- [Anthropic ClaudeV2](https://www.anthropic.com/)
- [Google Gemini Pro](https://ai.google.dev/)
- [Ollama (chat models)](https://ollama.ai/)
- [LM Studio (all models)](https://lmstudio.ai)
- [LocalAi (all models)](https://localai.io/)
- [Together AI (chat models)](https://www.together.ai/)
- [Mistral](https://mistral.ai/)

**Supported Embedding models:**

- [AnythingLLM Native Embedder](/server/storage/models/README.md) (default)
- [OpenAI](https://openai.com)
- [Azure OpenAI](https://azure.microsoft.com/en-us/products/ai-services/openai-service)
- [LM Studio (all)](https://lmstudio.ai)
- [LocalAi (all)](https://localai.io/)

**Supported Vector Databases:**

- [LanceDB](https://github.com/lancedb/lancedb) (default)
- [Astra DB](https://www.datastax.com/products/datastax-astra)
- [Pinecone](https://pinecone.io)
- [Chroma](https://trychroma.com)
- [Weaviate](https://weaviate.io)
- [QDrant](https://qdrant.tech)
- [Milvus](https://milvus.io)
- [Zilliz](https://zilliz.com)

### Technical Overview

This monorepo consists of three main sections:

- `frontend`: A viteJS + React frontend that you can run to easily create and manage all your content the LLM can use.
- `server`: A NodeJS express server to handle all the interactions and do all the vectorDB management and LLM interactions.
- `docker`: Docker instructions and build process + information for building from source.
- `collector`: NodeJS express server that process and parses documents from the UI.

## 🛳 Self Hosting

Mintplex Labs & the community maintain a number of deployment methods, scripts, and templates that you can use to run AnythingLLM locally. Refer to the table below to read how to deploy on your preferred environment or to automatically deploy.
| Docker | AWS | GCP | Digital Ocean | Render.com |
|----------------------------------------|----:|-----|---------------|------------|
| [![Deploy on Docker][docker-btn]][docker-deploy] | [![Deploy on AWS][aws-btn]][aws-deploy] | [![Deploy on GCP][gcp-btn]][gcp-deploy] | [![Deploy on DigitalOcean][do-btn]][aws-deploy] | [![Deploy on Render.com][render-btn]][render-deploy] |

[or set up a production AnythingLLM instance without Docker →](./BARE_METAL.md)

## How to setup for development

- `yarn setup` To fill in the required `.env` files you'll need in each of the application sections (from root of repo).
  - Go fill those out before proceeding. Ensure `server/.env.development` is filled or else things won't work right.
- `yarn dev:server` To boot the server locally (from root of repo).
- `yarn dev:frontend` To boot the frontend locally (from root of repo).
- `yarn dev:collector` To then run the document collector (from root of repo).

[Learn about documents](./server/storage/documents/DOCUMENTS.md)

[Learn about vector caching](./server/storage/vector-cache/VECTOR_CACHE.md)

## Contributing

- create issue
- create PR with branch name format of `<issue number>-<short name>`
- yee haw let's merge

<details>
<summary><kbd>Telemetry for AnythingLLM</kbd></summary>

## Telemetry

AnythingLLM by Mintplex Labs Inc contains a telemetry feature that collects anonymous usage information.

### Why?

We use this information to help us understand how AnythingLLM is used, to help us prioritize work on new features and bug fixes, and to help us improve AnythingLLM's performance and stability.

### Opting out

Set `DISABLE_TELEMETRY` in your server or docker .env settings to "true" to opt out of telemetry.

```
DISABLE_TELEMETRY="true"
```

### What do you explicitly track?

We will only track usage details that help us make product and roadmap decisions, specifically:

- Version of your installation
- When a document is added or removed. No information _about_ the document. Just that the event occurred. This gives us an idea of use.
- Type of vector database in use. Let's us know which vector database provider is the most used to prioritize changes when updates arrive for that provider.
- Type of LLM in use. Let's us know the most popular choice and prioritize changes when updates arrive for that provider.
- Chat is sent. This is the most regular "event" and gives us an idea of the daily-activity of this project across all installations. Again, only the event is sent - we have no information on the nature or content of the chat itself.

You can verify these claims by finding all locations `Telemetry.sendTelemetry` is called. Additionally these events are written to the output log so you can also see the specific data which was sent - if enabled. No IP or other identifying information is collected. The Telemetry provider is [PostHog](https://posthog.com/) - an open-source telemetry collection service.

</details>

## 🔗 More Products

- **[VectorAdmin][vector-admin]:** An all-in-one GUI & tool-suite for managing vector databases.
- **[OpenAI Assistant Swarm][assistant-swarm]:** Turn your entire library of OpenAI assistants into one single army commanded from a single agent.

<div align="right">

[![][back-to-top]](#readme-top)

</div>

---

Copyright © 2023 [Mintplex Labs][profile-link]. <br />
This project is [MIT](./LICENSE) licensed.

<!-- LINK GROUP -->

[back-to-top]: https://img.shields.io/badge/-BACK_TO_TOP-222628?style=flat-square
[profile-link]: https://github.com/mintplex-labs
[vector-admin]: https://github.com/mintplex-labs/vector-admin
[assistant-swarm]: https://github.com/Mintplex-Labs/openai-assistant-swarm
[docker-btn]: ./images/deployBtns/docker.png
[docker-deploy]: ./docker/HOW_TO_USE_DOCKER.md
[aws-btn]: ./images/deployBtns/aws.png
[aws-deploy]: ./cloud-deployments/aws/cloudformation/DEPLOY.md
[gcp-btn]: https://deploy.cloud.run/button.svg
[gcp-deploy]: ./cloud-deployments/gcp/deployment/DEPLOY.md
[do-btn]: https://www.deploytodo.com/do-btn-blue.svg
[do-deploy]: ./cloud-deployments/digitalocean/terraform/DEPLOY.md
[render-btn]: https://render.com/images/deploy-to-render-button.svg
[render-deploy]: https://render.com/deploy?repo=https://github.com/Mintplex-Labs/anything-llm&branch=render
