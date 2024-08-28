# Boardwalk Cash

This folder contains comprehensive documentation and analysis of the Boardwalk Cash project, an ecash wallet application.

## Project Overview

Boardwalk Cash is a Lightning / Cashu Ecash wallet designed for fast and easy onboarding and use. It integrates Lightning Network payments with Cashu ecash protocols, providing a user-friendly interface for managing digital cash transactions.

- GitHub Repository: https://github.com/MakePrisms/boardwalkcash
- Website: https://boardwalkcash.com/

## Key Features

- Lightning Network Integration: Send and receive Lightning payments
- Cashu Ecash Wallet: Store balance locally as e-cash
- Lightning Address: Receive payments using an auto-generated Lightning Address
- Nostr Wallet Connect (NWC): Initiate payments from apps
- Nostr Wallet Authentication (NWA): Seamless app connections
- Multi-mint Support: Manage multiple keysets from different mints
- Progressive Web App (PWA) Capabilities

## Technology Stack

- Frontend: Next.js with TypeScript
- State Management: Redux Toolkit
- Backend: RESTful API with PostgreSQL database (managed by Prisma ORM)
- Containerization: Docker and Docker Compose

## Contents

1. [System Overview](system_overview.md)
   - Comprehensive breakdown of frontend and backend systems
   - Integration details with Lightning Network, Cashu, and Nostr
   - Key challenges and improvement areas
   - Security considerations

2. [User Management](user-management.md)
   - User state structure and initialization process
   - Key components and actions in user management
   - Known issues and suggested improvements

3. [Wallet Management](wallet-management.md)
   - Wallet state structure and key components
   - Keyset management and balance operations
   - Multi-mint support details

4. [Architecture](architecture.md)
   - Detailed breakdown of the application's architecture
   - Component interactions and data flow

5. [Known Issues](known-issues.md)
   - Current challenges in the application
   - Potential solutions and improvement suggestions

## Contributing

For the most up-to-date information on contributing to the Boardwalk Cash project, please refer to the official repository's contributing guidelines.

## Note

The information in these documents is based on our analysis of the Boardwalk Cash repository and may not reflect the most current state of the project. Always refer to the official repository and documentation for the most up-to-date and accurate information.