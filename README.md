# Reevol MCP servers

Two free, hosted MCP servers from [Reevol](https://reevol.com), the Revenue OS for global trade. Both use Streamable HTTP, need no key and no install, and work in Claude, ChatGPT, Cursor and any MCP client.

| Server | What it does | Endpoint |
|---|---|---|
| **Reevol Source** | Search, verify and compare 200,000+ global suppliers by brief, name, HS code or country | `https://source.reevol.com/mcp` |
| **Reevi** | Find companies that already buy a product, by product and country | `https://reevi.ai/mcp` |

This repo holds docs and the registry metadata only. The servers are hosted by Reevol.

## Reevol Source: supplier search

Supplier intelligence for AI procurement and sourcing agents. Search 200,000+ manufacturers and trading companies in 6 languages, open a supplier card, or compare suppliers side by side. Results are citation-friendly, so an agent can show where each fact came from.

- Endpoint: `https://source.reevol.com/mcp`
- Auth: none for the read tools (60 requests/min per IP). An optional partner key unlocks `get_red_flags`, `draft_rfq`, `find_and_brief` and `request_introduction`.
- Docs: https://source.reevol.com/for-agents/
- Official MCP Registry: `com.reevol.source/supplier-search`

| Tool | What it does |
|---|---|
| `search_suppliers` | Find suppliers by company name, brand or alias |
| `match_suppliers_by_brief` | Match suppliers to a plain-language buyer brief |
| `find_suppliers_by_hs_code` | List suppliers under an HS code, with country, certification and size filters |
| `find_suppliers_by_country` | List suppliers in a country, with the same filters |
| `get_supplier` | Full supplier profile |
| `get_similar_suppliers` | Up to 10 similar suppliers |
| `compare_suppliers` | Side-by-side comparison |
| `get_red_flags` | Due-diligence signals (partner key) |
| `draft_rfq` | Draft a request for quotation (returns text, sends nothing; partner key) |
| `find_and_brief` | One-shot research brief (partner key) |
| `request_introduction` | Ask Reevol to introduce the buyer to a supplier (partner key) |
| `request_supplier_listing`, `verify_supplier_listing`, `resend_supplier_listing_code` | A supplier requests or verifies its own listing |

Try: "Find suppliers for HS code 8504 in China." / "Find a BSCI-certified factory in Vietnam for women's woven outerwear, 11 to 50 staff." / "Compare the first two suppliers you found."

## Reevi: find buyers for exporters

Reevi is the AI assistant for exporters growing globally. Give a product and target countries and get named buyer companies with website, country, an A/B/C fit grade and the reason each fits, drawn from trade records and the public web, plus a link to the saved report on reevi.ai.

- Endpoint: `https://reevi.ai/mcp`
- Auth: none. 5 free searches a day per IP.
- Website: https://reevi.ai/find-buyers
- Official MCP Registry: `ai.reevi/find-buyers`

| Tool | What it does |
|---|---|
| `find_buyers` | Named buyer companies for a product and target markets (read-only, 30 to 75 seconds) |

Try: "Find buyers in Germany and the United States for organic turmeric powder."

## Connect

**Claude (claude.ai or desktop):** Settings > Connectors > Add custom connector, paste the endpoint.

**ChatGPT:** Settings > Connectors (developer mode) > Create, paste the endpoint, no authentication.

**Cursor, Claude Code, VS Code and other clients** (`mcp.json`):

```json
{
  "mcpServers": {
    "reevol-source": { "type": "http", "url": "https://source.reevol.com/mcp" },
    "reevi": { "type": "http", "url": "https://reevi.ai/mcp" }
  }
}
```

## Support

contact@reevol.com · [Privacy](https://reevol.com/privacy-policy) · [Terms](https://www.reevol.com/terms-and-conditions)
