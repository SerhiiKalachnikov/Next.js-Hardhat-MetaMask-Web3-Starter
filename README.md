# Next.js + Hardhat MetaMask Web3 Starter

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![Hardhat](https://img.shields.io/badge/Hardhat-FFCC2F?style=for-the-badge&logo=hardhat&logoColor=black)
![MetaMask](https://img.shields.io/badge/MetaMask-E2761B?style=for-the-badge&logo=metamask&logoColor=white)
![Web3.js](https://img.shields.io/badge/Web3.js-F16822?style=for-the-badge&logo=web3dotjs&logoColor=white)

This project is a starter template for building Web3 applications using Next.js and Hardhat. It includes essential configurations and examples to help you get started quickly.

## Table of Contents

- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Development Server](#running-the-development-server)
- [Smart Contract Development](#smart-contract-development)
  - [Compiling Contracts](#compiling-contracts)
  - [Check existing contracts](#check-existing-contracts)
  - [Testing Contracts](#testing-contracts)
  - [Deploying Contracts](#deploy-contracts)
  - [Running Contract on Localhost Network](#run-contract-on-localhost-network)
- [Configure Metamask](#configure-metamask)
  - [Download MetaMask](#download-metamask)
  - [Connecting MetaMask to Local Network](#connecting-metamask-to-local-network)
  - [Import the accounts generated by Hardhat into MetaMask](#import-the-accounts-generated-by-hardhat-into-metamask)
- [Project Structure](#project-structure)
- [Learn More](#learn-more)
- [Contributing](#contributing)
- [License](#license)

## Getting Started

### Prerequisites

Ensure you have the following installed on your machine:

- Node.js (v20 or later)
- npm, yarn, pnpm, or bun (package managers)
- MetaMask (browser extension for Ethereum)

### Installation

Clone the repository:

```bash
git clone https://github.com/SerhiiKalachnikov/nextjs-hardhat-web3-starter.git
cd nextjs-hardhat-web3-starter
```

Install dependencies:

```bash
npm install
```

Create a `.env` file in the root directory and add the following environment variables:

```plaintext
NEXT_PUBLIC_WEB3_PROVIDER_URL="http://localhost:8545"
NEXT_PUBLIC_CONTRACT_ADDRESS=""
```

Replace `NEXT_PUBLIC_CONTRACT_ADDRESS` with the address of your deployed smart contract. In console output, you can find the address of the deployed contract.

### Running the Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Smart Contract Development

This project uses Hardhat for smart contract development. Hardhat is a development environment to compile, deploy, test, and debug your Ethereum software.
You can find the smart contracts in the `contracts` directory. The starter template includes a simple contract called `BuyMeACoffee.sol`.

### Compiling Contracts

To compile your smart contracts, run:

```bash
npx hardhat compile
```

This will compile the contracts and generate the artifacts in the `artifacts` directory.

## Check existing contracts

For check contracts which already deployed, run:

```shell
npx hardhat console --network hardhat
```

### Testing Contracts

To test your smart contracts, run:

```bash
npm run "test:contract:BuyMeACoffee"
```

### Deploy contracts

For deploy your smart contract, use the following command:

```shell
npm run deploy:contract:BuyMeACoffee
```

If you want to deploy it using a specific network, you can use the `--network` flag:

```shell
npx hardhat run ./contracts/deploy.ts --network hardhat
```

Update possible networks by updating `hardhat.config.ts` file.

### Run Contract on Localhost Network

To run your contract on localhost network, run:

```shell
npx hardhat node
```

This will start a local Ethereum network with 20 accounts, each with 10,000 ETH.

## Configure Metamask

### Download MetaMask

To interact with the smart contracts, you need to connect your application to MetaMask. Ensure MetaMask is installed and configured to connect to the appropriate network (e.g., localhost for local development).

[MetaMask download](https://chromewebstore.google.com/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn?hl=en&pli=1)

### Connecting metamask to local network

To connect your MetaMask wallet to the local network, follow these steps:

1. Open MetaMask and click on the network dropdown.
2. Click on "Custom RPC".
3. Enter the network name, RPC URL (<http://localhost:8545>), chain ID (1337), and symbol (ETH).
4. Click "Save".

### Import the accounts generated by Hardhat into MetaMask

1. Open MetaMask and click on the account icon.
2. Click on "Import Account".
3. Enter the private key of the account you want to import. (from the output of `npx hardhat node`)
4. Click "Import".

## Project Structure

```plaintext
├── LICENSE
├── README.md
├── app
│   ├── api
│   │   └── buyCoffee
│   │       └── route.ts
│   ├── components
│   │   ├── BuyCoffeeForm.tsx
│   │   └── ErrorBoundary.tsx
│   ├── favicon.ico
│   ├── fonts
│   │   ├── GeistMonoVF.woff
│   │   └── GeistVF.woff
│   ├── globals.css
│   ├── layout.tsx
│   ├── page.tsx
│   └── utils
│       ├── BuyMeACoffee.json
│       └── web3.ts
├── artifacts
│   ├── build-info
│   └── contracts
│       └── BuyMeACoffee.sol
│           ├── BuyMeACoffee.dbg.json
│           └── BuyMeACoffee.json
├── bin
├── cache
├── contracts
│   ├── BuyMeACoffee.sol
│   ├── BuyMeCoffee.test.ts
│   └── deploy.ts
├── global.d.ts
├── hardhat.config.ts
├── jest.config.js
├── next-env.d.ts
├── next.config.mjs
├── package-lock.json
├── package.json
├── postcss.config.js
├── postcss.config.mjs
├── tailwind.config.ts
└── tsconfig.json
```

- [`LICENSE`](LICENSE): Contains the license information for the project.
- [`README.md`](README.md): The main documentation file for the project, providing an overview and instructions.
- [`app/`](app/): Contains the main application code.
  - [`api/`](app/api/): Contains API routes.
    - [`buyCoffee/`](app/api/buyCoffee/): Contains the route handler for the buyCoffee API.
      - [`route.ts`](app/api/buyCoffee/route.ts): The API route handler for buying coffee.
  - [`components/`](app/components/): Contains React components used in the application.
    - [`BuyCoffeeForm.tsx`](app/components/BuyCoffeeForm.tsx): The form component for buying coffee.
    - [`ErrorBoundary.tsx`](app/components/ErrorBoundary.tsx): A component for catching and displaying errors.
  - [`favicon.ico`](app/favicon.ico): The favicon for the application.
  - [`fonts/`](app/fonts/): Contains custom fonts used in the application.
    - [`GeistMonoVF.woff`](app/fonts/GeistMonoVF.woff): A custom font file.
    - [`GeistVF.woff`](app/fonts/GeistVF.woff): Another custom font file.
  - [`globals.css`](app/globals.css): Global CSS styles for the application.
  - [`layout.tsx`](app/layout.tsx): The layout component for the application.
  - [`page.tsx`](app/page.tsx): The main page component for the application.
  - [`utils/`](app/utils/): Contains utility files.
    - [`BuyMeACoffee.json`](app/utils/BuyMeACoffee.json): ABI file for the BuyMeACoffee smart contract.
    - [`web3.ts`](app/utils/web3.ts): Web3 utility functions.
- [`artifacts/`](artifacts/): Contains build artifacts generated by Hardhat.
  - [`build-info/`](artifacts/build-info/): Contains build information.
  - [`contracts/`](artifacts/contracts/): Contains contract build artifacts.
    - [`BuyMeACoffee.sol/`](artifacts/contracts/BuyMeACoffee.sol/): Build artifacts for the BuyMeACoffee smart contract.
      - [`BuyMeACoffee.dbg.json`](artifacts/contracts/BuyMeACoffee.sol/BuyMeACoffee.dbg.json): Debug information for the BuyMeACoffee contract.
      - [`BuyMeACoffee.json`](artifacts/contracts/BuyMeACoffee.sol/BuyMeACoffee.json): ABI and bytecode for the BuyMeACoffee contract.
- [`bin/`](bin/): Contains binary files (if any).
- [`cache/`](cache/): Contains cache files generated by the build process.
- [`contracts/`](contracts/): Contains Solidity smart contracts and related files.
  - [`BuyMeACoffee.sol`](contracts/BuyMeACoffee.sol): The BuyMeACoffee smart contract.
  - [`BuyMeCoffee.test.ts`](contracts/BuyMeCoffee.test.ts): Test file for the BuyMeACoffee smart contract.
  - [`deploy.ts`](contracts/deploy.ts): Deployment script for the BuyMeACoffee smart contract.
- [`global.d.ts`](global.d.ts): Global TypeScript declarations.
- [`hardhat.config.ts`](hardhat.config.ts): Configuration file for Hardhat.
- [`jest.config.js`](jest.config.js): Configuration file for Jest.
- [`next-env.d.ts`](next-env.d.ts): Next.js environment variables.
- [`next.config.mjs`](next.config.mjs): Configuration file for Next.js.
- [`package-lock.json`](package-lock.json): Lock file for npm dependencies.
- [`package.json`](package.json): Contains project metadata and dependencies.
- [`postcss.config.js`](postcss.config.js): Configuration file for PostCSS.
- [`postcss.config.mjs`](postcss.config.mjs): Another configuration file for PostCSS.
- [`tailwind.config.ts`](tailwind.config.ts): Configuration file for Tailwind CSS.
- [`tsconfig.json`](tsconfig.json): TypeScript configuration file.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

To learn more about Hardhat, take a look at the following resources:

- [Hardhat Documentation](https://hardhat.org/getting-started/) - learn about Hardhat features and API.
- [Hardhat GitHub Repository](https://github.com/nomiclabs/hardhat) - your feedback and contributions are welcome!

To lean more about Web3, take a look at the following resources:

- [Web3.js Documentation](https://web3js.readthedocs.io/en/v1.3.4/) - learn about Web3.js features and API.

To learn Arbitrum, take a look at the following resources:

- [Arbitrum Documentation](https://docs.arbitrum.io/welcome/arbitrum-gentle-introduction) - learn about Arbitrum features and API.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## License

This project is licensed under the MIT License.
