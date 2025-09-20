## What it does

PlayStoreX is a decentralized gaming asset marketplace built on Filecoin that enables game developers, creators, and players to buy, sell, and trade gaming assets like skins, models, textures, and DLCs. Think of it as "Steam on Web3" - a platform where gaming assets are stored permanently on the decentralized Filecoin network, ensuring they never disappear even if game servers go offline.

The platform features a complete marketplace with asset browsing, real-time upload to Filecoin storage, smart contract integration for transactions, and a modern gaming-focused UI. Users can upload their gaming assets, set prices, enable CDN for faster delivery, and manage their digital assets through a comprehensive dashboard.

## The problem it solves

Traditional gaming platforms like Steam, Epic Games Store, and others rely on centralized servers to store and deliver gaming assets. This creates several critical problems:

1. **Asset Loss**: When game servers go offline or companies shut down, all purchased assets disappear forever
2. **Platform Lock-in**: Assets are tied to specific platforms and can't be transferred or used elsewhere
3. **Censorship**: Centralized platforms can remove or restrict access to assets
4. **High Fees**: Platform fees can be as high as 30% of each transaction
5. **Limited Ownership**: Players don't truly own their digital assets

PlayStoreX solves these issues by leveraging Filecoin's decentralized storage network, ensuring assets are permanently stored and accessible, while smart contracts enable true ownership and peer-to-peer trading without platform lock-in.

## Challenges I ran into

**Filecoin Integration Complexity**: The biggest challenge was integrating with the Filecoin network through the Synapse SDK. The documentation was limited, and I had to reverse-engineer the existing codebase to understand how to properly upload files and create datasets.

**Gas Estimation Failures**: Encountered persistent "Failed to create data set" errors with contract reverts during gas estimation. This required implementing robust error handling, fallback mechanisms, and balance checking to ensure users have sufficient USDFC and FIL before attempting transactions.

**Smart Contract Gas Optimization**: Initially, storing large metadata strings on-chain was extremely expensive. I had to redesign the entire smart contract architecture to store only essential data on-chain and metadata hashes, with full metadata stored on Filecoin for gas efficiency.

**Wallet Integration Issues**: Getting the ethers.js signer to work properly with the Synapse SDK required debugging the `useEthers` hook and fixing scope issues in callback functions.

**Real-time Upload Progress**: Implementing smooth, real-time progress tracking for Filecoin uploads while handling multiple files simultaneously was technically challenging, requiring careful state management and error handling.

## Technologies I used

**Frontend**: Next.js 15, TypeScript, Tailwind CSS, Framer Motion for animations
**Blockchain**: Solidity, Hardhat, ethers.js v6, Filecoin network
**Storage**: Filecoin Warm Storage Service, Synapse SDK, IPFS
**Web3**: RainbowKit, Wagmi, MetaMask integration
**Smart Contracts**: OpenZeppelin, custom gas-optimized contracts
**Development**: pnpm, ESLint, Prettier
**UI/UX**: Lucide React icons, custom gaming-themed components

## How we built it

**Phase 1 - Smart Contract Architecture**: Designed and deployed gas-optimized smart contracts using Solidity, implementing a marketplace contract, NFT contract for gaming assets, and payment manager. Used OpenZeppelin for security and gas optimization techniques.

**Phase 2 - Filecoin Integration**: Integrated the Synapse SDK to handle file uploads to Filecoin's decentralized storage network. Implemented preflight checks for USDFC balance and storage allowances, with comprehensive error handling and fallback mechanisms.

**Phase 3 - Frontend Development**: Built a modern Next.js application with TypeScript, featuring multiple pages (landing, marketplace, upload, dashboard) with responsive design and gaming-focused UI components.

**Phase 4 - Web3 Integration**: Connected the frontend to smart contracts using ethers.js, implemented wallet connection with RainbowKit, and created custom hooks for contract interactions and file uploads.

**Phase 5 - User Experience**: Added real-time upload progress tracking, comprehensive error handling, success modals, and a complete asset management system with metadata storage on Filecoin.

## What we learned

**Filecoin Ecosystem**: Gained deep understanding of how Filecoin's decentralized storage works, including datasets, storage providers, and the Synapse SDK integration patterns.

**Gas Optimization**: Learned advanced Solidity gas optimization techniques, including storing metadata off-chain and using struct packing to reduce transaction costs.

**Web3 UX Challenges**: Discovered the importance of comprehensive error handling and user feedback in Web3 applications, as blockchain transactions can fail for many reasons.

**State Management**: Mastered complex state management for real-time file uploads, progress tracking, and error handling across multiple asynchronous operations.

**Decentralized Storage**: Understood the trade-offs between centralized and decentralized storage, including costs, reliability, and user experience considerations.

## What's next for PlayStoreX

**Enhanced Gaming Features**: Add support for 3D model previews, asset versioning, and compatibility checking between different game engines.

**Community Features**: Implement creator profiles, asset reviews and ratings, social features, and community-driven curation.

**Advanced Marketplace**: Add auction functionality, asset bundles, subscription models, and automated royalty distribution for creators.

**Cross-Chain Integration**: Expand beyond Filecoin to support other storage networks and blockchain ecosystems for broader asset compatibility.

**Developer Tools**: Create SDKs and APIs for game developers to easily integrate PlayStoreX into their games, with plugins for Unity, Unreal Engine, and other popular game engines.

**Mobile App**: Develop native mobile applications for iOS and Android to make asset trading accessible on mobile devices.

**AI-Powered Features**: Implement AI-driven asset recommendations, automatic tagging, and content moderation to improve the marketplace experience.