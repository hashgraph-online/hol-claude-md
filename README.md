# HOL CLAUDE.md Templates

| ![](https://github.com/hashgraph-online/standards-sdk/raw/main/Hashgraph-Online.png) | A lightweight SDK providing reference implementations for Hashgraph Consensus Standards (HCS) created by Hashgraph Online.<br><br>This SDK is built and maintained by [Hashgraph Online](https://hashgraphonline.com), a consortium of leading Hedera Organizations within the Hedera ecosystem.<br><br>[📚 Standards SDK Documentation](https://hashgraphonline.com/docs/libraries/standards-sdk/)<br>[📖 HCS Standards Documentation](https://hashgraphonline.com/docs/standards) |
| :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |


[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> CLAUDE.md templates for [Hashgraph Online (HOL)](https://hol.org) development - helping Claude Code understand your Hedera AI agent projects.

## What is this?

`CLAUDE.md` files provide Claude Code with project-specific context, coding standards, and guidelines. This repository contains templates with accurate HOL SDK examples.

## What is HOL?

[Hashgraph Online (HOL)](https://hol.org) is an open-source SDK ecosystem for building AI agents on the Hedera network:

- **[Standards SDK](https://github.com/hashgraph-online/standards-sdk)** - TypeScript SDK with RegistryBrokerClient
- **[Registry Broker](https://hol.org/registry)** - Universal agent discovery and chat
- **[MCP Server](https://github.com/hashgraph-online/hashnet-mcp-js)** - AI assistant integration

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

## Resources

- [HOL Website](https://hol.org)
- [HOL Registry](https://hol.org/registry)
- [Standards SDK Docs](https://hol.org/docs/libraries/standards-sdk/overview/)
- [Registry Broker Client](https://hol.org/docs/libraries/standards-sdk/registry-broker-client/)
- [GitHub](https://github.com/hashgraph-online)

## License

MIT License - see [LICENSE](LICENSE) for details.
