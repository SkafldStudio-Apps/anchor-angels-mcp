# Anchor Angels for Claude

Use your Anchor Angels account from Claude: ask about the deals open to you, read their decks, data rooms and investor deep dives, see upcoming events and RSVP, and express interest or record a commitment after you confirm.

This repository holds a Claude Code plugin and the connection details. It has no agents, skills or code of its own: everything runs on the Anchor Angels platform, which answers as you.

- MCP address: `https://www.anchorangels.com/api/mcp`
- About this connector: https://www.anchorangels.com/mcp
- Your settings, once signed in: https://www.anchorangels.com/settings/mcp

## How sign-in works

There is nothing to copy. You add the address in your client, and the first time it connects your browser opens the Anchor Angels sign-in. You approve the connection, and the client can then act as you.

- It sees only what your account sees in the app, for your role.
- An active membership is required.
- You can disconnect any time from Settings > Claude and MCP in the app.

## Install

### Claude Code

As a plugin:

```bash
claude plugin marketplace add SkafldStudio-Apps/anchor-angels-mcp
claude plugin install anchor-angels@anchor-angels-mcp
```

Or add the server directly:

```bash
claude mcp add --scope user --transport http anchor-angels https://www.anchorangels.com/api/mcp
```

Then run `/mcp` in Claude Code and choose anchor-angels to sign in.

### claude.ai and Claude Desktop

Settings > Connectors > Add custom connector. Name it Anchor Angels and paste `https://www.anchorangels.com/api/mcp`. Connect, and sign in when your browser opens.

### Cursor

In `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "anchor-angels": {
      "url": "https://www.anchorangels.com/api/mcp"
    }
  }
}
```

### Codex

In `~/.codex/config.toml`:

```toml
[mcp_servers.anchor-angels]
url = "https://www.anchorangels.com/api/mcp"
```

Then sign in with `codex mcp login anchor-angels`.

### Other MCP clients

Any client that supports remote MCP servers over HTTP with OAuth sign-in can use the same address.

## What investors can do

Reading:

- `whoami`: your role and the network's profile
- `query_deals`, `get_deal_details`, `compare_deals`, `pipeline_summary`: the deals open to you
- `search_documents`, `search_records`: search decks, documents, deals and events you can see
- `get_pitch_deck_link`: a deal's pitch deck
- `list_data_room_documents`, `get_document_link`: data room documents, when a deal's room is open to you (links expire after 10 minutes)
- `list_investor_deep_dives`, `get_investor_deep_dive`: approved investor deep dives
- `list_events`: upcoming events
- `my_investments`: your own interest and commitments
- `my_notifications`: your notifications

Actions:

- `rsvp_event`: going or not going to an event
- `express_interest`: tell the team you are interested in a deal. Claude shows you a preview first and records it only after you confirm.
- `record_commitment`: record a commitment to a deal for yourself. Claude shows you the deal, the amount and the minimum first, and records it only after you confirm. The team follows up with the terms.

Other roles see the tools their role has; the platform lists them on connect and on the settings page.

Nothing here is investment advice. See https://www.anchorangels.com/disclaimers.

## Questions

hello@anchorangels.com

## License

MIT
