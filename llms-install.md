# Installing the MachineWitness MCP server

The server is remote (Streamable HTTP) and needs no authentication. Nothing to
clone, build or run.

```json
{
  "mcpServers": {
    "machinewitness": {
      "type": "streamableHttp",
      "url": "https://machinewitness.eu/mcp"
    }
  }
}
```

No API key, no account, no sign-up.

**Check that it works:** call `check_coverage` with `{"domain": "spiegel.de"}`.
The answer says the domain is observed, from which sealed day onward, which
machine-readable files are requested and at what cadence. A domain that is not
observed returns "Not observed", which is a statement about this archive, not
about the domain.

**Ordering a point-in-time record:** `order_capture` with
`{"addresses": ["https://example.eu/terms"], "language": "en"}` checks the
addresses for free and returns a payment link. The call itself charges nothing;
nothing is captured until a person pays on that page. Follow the order with
`capture_status` and the returned reference (`MW-K-…`).
