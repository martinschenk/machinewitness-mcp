<img src="assets/logo-400.png" width="72" alt="MachineWitness">

# MachineWitness MCP server: is this domain on the record?

MachineWitness is an evidentiary archive of the machine-readable web in the
European Union. Every day two independent witnesses record what public domains
serve to machines (robots.txt, ai.txt, TDM reservations, llms.txt, and the
headers and meta tags of the homepage) and seal that day into a published
Merkle root with an external timestamp.

This server lets Claude, ChatGPT, Cursor or any MCP client ask whether a domain
is observed, suggest one, and order a time-stamped record of public addresses,
in the same conversation in which the question comes up. Hosted by
[machinewitness.eu](https://machinewitness.eu); this repository holds the public
metadata, the server code is not open source.

```
https://machinewitness.eu/mcp
```

Streamable HTTP · no authentication · listed in the
[official MCP registry](https://registry.modelcontextprotocol.io/v0/servers?search=machinewitness)
as `eu.machinewitness/archive`.

## A witness, not a detective

The archive records; it does not evaluate, rank or accuse. The tools answer
whether a domain is observed and from when. They never return file contents,
and there is no way to list or search the observed set. A record states what an
address delivered at a given time; it is not an assessment and not legal advice.

## Tools

- `check_coverage`: is a domain observed, from which sealed day, which files,
  at what cadence. Metadata only. *read-only*
- `capture_status`: where a point-in-time record stands, by its reference.
  Returns no customer data. *read-only*
- `suggest_domain`: suggest a domain for observation, with a reason a person
  reads. Always answered with "received", never with a promise. *write*
- `order_capture`: up to twenty public addresses on one domain. Every address is
  checked for free first; the tool then returns a payment link and charges
  nothing itself. After payment, both witnesses fetch and picture each address,
  each capture gets its own qualified electronic time-stamp, and the record is
  delivered by e-mail. *write*
- `order_extract`: one to twenty observed domains. Returns a payment link for an
  evidence extract, everything the archive recorded on each domain as one
  verifiable document; a domain never observed is refused by name before
  payment. Charges nothing itself. *write*
- `order_observation`: one to 500 domains, yearly or monthly. Returns a payment
  link for daily observation; a domain already observed daily in the core is
  refused by name. Charges nothing itself. *write*

Six languages for payment page and e-mails: `en`, `de`, `es`, `fr`, `it`, `pl`.

## Setup

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

See [llms-install.md](llms-install.md) for a one-call check that it works.
Full reference, including the plain HTTP API: [machinewitness.eu/api](https://machinewitness.eu/api).
Fees: [machinewitness.eu/services](https://machinewitness.eu/services).

## Privacy

The tools ask only for what their purpose needs: a domain, a reply address for
a suggestion, addresses to record and a delivery address for an order. Never a
purpose or a matter. What is kept and for how long:
[machinewitness.eu/privacy](https://machinewitness.eu/privacy)

---

Operated by Martin Schenk S.L., Madrid · [machinewitness.eu](https://machinewitness.eu) ·
questions: contact@machinewitness.eu
