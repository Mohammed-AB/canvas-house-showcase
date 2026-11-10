# Canvas House: engineering notes

Creative generation is only useful when the user can understand the cost, keep the result and return to it later. Canvas House brings that complete loop into one bilingual studio.

## System path

~~~mermaid
flowchart LR
  Brief --> Quote
  Quote --> Reservation
  Reservation --> ImageProvider
  ImageProvider --> OwnedArtifact
  OwnedArtifact --> Gallery
  Gallery --> Download
~~~

This diagram describes the demonstrated system boundary, not a production deployment topology.

## Decisions and tradeoffs

### Approve the cost first

A short-lived quote precedes generation. A durable reservation limits spending even when a request times out or the server restarts.

### Treat output as an owned artifact

Saved images have visitor ownership. Reopening and downloading use the stored output rather than paying to regenerate it.

### Keep the preview deliberately small

Three selected references and a bounded brief expose the creative workflow without distributing the private studio implementation or customer material.

## Review questions

- What evidence demonstrates **approve the cost first**, and what would fail without it?
- What evidence demonstrates **treat output as an owned artifact**, and what would fail without it?
- What evidence demonstrates **keep the preview deliberately small**, and what would fail without it?

## Verification boundary

13 nonpaid acceptance groups, including ownership, concurrency and restart persistence. A real 1024 × 1024 PNG was generated, saved, reopened after reload and downloaded with matching bytes. EN/AR desktop and narrow-viewport evidence recorded.

This is a limited local showcase, not the full commercial studio. No production checkout, customer account or video-generation claim is made here.
