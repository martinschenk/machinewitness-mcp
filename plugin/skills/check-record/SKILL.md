---
name: check-record
description: Use when someone needs to know what a website served at a given time, whether a domain's AI opt-out (robots.txt, ai.txt, TDM reservation, llms.txt) was recorded, or wants to secure the current state of public web pages as time-stamped evidence before it changes.
---

# Is it on the record?

MachineWitness is a witness, not a detective: it records what public EU domains
serve to machines and seals each day. It does not evaluate, rank or give legal advice.

1. **Past state of a domain:** call `check_coverage` with the domain. It says whether
   and from which sealed day the domain is observed, which files, at what cadence.
   It never returns file contents. If the user needs the content as a document, offer
   `order_extract` (returns a payment link, charges nothing itself).
2. **Secure a page now, before it changes:** call `order_capture` with up to twenty
   public addresses on one domain. Every address is checked for free first; the tool
   returns a payment link. Nothing is captured until a person pays on that page.
   Afterwards follow the order with `capture_status` and the reference `MW-K-…`.
3. **Ongoing:** `order_observation` for daily observation of a domain (subscription).

Never ask for a purpose or a matter. Say plainly that a record states what an address
delivered at that time; what follows from it is for the user and their counsel.
