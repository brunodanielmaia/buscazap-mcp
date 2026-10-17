# BuscaZap — MCP Server

> Product discovery across **180+ Brazilian stores**, straight from chat context — with a ready-to-buy link.
> Descoberta de produtos em **mais de 180 lojas brasileiras**, a partir do contexto da conversa — com link pronto pra comprar.

[![MCP Registry](https://img.shields.io/badge/MCP%20Registry-active-2ea44f)](https://registry.modelcontextprotocol.io/v0/servers?search=br.com.buscazap)

This repository is the **public home** of the BuscaZap MCP server: its [`server.json`](./server.json), docs and integration reference. The BuscaZap service itself is a hosted, proprietary product — there is no source code here.

---

## What it does

BuscaZap exposes its product-search engine as a **remote MCP server**. An LLM agent that detects purchase intent in a conversation can call the tool, and BuscaZap derives the search term, queries the stores and **ranks the results against the conversation context** — returning real products with a ready-to-buy link.

- 🇧🇷 Curated coverage of **180+ Brazilian retailers**
- 🧠 **Context-ranked** results (not just keyword search)
- 🔗 Each product comes with a direct purchase link
- ⚡ Stateless **Streamable HTTP**, spec `2025-06-18`

## Connect

| | |
|---|---|
| **Endpoint** | `https://buscazap.com.br/mcp` |
| **Transport** | `streamable-http` |
| **Registry name** | `br.com.buscazap/busca-produtos` |

Any MCP-compatible client (Claude, Cursor, Windsurf, …) can add it as a remote server pointing at the endpoint above. No credentials are required for anonymous access.

## Tools

| Tool | What it does |
|---|---|
| `buscar_produtos_por_contexto` | Takes a summary of the conversation (what the user wants, for whom, color/size/price range, rejected brands), derives the term and ranks products against that context. Optional args: `limit`, `llm` (provider per call), `recomendar`. |
| `listar_lojas` | Returns store coverage by segment plus the public total ("+180 lojas"). No arguments. |

## Access tiers

- **Anonymous** — open access to search and store listing, with a daily per-IP quota (abuse protection).
- **Enterprise** — authenticated partners (OAuth `client_credentials` or API key); no attribution in payload, higher limits. Talk to us for a partnership.

## Links

- 🤝 **Partners / B2B:** https://buscazap.com.br/mcp/parceiros
- 📖 **Technical docs:** https://buscazap.com.br/mcp/docs
- 💬 **WhatsApp (commercial):** +55 11 95455-7182

---

© BuscaZap — buscazap.com.br. BuscaZap is a proprietary product; see [LICENSE](./LICENSE).
