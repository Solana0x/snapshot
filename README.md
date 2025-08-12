# NFT Snapshots • Ronin

A web-based tool to take and export NFT holder snapshots for ERC-721 collections on the **Ronin** blockchain (chainId 2020).

Supports fetching via:
- **Explorer API** (fastest)
- **RPC Single calls**
- **RPC Multicall**

## Features
- Fetch holders with balances directly from Ronin's Explorer API.
- On-chain queries using RPC for `ownerOf` and `tokenByIndex`.
- Multicall support for batching.
- Pagination until all holders are fetched.
- Export results to Excel (`ronin_snapshot.xlsx`).
- Rate limiting, RPC rotation, and backoff handling.

## How to Use
1. Open `main.html` in your browser.
2. Choose the **Engine**:
   - **Explorer API (fast)** — Uses the Skynet Explorer endpoint:
     ```
     https://skynet-api.roninchain.com/ronin/explorer/v2/tokens/{contract}/top_holders
     ```
   - **RPC Single** — Queries each token sequentially.
   - **RPC Multicall** — Queries in batches using a multicall contract.
3. Enter:
   - **Collection (ERC721)**: Contract address (e.g., `0x...`)
   - **Block**: `latest` or a specific block number.
   - **RPCs**: Comma-separated RPC endpoints.
   - **From ID / To ID**: Optional token ID range (leave To ID blank to auto-detect).
4. (Optional) Configure advanced settings:
   - Calls/sec
   - Parallel workers
   - Multicall address
   - Multicall chunk size
   - Explorer page size
5. Click **Take snapshot**.
6. Wait for progress to reach 100%.
7. Click **Download Excel** to save the snapshot locally.
