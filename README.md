# HOL CLAUDE.md Templates

| ![](https://github.com/hashgraph-online/standards-sdk/raw/main/Hashgraph-Online.png) | **CLAUDE.md templates for the Universal Agentic Registry.** Configure Claude Code to build AI agents that discover and connect with 59,000+ agents across NANDA, MCP, A2A, Virtuals, and more.<br><br>[📚 SDK Documentation](https://hol.org/docs/libraries/standards-sdk/)<br>[📖 API Documentation](https://hol.org/docs/registry-broker/) |
| :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

[![npm version](https://img.shields.io/npm/v/@hashgraphonline/standards-sdk?style=for-the-badge&logo=npm&logoColor=white&label=standards-sdk)](https://www.npmjs.com/package/@hashgraphonline/standards-sdk)
[![Run in Postman](https://img.shields.io/badge/Run_in-Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)](https://app.getpostman.com/run-collection/51598040-f1ef77fd-ae05-4edb-8663-efa52b0d1e99?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D51598040-f1ef77fd-ae05-4edb-8663-efa52b0d1e99%26entityType%3Dcollection%26workspaceId%3Dfb06c3a9-4aab-4418-8435-cf73197beb57)
[![OpenAPI Spec](https://img.shields.io/badge/OpenAPI-3.1.0-6BA539?style=for-the-badge&logo=openapiinitiative&logoColor=white)](https://hol.org/registry/api/v1/openapi.json)

[![Open in CodeSandbox](https://img.shields.io/badge/Open_in-CodeSandbox-blue?style=for-the-badge&logo=codesandbox&logoColor=white)](https://codesandbox.io/s/github/hashgraph-online/hol-claude-md)
[![Open in StackBlitz](https://img.shields.io/badge/Open_in-StackBlitz-1269D3?style=for-the-badge&logo=stackblitz&logoColor=white)](https://stackblitz.com/github/hashgraph-online/hol-claude-md)
[![Open in Gitpod](https://img.shields.io/badge/Open_in-Gitpod-FFAE33?style=for-the-badge&logo=gitpod&logoColor=white)](https://gitpod.io/#https://github.com/hashgraph-online/hol-claude-md)

## What is the Universal Registry?

The [Universal Agentic Registry](https://hol.org/docs/registry-broker/) is the connectivity layer for the autonomous web. One standards-compliant API to access agents from:

| Protocol | Description |
|----------|-------------|
| **Virtuals** | Tokenized AI agents |
| **A2A** | Google's Agent-to-Agent protocol |
| **MCP** | Anthropic's Model Context Protocol |
| **ERC-8004** | On-chain agent verification |
| **x402 Bazaar** | Agent payment rails |
| **OpenConvAI** | Conversational AI standard |
| **XMTP** | Decentralized messaging |
| **ANS** | Agent Name Service |

## What is this?

`CLAUDE.md` files provide Claude Code with project-specific context, coding standards, and guidelines. This repository contains templates with accurate HOL SDK examples.

## Quick Start

```bash
curl -O https://raw.githubusercontent.com/hashgraph-online/hol-claude-md/main/CLAUDE.md
```

## What's Included

### Accurate SDK Examples

The templates include real, working code for:

- `RegistryBrokerClient` initialization
- Agent search with filters
- UAID resolution
- Agent registration with auto top-up
- Chat conversations
- Vector (semantic) search
- Registry stats and queries

### Code Quality Standards

- TypeScript strict mode
- File naming conventions
- TDD workflow
- Validation checklist

## Example: Search for Agents

```typescript
import { RegistryBrokerClient } from '@hashgraphonline/standards-sdk';

const client = new RegistryBrokerClient();

const results = await client.search({
  q: 'weather',
  registry: 'hcs-10',
  limit: 10,
});
```

## Example: Chat with Agent

```typescript
const conversation = await client.chat.start({
  uaid: 'hcs10://0.0.123456/agent',
  auth: {
    accountId: process.env.HEDERA_OPERATOR_ID!,
    privateKey: process.env.HEDERA_OPERATOR_KEY!,
  },
});

const response = await conversation.sendMessage({
  content: 'Hello!',
});
```

## API & Documentation

| Resource | Link |
|----------|------|
| **Live Registry** | [hol.org/registry](https://hol.org/registry) |
| **API Documentation** | [hol.org/docs/registry-broker](https://hol.org/docs/registry-broker/) |
| **SDK Reference** | [hol.org/docs/libraries/standards-sdk](https://hol.org/docs/libraries/standards-sdk/) |
| **Postman Collection** | [Run in Postman](https://app.getpostman.com/run-collection/51598040-f1ef77fd-ae05-4edb-8663-efa52b0d1e99) |
| **OpenAPI Spec** | [openapi.json](https://hol.org/registry/api/v1/openapi.json) |
| **npm Package** | [@hashgraphonline/standards-sdk](https://www.npmjs.com/package/@hashgraphonline/standards-sdk) |

## Related Repositories

- [`standards-sdk`](https://github.com/hashgraph-online/standards-sdk) - The core SDK powering the registry client
- [`hol-claude-skills`](https://github.com/hashgraph-online/hol-claude-skills) - Claude Code slash commands for HOL
- [`hol-cursorrules`](https://github.com/hashgraph-online/hol-cursorrules) - Cursor AI rules for HOL development

## 🏆 Score HOL Points

Contribute to this repository and score [HOL Points](https://hol.org/points)! 

- 🔧 **Fix bugs** or improve documentation
- ✨ **Add new features** or examples
- 📝 **Submit pull requests** to score points

Points can be used across the HOL ecosystem. [Learn more →](https://hol.org/points)

## License

MIT License - see [LICENSE](LICENSE) for details.
