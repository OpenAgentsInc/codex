# Wallet Management in Boardwalk Cash

## Wallet State

The wallet state in Boardwalk Cash includes:
- Balance: An object mapping currency units to amounts
- Balance Locked: A boolean indicating if the balance is locked
- Keysets: An object mapping keyset IDs to Wallet objects

## Key Components

1. **WalletSlice**: Redux slice for managing wallet state
   - Handles keyset initialization, balance updates, and keyset management
   - Manages loading states and error handling

2. **LocalStorage**: Used for storing:
   - Keysets
   - Proofs

3. **API Interactions**:
   - `updateUser`: Updates user information on the server, including default mint URL

4. **Custom Hooks**:
   - `useCashuContext`: Manages Cashu-related state and operations (proposed refactoring in Issue #67)
   - `useProofStorage`: Handles proof storage and retrieval (proposed refactoring in Issue #67)

## Wallet Actions

1. **Initialize Keysets**: `initializeKeysets`
   - Loads keysets and proofs from localStorage
   - Calculates the initial balance

2. **Set Main Keyset**: `setMainKeyset`
   - Sets a keyset as the main (active) keyset
   - Updates the user's default mint URL on the server

3. **Update Keyset Status**: `updateKeysetStatus`
   - Updates a keyset's active and reserve status

4. **Set Balance**: `setBalance`
   - Updates the wallet balance if it's not locked

5. **Lock/Unlock Balance**: `lockBalance` and `unlockBalance`
   - Controls whether the balance can be updated

6. **Add Keyset**: `addKeyset`
   - Adds a new keyset to the wallet

## Wallet Structure

A Wallet object includes:
- ID
- Keys (MintKeys)
- Proofs
- URL
- Active status
- Reserve status

## Key Features

1. **Multiple Keysets**: The wallet can manage multiple keysets, each associated with a different mint.

2. **Balance Locking**: The ability to lock the balance prevents unintended updates during certain operations.

3. **Main Keyset**: One keyset can be set as the main (active) keyset, which is used as the default for operations.

4. **Reserve Keysets**: Keysets can be marked as reserve, potentially for backup or secondary operations.

5. **Local Storage Sync**: Keyset changes are immediately synced to localStorage for persistence.

## Known Issues and Improvement Areas

1. **Token Availability After Refresh** (Issue #53):
   - Problem: Refreshing the browser while creating a token can cause the token to become unavailable, potentially leading to loss of funds.
   - Proposed Solution: Implement a more robust token creation and storage mechanism that persists across page refreshes.

2. **Decimal Place Restriction** (Issue #43):
   - Problem: Amount inputs currently allow any number of decimal places.
   - Proposed Solution: Implement input validation to restrict amount inputs to two decimal places for improved accuracy and consistency.

3. **Minting Tokens Exceeding Mint Reserves** (Issue #29):
   - Problem: The wallet can request minting of tokens that exceed the mint's reserves, leading to potential loss of funds.
   - Proposed Solution: Implement checks on the mint side to prevent quoting amounts exceeding available reserves.

4. **Context Refactoring** (Issue #67):
   - Proposal: Refactor the wallet to use `useCashuContext` and `useProofStorage` for improved state management and error prevention.
   - Benefits: This would make the state more manageable and less error-prone, potentially addressing issues like #53.

5. **Error Handling**: 
   - Current error handling is basic, with simple error messages
   - Opportunity to implement more detailed error handling and user feedback

6. **Asynchronous Operations**:
   - Keyset initialization and main keyset setting involve asynchronous operations
   - Ensure proper error handling and state management for all async operations

7. **Balance Calculation**:
   - Currently only supports USD
   - Could be expanded to support multiple currencies

8. **Proof Management**:
   - Proofs are loaded from localStorage but not actively managed in this slice
   - Consider integrating proof management more tightly with wallet management

## Suggested Improvements

1. Implement more robust error handling with specific error types and messages.
2. Consider adding support for multiple currencies in balance calculations.
3. Integrate proof management more closely with wallet management for better consistency.
4. Implement a mechanism to periodically sync wallet state with the server to prevent discrepancies.
5. Add functionality to remove or deactivate keysets.
6. Implement a more secure method for storing sensitive information like proofs and keys.
7. Develop a system for handling partially created tokens to prevent loss of funds during page refreshes.
8. Implement input validation for amount inputs to restrict to two decimal places.
9. Add checks or integrate with the mint to prevent requesting tokens that exceed available reserves.

Remember to always refer to the official repository and documentation for the most up-to-date information on wallet management in Boardwalk Cash.