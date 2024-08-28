# Boardwalk Cash System Overview

This document provides a categorized overview of the systems and components in the Boardwalk Cash project, based on the repository analysis and open issues.

## 1. Frontend Systems

### 1.1 User Interface (UI)
- Framework: Next.js with TypeScript
- Key Components:
  - Balance display
  - Activity indicator
  - Lightning send/receive buttons
  - Send modal
  - Clipboard button
  - Ecash buttons (in development)
  - PWA Refresh button (proposed in Issue #78)
  - ConfirmEcashReceiveModal
  - TransactionHistoryDrawer
  - EcashTapButton
  - NotificationDrawer
  - SettingsSidebar

### 1.2 State Management
- Primary Tool: Redux Toolkit
- Key Slices:
  - UserSlice: Manages user data, initialization, and actions
  - WalletSlice: Handles wallet state, keysets, and balance management
  - ActivitySlice: Manages activity state and notifications
  - CashuSlice: Handles Cashu-specific state and operations

### 1.3 Custom Hooks
- useCashu: Manages Cashu mint interactions and proof storage
- useNwc: Handles Nostr Wallet Connect (NWC) requests and Prism payments
- useCashuContext and useProofStorage: Provide context for Cashu operations
- useProofManager: Manages proof validation and balance updates

### 1.4 Routing and Navigation
- Uses Next.js routing
- Main page (index.tsx) checks for existing keysets in localStorage:
  - If keysets exist, redirects to '/wallet'
  - If no keysets, redirects to '/setup'
- Wallet page (wallet.tsx) handles token queries and user initialization

## 2. Backend Systems

### 2.1 API Endpoints
- RESTful API facilitating:
  - LUD16 operations
  - CRUD operations on the database
  - Mint operations (paying invoices, creating invoices, checking/exchanging proofs)

### 2.2 Database
- Type: PostgreSQL
- ORM: Prisma

## 3. Integration Systems

### 3.1 Lightning Network
- Features:
  - Send and receive Lightning payments
  - Auto-generated Lightning Address for receiving payments

### 3.2 Cashu Ecash
- Local storage of balance as e-cash
- Integration with Cashu mint and cashu-ts library
- Proof management and validation
- Support for multiple keysets (mints)

### 3.3 Nostr Integration
- Nostr Wallet Connect (NWC) for initiating payments from apps
- Nostr Wallet Authentication (NWA) for seamless app connections

## 4. Deployment and Infrastructure

### 4.1 Containerization
- Docker for containerizing the Next.js app and database
- Docker Compose for orchestrating deployment

### 4.2 Progressive Web App (PWA)
- PWA capabilities for improved mobile experience

## 5. Key Challenges and Improvement Areas

### 5.1 User Management
- Issue #79: Need for app-level user initialization
- Improved error handling for user not found scenarios
- More secure storage of user keys and sensitive information

### 5.2 State Management and Data Persistence
- Issue #53: Browser refresh causing token unavailability
- Issue #67: Proposed refactoring to use context for improved state management
- Heavy reliance on localStorage for key application data (e.g., keysets, proofs)
- Periodic proof validation and balance updates

### 5.3 Wallet Management
- Handling of multiple keysets and mints
- Balance locking mechanism for preventing unintended updates
- Synchronization between local state and server state

### 5.4 Transaction Handling
- Issue #29: Error in minting tokens exceeding mint reserves
- Issue #43: Decimal place restriction on amount inputs
- Handling of locked proofs and trusted mints

### 5.5 User Experience
- Issue #78: Addition of refresh button for improved mobile and PWA experience
- Handling of multiple tabs to prevent concurrent usage
- Improved error messaging and user feedback

## 6. Security Considerations

### 6.1 Local Storage
- Current use of localStorage for storing user proofs, keysets, and keys
- Use of sessionStorage for tab management
- Potential need for a more secure and centralized storage solution

### 6.2 Key Management
- Handling of public and private keys for user accounts
- Integration with Nostr for key management

### 6.3 Token Handling
- Decoding and validation of received tokens
- Handling of locked proofs and trusted mints

### 6.4 Multi-mint Support
- Security implications of supporting multiple mints
- Proper isolation and management of keys and proofs from different mints

This overview provides a holistic view of the Boardwalk Cash application, highlighting its main systems, current challenges, and areas for improvement. It serves as a foundation for addressing open issues and making informed decisions about the application's architecture and feature development.