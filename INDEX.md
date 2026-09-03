# LinkedIn Auto Publisher — Repository Index

**Current status:** TEMPLATE REQUIRING API + DELAY-LOGIC REPAIR — not a verified publisher.

## Start here
1. [`README.md`](README.md)
2. [`TEMPLATE_STATUS.md`](TEMPLATE_STATUS.md) — authoritative compatibility/repair status.
3. [`workflow/`](workflow/) — current historical/template JSON.
4. [`index.html`](index.html)
5. [`evidence/demo/README.md`](evidence/demo/README.md)
6. [`evidence/screenshots/README.md`](evidence/screenshots/README.md)

## Confirmed current defects

- the checked workflow uses LinkedIn's legacy `/v2/ugcPosts` pattern rather than the current Posts API direction;
- the node named `Wait 24h` is a Set node that writes text rather than performing a real delay.

Do not call the current JSON a verified scheduled LinkedIn publisher.

## Repair gate

Update against current LinkedIn API/auth requirements, implement a real delayed/scheduled engagement-fetch path, verify post creation in an authorized test environment, validate duplicate/retry behavior, then preserve the old export as historical when a repaired version is created.

## Version policy

The present export becomes historical once a repaired workflow exists. Do not overwrite it in place.