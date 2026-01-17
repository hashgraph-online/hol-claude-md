# Claude Code Guidelines for HOL Development

## Project Overview

This project uses [Hashgraph Online (HOL)](https://hol.org) - an open-source SDK ecosystem for building AI agents and decentralized applications on the Hedera network.

**Key Technologies:**
- TypeScript (strict mode)
- Node.js 20+ with pnpm
- @hashgraphonline/standards-sdk
- Jest with @swc/jest

## Build & Test Commands

```bash
pnpm install                 # Install dependencies
pnpm run dev                 # Development
pnpm run build               # Build
pnpm test                    # Run all tests
pnpm test -- --watch         # Watch mode
pnpm test -- --coverage      # With coverage
pnpm run lint                # ESLint
pnpm run typecheck           # TypeScript check
```

## Code Style Requirements

### TypeScript
- **NO `any` types** - Define proper interfaces
- **NO `as any` casting** - Use type guards
- **NO `@ts-ignore`** - Fix the type issue
- Always define explicit return types

### File Naming
- **kebab-case** for all files: `registry-client.ts`
- Tests in `__tests__/` directory

### Code Organization
- Maximum 500 lines per file
- No nested ternaries
- No inline comments - use JSDoc only
- No console.log - use Logger from standards-sdk

## HOL SDK Patterns

### RegistryBrokerClient Initialization
```typescript
import { RegistryBrokerClient } from '@hashgraphonline/standards-sdk';

const client = new RegistryBrokerClient({
  baseUrl: 'https://api.hol.org',
  apiKey: process.env.HOL_API_KEY,
});
```

### Search for Agents
```typescript
const results = await client.search({
  q: 'weather assistant',
  registry: 'hcs-10',
  limit: 10,
  page: 1,
});

results.hits.forEach(agent => {
  console.log(`${agent.name}: ${agent.description}`);
});
```

### Resolve Agent by UAID
```typescript
const agent = await client.resolveUaid('hcs10://0.0.123456/my-agent');
console.log('Name:', agent.name);
console.log('Protocols:', agent.protocols);
console.log('Capabilities:', agent.capabilities);
```

### Register an Agent
```typescript
const response = await client.registerAgent({
  name: 'My Agent',
  description: 'A helpful AI agent',
  protocols: ['hcs-10'],
  capabilities: ['chat'],
  endpoint: 'https://my-agent.example.com',
}, {
  autoTopUp: {
    accountId: process.env.HEDERA_OPERATOR_ID!,
    privateKey: process.env.HEDERA_OPERATOR_KEY!,
  },
});

if (response.success) {
  console.log('Registered:', response.uaid);
}
```

### Start a Chat Conversation
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

### Vector Search (Semantic)
```typescript
const results = await client.vectorSearch({
  query: 'find agents that can help with scheduling',
  limit: 5,
  filter: {
    protocols: ['a2a'],
  },
});

results.hits.forEach(hit => {
  console.log(`${hit.agent.name} (score: ${hit.score})`);
});
```

### Get Registry Stats
```typescript
const stats = await client.stats();
console.log('Total agents:', stats.totalAgents);

const registries = await client.registries();
registries.forEach(r => console.log(r.name));
```

## Testing Requirements

### TDD Workflow
1. **RED**: Write failing tests first
2. **GREEN**: Implement minimum code to pass
3. **REFACTOR**: Improve while keeping tests green

### Test Structure
```typescript
describe('RegistryBrokerClient', () => {
  let client: RegistryBrokerClient;

  beforeEach(() => {
    client = new RegistryBrokerClient();
  });

  describe('search', () => {
    it('should return agents matching query', async () => {
      const result = await client.search({ q: 'test' });
      expect(result.hits).toBeDefined();
      expect(Array.isArray(result.hits)).toBe(true);
    });
  });
});
```

## Validation Before Completion

Always run before marking work complete:
1. `pnpm run lint` - Zero violations
2. `pnpm run typecheck` - Zero errors
3. `pnpm run build` - Must compile
4. `pnpm test` - All tests pass

## Environment Variables

```bash
# .env
HOL_API_URL=https://api.hol.org
HOL_API_KEY=your-api-key
HEDERA_NETWORK=testnet
HEDERA_OPERATOR_ID=0.0.123456
HEDERA_OPERATOR_KEY=302e...
```

## Resources

- [HOL Website](https://hol.org)
- [HOL Registry](https://hol.org/registry)
- [SDK Documentation](https://hol.org/docs/libraries/standards-sdk/overview/)
- [Registry Broker Client](https://hol.org/docs/libraries/standards-sdk/registry-broker-client/)
- [GitHub](https://github.com/hashgraph-online)
