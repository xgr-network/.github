# XGR Network

**Reach more blockchains. We handle the integration.**

Through **XITA**, token projects can expand to additional supported blockchain networks without developing or maintaining their own bridge. For **approved projects**, XGR.Network handles the **technical integration and smart-contract deployment free of charge**. After the first successful transfer, eligible tokens can also become discoverable through XITA. Normal network transaction and validator fees remain separate.

XGRChain connects the blockchain ecosystems; XDaLa adds verifiable automated workflows; and the XGR MCP Gateway links AI agents with blockchain data and applications.

**Explore:** [XITA — connect your token](https://xita.xgr.network/) · [Free project integration](https://xita.xgr.network/join) · [XGRChain native coin](https://xgr.network/xgr.html) · [Technical documentation](https://xgr.network/docs/)

The XGR ecosystem includes:

- **XITA / XGR Interchain** — token connectivity across supported blockchains, without building a separate bridge
- **XGRChain** — independent EVM-compatible Layer-1 and connecting hub
- **XDaLa** — verifiable business-process and workflow automation
- **XGR MCP Gateway** — interfaces for AI-agent access to chain and workflow tooling
- **XGR** — the native coin of XGRChain, used for network fees and validator participation

---

## XITA — integrate once, expand your token's reach

XITA helps existing token projects access more blockchain ecosystems through XGRChain. Instead of commissioning a bridge for every additional network, projects can connect their tokens through XITA's shared Interchain infrastructure.

**XGR.Network covers technical integration and smart-contract deployment for approved projects, at no cost to those projects.** The application supports project discovery after the first successful transfer, subject to eligibility. Users retain control of their wallets and transactions; normal network gas and validator fees still apply.

Available blockchain networks and individual token routes evolve over time. **[Check XITA for current support](https://xita.xgr.network/)** rather than relying on a static list in a project description. The protocol security and implementation details remain documented below and in the public Interchain reference.

[Explore XITA](https://xita.xgr.network/) · [Request free technical integration](https://xita.xgr.network/join)

---

## XGRChain

XGRChain is the execution and settlement layer of the XGR ecosystem.

Current public mainnet baseline:

| Parameter | Value |
| --- | --- |
| Public node | `xgr-node v3.4.0` |
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

This section documents the deployed technical architecture and operational details. For token projects, the practical entry point is **[XITA](https://xita.xgr.network/)**, including **[free technical integration for approved projects](https://xita.xgr.network/join)**. The named networks below are an implementation snapshot; current support and active routes must be checked on XITA.

[Full technical documentation: protocol, contracts, CLI, RPC, independent transfers, runtime and services](https://github.com/xgr-network/XGR/blob/main/docs/interchain/README.md).

XGR Interchain supports multiple assets and directed route instances across **XGRChain (1643), Base (8453) and Arbitrum (42161)**. The repository records XGR representations on the hub and both spokes, and ARB collateral on Arbitrum with synthetic representations on XGRChain and Base. A manifest entry is not itself proof of current on-chain transfer readiness.

Every directed route has XGRChain at exactly one endpoint. XGRChain↔Base and XGRChain↔Arbitrum are distinct one-hop connections; Base↔Arbitrum journeys use two separately authenticated hops through XGRChain. This is not a single-route or XGR-only bridge.

The public Factory permits independent router deployments and route registration. A router has one immutable Gateway/route binding **per destination domain**; the hub router can bind multiple spoke domains. Parallel route instances for the same canonical asset are possible using separate router pairs. XITA's listing does not grant exclusive protocol admission.

Each message is authenticated with **Direct-BLS**, binding its original source evidence, route, fee and current destination set. `XITADirectTransport` uses a Mailbox and a zero-fee `ProtocolFee` dispatch hook. The retained `dispatchHook` field is **not a MerkleTreeHook**; it stores no message leaves and supplies no Merkle proof. Native chain state/receipt tries are unrelated.

The managed relayer is optional. Any executor can submit valid destination `Mailbox.process` calldata and pay destination gas. The public recovery helper prepares that calldata without signing keys or company permission. Source fees, principal/allowance, chain access and eligible validator quorum remain required.

- [Detailed multi-asset architecture](https://github.com/xgr-network/XGR/blob/main/docs/interchain/XGR_INTERCHAIN_Overview.md)
- [Exact security model and signed payload](https://github.com/xgr-network/XGR/blob/main/docs/interchain/XGR_INTERCHAIN_Security_Model.md)
- [Transfer without managed relayer: complete procedure](https://github.com/xgr-network/XGR/blob/main/docs/interchain/XGR_INTERCHAIN_v3.4.0_Operations.md)
- [Validator CLI and JSON-RPC](https://github.com/xgr-network/xgr-node/blob/XGR3.0/docs/ILN_V340_OPERATOR_REFERENCE.md)
- [Deployment and route inventory](https://github.com/xgr-network/XGR/blob/main/docs/interchain/XGR_INTERCHAIN_Deployment_Reference.md)


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
| [xgr-interchain](https://github.com/xgr-network/xgr-interchain) | XGR Interchain infrastructure and deployment tooling |
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

- **XITA for token projects:** https://xita.xgr.network/
- **Free project integration application:** https://xita.xgr.network/join
- **Interchain:** https://github.com/xgr-network/xgr-interchain
- **MCP implementation:** https://github.com/xgr-network/xgr-mcp
- **MCP Mainnet:** https://mcp.xgr.network/mcp
- **MCP Testnet:** https://mcp.testnet.xgr.network/mcp

---

## Public node release

Current XGRChain public release:

**`xgr-node v3.4.0`**

Release commit:

**`cbe6f8a4ae1718429a9924dcf87f0d28591d74e1`**

Release artifacts:

https://github.com/xgr-network/xgr-node/releases/tag/v3.4.0

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
- an eligible current Interchain signer must also match the active canonical XGR validator identity and BLS key,
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


## Current v3.4.0 documentation and independent operation

XGRChain node v3.4.0 is deployed on Testnet and Mainnet according to the network operator (27 October 2026). Binary rollout and consensus activation are distinct: the published Mainnet configuration activates `params.forks.securityAccounting.block` at **12,186,213**, inclusively. An omitted fork entry leaves the new rules inactive.

The current Interchain implementation is [xgr-interchain](https://github.com/xgr-network/xgr-interchain). Route registration through the public Factory is permissionless; XITA listing is not protocol admission. Message validity depends on the current destination validator BLS quorum and verified source evidence, not on the identity of a relayer. Users or independent executors can prepare and submit the same authenticated `Mailbox.process` call without the XITA website, commercial execution gateway, sponsor or managed relayer. Gas, protocol fees, working RPC access and validator quorum availability remain required.

- [Complete Direct-BLS technical reference](https://github.com/xgr-network/XGR/blob/main/docs/interchain/XGR_INTERCHAIN_v3.4.0_Reference.md)
- [Independent transfer and recovery runbook](https://github.com/xgr-network/XGR/blob/main/docs/interchain/XGR_INTERCHAIN_v3.4.0_Operations.md)
- [Node release, checksums and activation](https://github.com/xgr-network/XGR/blob/main/docs/chain/XGRCHAIN_v3.4.0_Release_and_Activation.md)
