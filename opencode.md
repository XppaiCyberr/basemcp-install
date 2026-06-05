# Install Base MCP on Opencode

A step-by-step guide to connect the [Base MCP server](https://mcp.base.org/) with opencode, enabling AI agents to interact with Base blockchain (send tokens, swap, query wallets, and more).

## Prerequisites

- [opencode](https://opencode.ai) installed
- A [Base Account](https://base.org/account) (smart wallet) — required for authentication and transactions

## Step 1: Create the project directory

```bash
mkdir my-base-mcp-project
cd my-base-mcp-project
```

## Step 2: Configure the MCP server

Create `opencode.json` in the project root:

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "base": {
      "type": "remote",
      "url": "https://mcp.base.org/"
    }
  }
}
```

## Step 3: Authenticate with your Base Account

Open the project in opencode:

```bash
opencode
```

The first time the AI agent tries to use a Base MCP tool (e.g., sending tokens or checking a wallet), it will prompt you to approve a connection in your **Base Account** (https://base.org/account).

1. Follow the approval URL provided by the agent
2. Sign in to your Base Account
3. Approve the session

> **Note:** Base MCP uses [x402](https://x402.org) — a pay-per-request protocol. Some requests (e.g., swaps, sends) may require a micro-payment in USDC on Base. The AI agent will prompt you for approval when needed.

## Step 4: Start using Base MCP

Once authenticated, the AI agent can use tools like:

- `base_get_wallets` — list your wallets
- `base_get_portfolio` — check portfolio balance
- `base_send` — send ETH / ERC-20 tokens
- `base_swap` — swap tokens
- `base_search_tokens` — find token addresses
- `base_get_transaction_history` — view transaction history
- `base_sign` — sign messages / typed data

## Troubleshooting

| Problem | Solution |
|---------|----------|
| `Connection refused` | Ensure `https://mcp.base.org/` is accessible from your network |
| `x402 payment required` | The agent will provide an approval URL — open it in your Base Account |
| `Tool not found` | Verify `opencode.json` has the correct config and restart opencode |
| `Session expired` | Re-approve the connection in your Base Account |

## Full example `opencode.json`

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "base": {
      "type": "remote",
      "url": "https://mcp.base.org/"
    }
  }
}
```

That's it — you're now connected to Base MCP.
