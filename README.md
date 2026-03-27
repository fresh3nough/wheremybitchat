# wheremybitchat

A minimal, real-time Nostr ephemeral chat monitor. Streams live messages from all bitchat/NYM geohash channels in a single view with cypherpunk neon aesthetics on a black background.

Built on the Nostr protocol (kind 20000 ephemeral events), compatible with [Bitchat](https://github.com/permissionlesstech/bitchat) and [NYM](https://github.com/Spl0itable/NYM) geohash channels.

## Setup

No build tools, frameworks, or npm install required. The app is a single self-contained HTML file.

### Option 1: Local HTTP server (recommended)

Clone and serve:

```bash
git clone https://github.com/fresh3nough/wheremybitchat.git
cd wheremybitchat
```

Then serve with any local server:

```bash
# Python
python -m http.server 8000

# Node.js
npx serve

# PHP
php -S localhost:8000
```

Open `http://localhost:8000` in your browser.

### Option 2: Open directly

Open `index.html` directly in any modern browser (Chrome, Firefox, Edge, Safari). Some browsers may restrict ES module imports from `file://`, in which case use Option 1.

## Usage

1. Enter a nickname on the welcome screen and click **ENTER** (or press Enter).
2. Messages from all geohash channels stream in real time across the full page.
3. Type a message in the chat bar at the bottom and press **ENTER** or click **SEND**.
4. Type `#channelname` to switch your send target (e.g. `#9q`, `#dr`, `#gc`, `#nym`).
5. Your channel selection persists until you switch again -- no need to prefix every message.

## How it works

- Generates an ephemeral secp256k1 keypair per session (no registration, no accounts).
- Connects to multiple Nostr relays via WebSocket.
- Subscribes to kind 20000 ephemeral events (geohash-based channels).
- Each channel gets a consistent neon color for visual scanning.
- Messages are signed with Schnorr signatures per the Nostr protocol (NIP-01).
- Compatible with Bitchat and Nymchat -- messages you send appear in those apps and vice versa.

## Relays

The app connects to these Nostr relays by default:

- `wss://nos.lol`
- `wss://relay.damus.io`
- `wss://relay.primal.net`
- `wss://bitchat.nostr1.com`
- `wss://relay.nostr.band`

Edit the `RELAYS` array in `index.html` to add or change relays.

## License

MIT
