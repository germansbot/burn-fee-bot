Clanker Fee Buyback Bot (Base)
What it is

A Node.js/TypeScript bot that:

monitors pending fees on Clanker Fee Locker (Base),

claims fees (usually in WETH),

uses 0x Swap API to swap WETH → BUY_TOKEN,

(optional) sends purchased tokens to a burn address (0x...dead),

(optional) supports a transparent dev “tip” (OFF by default).

⚠️ Security: NEVER share your private key. Use at your own risk.

Requirements

Node.js 20+

A wallet funded with native Base ETH for gas

RPC key (Alchemy recommended) or public fallback

0x API key

Install
git clone <YOUR_REPO>
cd burn-fee-bot
npm i


Create .env:

cp .env.example .env


Edit .env and fill:

BASE_RPC_URLS

DEV_PRIVATE_KEY

ZEROEX_API_KEY

BUY_TOKEN

Safe mode (no transactions)

Set:

DRY_RUN="1"


Run:

npm run dev

Production mode (sends transactions)

Set:

DRY_RUN="0"
DEBUG="0"
MIN_NATIVE_ETH_FOR_GAS="0.001"  # or 0.005


Run:

npm run build
npm start

Useful commands

Dev:

npm run dev


Build + start:

npm run build
npm start


Check pending fees:

npm run check:pending

Configuration (.env)

Required

BASE_RPC_URLS (comma-separated for fallback)

DEV_PRIVATE_KEY

ZEROEX_API_KEY

BUY_TOKEN

Recommended (safety)

MIN_NATIVE_ETH_FOR_GAS

SLIPPAGE_BPS (recommended 50–300)

CHECK_INTERVAL_MIN_S / CHECK_INTERVAL_MAX_S

CLAIM_COOLDOWN_S / SWAP_COOLDOWN_S

Auto-burn (optional)

AUTO_BURN="1"
BURN_ADDRESS="0x000000000000000000000000000000000000dEaD"

Operational notes

Run one instance per wallet (prevents nonce issues).

Keep DRY_RUN=1 until everything is verified.

Ensure enough Base native ETH for gas.

Use RPC fallback to reduce downtime.
