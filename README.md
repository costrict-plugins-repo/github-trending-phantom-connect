# Phantom Connect — Cursor & Claude Code Plugin

Give your agent a wallet. Swap, sign, and manage addresses across Phantom's supported chains — and tap into Phantom's docs for context. This plugin also includes skills, rules, and agents to help scaffold wallet-connected apps with the Phantom Connect SDK across React, React Native, and vanilla JS/TS.

Works with both **Cursor** and **Claude Code**.

## Installation

### Cursor

1. Clone or copy this plugin into your Cursor plugins directory, or open the folder in Cursor.
2. Cursor will automatically detect the `.cursor-plugin/plugin.json` manifest.
3. The MCP servers (`phantom-connect-sdk` and `phantom-mcp`) will appear in your MCP settings.

### Claude Code

1. Install the plugin from a marketplace, or load it locally for development:

   ```bash
   # From a marketplace (if available)
   claude plugin install phantom-connect@marketplace-name

   # From a local directory
   claude --plugin-dir /path/to/phantom-connect-plugin/
   ```

2. Claude Code will detect the `.claude-plugin/plugin.json` manifest and load all skills, agents, and MCP servers.
3. Use the `/phantom-connect:phantom-connect` skill to get full SDK assistance:

   ```
   /phantom-connect:phantom-connect react        # React SDK help
   /phantom-connect:phantom-connect browser      # Browser SDK help
   /phantom-connect:phantom-connect react-native # React Native SDK help
   ```

## What's Included

### Skills

All 8 skills are shared between Cursor and Claude Code, auto-discovered from `skills/`.

| Skill | Description |
|-------|-------------|
| **phantom-connect** | Comprehensive skill covering all three SDKs, transactions, payments, token-gating, and NFT minting |
| **setup-react-app** | Scaffold a React app with `@phantom/react-sdk`, PhantomProvider, ConnectButton, and hooks |
| **setup-browser-app** | Scaffold a vanilla JS/TS app with `@phantom/browser-sdk` singleton pattern |
| **setup-react-native-app** | Scaffold a React Native (Expo) app with `@phantom/react-native-sdk` and required polyfills |
| **send-sol-transaction** | Build and send SOL transfers with proper signing and verification |
| **sign-message** | Implement message signing for Solana and EVM, including SIWS authentication |
| **add-social-login** | Configure Google/Apple social login with embedded wallet support |
| **phantom-wallet-mcp** | Execute wallet operations via the Phantom MCP — addresses, transfers, signing, swaps |

### Rules (Cursor only)

| Rule | What It Enforces |
|------|------------------|
| **phantom-sdk-best-practices** | Use `signAndSendTransaction`, proper provider setup, error handling, connection checks |
| **solana-transaction-safety** | Use `LAMPORTS_PER_SOL`, verify transactions, correct network selection, no key exposure |
| **embedded-wallet-constraints** | No `signTransaction`, spending limits, session duration, polyfill requirements |

> Claude Code's plugin system does not support always-on rules. These rules are embedded in the `phantom-connect` skill and applied when the skill is invoked.

### Agents

| Agent | Purpose |
|-------|---------|
| **Phantom Integration Specialist** | SDK integration — scaffolds projects, writes correct code, validates against constraints, and looks up Phantom docs in real-time |
| **Phantom Wallet Agent** | Wallet operations — get addresses, transfer tokens, sign transactions, execute swaps, and sign messages via the `phantom-mcp` server |

### MCP Servers


| Server | Transport | Description |
|--------|-----------|-------------|
| **phantom-connect-sdk** | SSE | Phantom Connect SDK documentation at `https://docs.phantom.com/mcp` for real-time API reference |
| **phantom-mcp** | stdio | Wallet operations via [`@phantom/mcp-server`](https://www.npmjs.com/package/@phantom/mcp-server) — sign transactions, transfer tokens, buy tokens, sign messages |

The `phantom-mcp` server requires a `PHANTOM_APP_ID` environment variable from [Phantom Portal](https://phantom.com/portal). Set it in your environment or MCP settings.

## Usage

Once installed, ask the agent to:

- "Set up a React app with Phantom Connect"
- "Add social login with Google and Apple"
- "Send 0.1 SOL to an address"
- "Implement Sign-in with Solana"
- "Set up a React Native app with Phantom wallet"
- "Get my wallet addresses"
- "Transfer 0.5 SOL to [address]"
- "Sign this message with my wallet"

The agent will follow the plugin's skills and rules to generate correct, safe integration code.

## Requirements

- [Cursor](https://cursor.sh) editor **or** [Claude Code](https://claude.com/claude-code) CLI
- A Phantom Portal account for `appId` registration: [phantom.com/portal](https://phantom.com/portal)

## License

MIT
