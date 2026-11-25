# Gas Oracle

The `gas-oracle` contract maintains a recent history of fee observations and uses an exponentially moving average (EMA) to estimate a current gas fee. An administrator initializes the oracle with optional smoothing, history-window, and bump-factor settings, then submits positive fee observations; callers can query the EMA, recent observations, or a bumped suggested fee.

## Public Functions

- `initialize(env, admin, alpha, window_size, bump_factor)` — Initializes the oracle once, using supplied parameters or the contract defaults for smoothing, history length, and the suggestion bump factor.
- `update(env, fee)` — Records a positive fee observation, maintains the configured recent-rate window, and updates the EMA.
- `get_ema(env)` — Returns the current EMA fee estimate.
- `get_suggested_fee(env)` — Returns the EMA-based fee estimate after applying the configured bump factor.
- `get_recent_rates(env)` — Returns the stored recent fee observations in insertion order.

## Build and Test

Run these commands from the `contracts/gas-oracle` directory:

```bash
# Build the contract for Soroban (WASM)
cargo build --target wasm32-unknown-unknown --release

# Run the contract tests
cargo test
```
