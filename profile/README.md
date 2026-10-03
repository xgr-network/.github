# XGR Network

**XGR Network builds infrastructure for deterministic execution, verifiable processes and AI-native interaction on an EVM-compatible Layer-1.**

The public XGR stack combines:

- **XGRChain** — EVM-compatible Layer-1 blockchain
- **XDaLa** — validation, orchestration and process execution
- **XGR Interchain** — cross-chain XGR messaging and asset infrastructure
- **XGR MCP Gateway** — AI-native access to chain, process and protocol data
- **XGR** — native asset of XGRChain

---

## XGRChain

XGRChain is the execution and settlement layer of the XGR ecosystem.

Current public mainnet baseline:

| Parameter | Value |
| --- | --- |
| Public node | `xgr-node v3.1.1` |
| Chain ID | `1643` |
| Native asset | XGR |
| Execution | EVM-compatible |
| Finality | IBFT |
| Validator model | Delegated PoS |
| Voting power | Stake- and uptime-weighted |
| Mainnet | Live |
| Testnet | Available |

XGRChain supports:

- Ethereum-compatible accounts and smart contracts,
- standard Ethereum transaction types,
- deterministic IBFT finality,
- validator self-staking,
- delegated staking,
- epoch-based validator lifecycle,
- stake-weighted consensus,
- XGR-specific gas and fee policy,
- native protocol precompiles,
- configurable historical-state retention through the Online State Trie Sweeper.

Node implementation:

https://github.com/xgr-network/xgr-node

Chain specifications and documentation:

https://github.com/xgr-network/XGR

---

## XDaLa

**XDaLa** extends blockchain transactions into deterministic, auditable processes.

It combines:

1. **Validation** — rules evaluate transaction intent, parameters and external conditions.
2. **Orchestration** — multi-step execution paths coordinate permits, limits, triggers and dependencies.
3. **Execution** — smart-contract actions execute after successful validation.

XDaLa is designed for workflows requiring:

- deterministic process logic,
- external data integration,
- verifiable execution,
- encrypted inputs and outputs,
- auditability,
- compliance-sensitive controls,
- controlled smart-contract execution.

XDaLa specifications and XRC standards are maintained in:

https://github.com/xgr-network/XGR

---

## XGR Interchain

XGR Network maintains Interchain infrastructure for connecting XGRChain with supported external networks.

The first implemented XGR asset route connects:

**XGRChain ↔ Base**

Both transfer directions have been validated end-to-end on mainnet.

The route uses:

- native XGR on XGRChain,
- synthetic XGR / wXGR on Base,
- lock/mint and burn/unlock semantics,
- cross-chain messaging,
- validator attestations,
- BLS verification,
- Merkle proofs,
- destination-side security modules,
- relayers.

Bidirectional mainnet validation does not by itself imply that every route direction is continuously enabled or that a public bridge interface is currently open.

Current deployment and operational state belongs to the Interchain repository and its deployment manifests.

Implementation:

https://github.com/xgr-network/xgr-hyperlane

---

## AI-native access with MCP

The **XGR MCP Gateway** exposes XGR infrastructure through the Model Context Protocol.

MCP-compatible agents can work with structured tools for:

- XGRChain state,
- transactions and receipts,
- XDaLa sessions,
- XRC standards,
- deployed workflow discovery,
- address-relation graphs,
- native-XGR value-flow provenance,
- historical Session Start payloads,
- XDaLa authoring and validation,
- deployment handoffs,
- optional XGR purchase workflows,
- optional native-XGR starter gas.

User transaction signing remains under the control of the user's wallet, signer or custody setup.

Public implementation:

https://github.com/xgr-network/xgr-mcp

Mainnet MCP endpoint:

https://mcp.xgr.network/mcp

Testnet MCP endpoint:

https://mcp.testnet.xgr.network/mcp

---

## Core public repositories

| Repository | Purpose |
| --- | --- |
| [XGR](https://github.com/xgr-network/XGR) | Public specifications, XRC standards, genesis and technical documentation |
| [xgr-node](https://github.com/xgr-network/xgr-node) | Public XGRChain node implementation |
| [xgr-hyperlane](https://github.com/xgr-network/xgr-hyperlane) | XGR Interchain infrastructure and deployment tooling |
| [xgr-mcp](https://github.com/xgr-network/xgr-mcp) | Public MCP implementation for AI-native XGR access |

Other repositories in the organization contain application, tooling, infrastructure and ecosystem components built around the same stack.

---

## Architecture

At a high level:

    XDaLa
      │
      │ deterministic process execution
      ▼
    XGRChain
      │
      ├── EVM execution
      ├── IBFT finality
      ├── delegated PoS
      └── native XGR
      │
      ├──────────── XGR Interchain ──────────── external networks
      │
      └──────────── XGR MCP Gateway ────────── AI / agents / tools

These layers are related but independently versioned.

A change to one component does not automatically imply a protocol change in another.

---

## Start here

### Build on XGR

- **Website:** https://xgr.network
- **Documentation:** https://xgr.network/docs
- **Specifications:** https://github.com/xgr-network/XGR
- **XGRChain node:** https://github.com/xgr-network/xgr-node

### Network

- **Explorer:** https://explorer.xgr.network
- **Mainnet RPC:** https://rpc.xgr.network
- **Testnet Faucet:** https://faucet.xgr.network
- **XDaLa Workbench:** https://xdala.xgr.network

### Interchain and AI

- **Interchain:** https://github.com/xgr-network/xgr-hyperlane
- **MCP implementation:** https://github.com/xgr-network/xgr-mcp
- **MCP Mainnet:** https://mcp.xgr.network/mcp
- **MCP Testnet:** https://mcp.testnet.xgr.network/mcp

---

## Public node release

Current XGRChain public release:

**`xgr-node v3.1.1`**

Release commit:

**`1a4844b311fb856cb8c2303a40fa8aa69b560544`**

Release artifacts:

https://github.com/xgr-network/xgr-node/releases/tag/v3.1.1

The XGRChain protocol documentation is maintained against this release unless an individual document explicitly states otherwise.

---

## Security model

The XGR stack contains several distinct security domains.

They must not be treated as interchangeable:

- XGRChain consensus validators,
- staking and delegation state,
- node and RPC infrastructure,
- XDaLa permissions,
- MCP service authority,
- Interchain validators,
- Interchain relayers,
- contract ownership and administrative roles.

For example:

- an RPC user is not a consensus validator,
- an Interchain relayer is not a consensus validator,
- an Interchain validator is not automatically an XGRChain validator,
- MCP access does not transfer control of a user's transaction signer.

---

## Security reporting

Please report potential security issues responsibly.

**Contact:** security@xgr.network

Do not publish:

- private keys,
- seed phrases,
- validator keys,
- relayer signing keys,
- keystore passwords,
- production credentials,
- private RPC credentials,
- internal infrastructure secrets.

---

## About XGR Network

XGR Network develops an integrated blockchain stack centered on deterministic execution rather than isolated token transfers.

The architecture combines an EVM-compatible Layer-1, process execution, Interchain infrastructure and AI-native protocol access while keeping consensus, application and external-service authority explicitly separated.
