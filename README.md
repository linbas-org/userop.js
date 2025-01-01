# userop.js

Userop.js is an SDK for building ERC-4337 User Operations. This library provides a convenient way to create, sign, and manage UserOperations for account abstraction on Ethereum.

## Installation

```bash
# npm
npm install userop

# pnpm
pnpm add userop

# yarn
yarn add userop
```

## Why userop.js?

### No vendor lock-in 🔓
We began building userop.js in 2022 because building User Operations from scratch was too difficult with viem or ethers.js alone. As more ERC-4337 companies emerged in 2023 and began to develop their own SDKs, it was evident that this was a problem for all applications building with Smart Accounts.

We strongly believe in creating an open ecosystem and helping everyone thrive. That's why userop.js:
- Lets you mix-and-match services from any provider
- Is MIT-licensed and open source
- Works out-of-the-box with both viem PublicClients and ethers v6 JsonRpcProviders

### Designed for App Development 📲
We put a lot of care into creating the right levels of abstraction to reduce the time you spend writing boilerplate code.

Key features:
- Strong typing with Smart Account ABI enforcement
- Sensible defaults with automatic JSON-RPC method orchestration
- Flexible configuration for different use cases
- Simple API for creating and managing UserOperations
- Built-in support for popular account abstraction wallets
- Gas estimation and fee management utilities
- Middleware system for customizing UserOperation handling

### Stability ⚖️
Many organizations rely heavily on the userop.js library. We ensure stability through:
- High coverage end-to-end testing using the ERC-4337 developer testnet
- Robust QA testing with ERC-4337 examples repository
- Active maintenance and support

## Quick Example

```javascript
import { Client } from "userop";

// Create a client instance
const client = await Client.init(rpcUrl);

// Build a UserOperation
const userOp = await client.buildUserOperation({
    target: receiverAddress,
    data: "0x",
    value: ethers.utils.parseEther("0.1")
});

// Send the UserOperation
const result = await client.sendUserOperation(userOp);
```

## Contributing

### Prerequisites

- Node >=18.0.0

### Setup

```bash
yarn install
yarn test
```

### Development Guidelines
- Write tests for new features
- Follow the existing code style
- Update documentation when making changes
- Create detailed PR descriptions

## FAQs

### Why not just use viem or ethers.js?
Viem and ethers are excellent tools for interacting with an Ethereum network. However, ERC-4337 adds an additional layer of infrastructure from Bundlers to Smart Accounts and Paymasters. Userop.js removes the complexity of working with low level protocols and allows you to spend more time focusing on your application.

### Do I have to use specific infrastructure?
No. Userop.js is vendor agnostic and can work with any ERC-4337 compliant infrastructure, whether self-hosted or from a third party provider. It is also compatible with any Smart Account implementation.

### Found an issue?
Please open an issue on GitHub or reach out through our Discord community.

## License

Distributed under the MIT License. See [LICENSE](./LICENSE) for more information.
