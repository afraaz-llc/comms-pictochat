# Vendored dependencies

## trystero-nostr.js

A self-contained ESM bundle of [Trystero](https://github.com/dmotz/trystero)'s
Nostr strategy (`@trystero-p2p/nostr@0.23.1`), produced with esbuild so the app
has **no runtime CDN dependency** and no third-party supply-chain surface — the
whole UI loads even if a CDN is down or blocked.

Exports: `joinRoom`. Upstream license: MIT (Trystero).

### Regenerate

```bash
tmp=$(mktemp -d) && cd "$tmp"
echo '{"type":"module"}' > package.json
npm i @trystero-p2p/nostr@0.23.1
echo "export { joinRoom } from '@trystero-p2p/nostr';" > entry.js
npx esbuild entry.js --bundle --format=esm --minify --outfile=trystero-nostr.js
# then copy trystero-nostr.js into this directory
```
