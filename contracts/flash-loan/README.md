# Flash Loan Liquidity Pool

The `flash-loan` contract is a Soroban liquidity pool for trustless, multi-asset flash loans. Depositors provide token liquidity, and borrowers can receive an asset and use it during one transaction without collateral; the loan must be repaid with the applicable fee before the call completes or the transaction fails. The pool tracks balances, loan activity, borrowing volume, and collected fees, while restricting administration and protecting against reentrancy.

## Public Functions

- `initialize(env, admin, base_fee_bps)` — Initializes the pool once, records the administrator, and sets the starting fee in basis points.
- `deposit(env, depositor, token, amount)` — Transfers tokens from a depositor into the pool and increases the tracked liquidity for that asset.
- `withdraw(env, caller, token, amount, recipient)` — Allows the administrator to withdraw available token liquidity to a recipient.
- `flash_loan(env, token, amount, receiver, user_data)` — Sends a token amount to a receiver, invokes its callback, and requires repayment of the principal plus the calculated fee in the same transaction.
- `set_base_fee(env, caller, new_fee_bps)` — Updates the administrator-controlled base fee in basis points.
- `get_pool_balance(env, token)` — Returns the pool’s tracked balance for a token.
- `get_base_fee_bps(env)` — Returns the current base fee in basis points.
- `quote_fee(env, token, amount)` — Calculates the fee that would currently apply to a loan without executing it.
- `get_total_borrowed(env, token)` — Returns the total volume borrowed for a token across completed flash loans.
- `get_total_fees_collected(env, token)` — Returns the total fees collected for a token.
- `is_loan_active(env, token)` — Reports whether a flash loan is currently active for a token.

## Build and Test

Run these commands from the `contracts/flash-loan` directory:

```bash
# Build the contract for Soroban (WASM)
cargo build --target wasm32-unknown-unknown --release

# Run the contract tests
cargo test
```
