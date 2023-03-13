# dApp for NFT Ticketing
This page is the main page for others Sub-repositories. Frontend is hosted in Vercel (https://nextjs-nft-ticketing-mui.vercel.app). The backend is only implemented in Goerli Testnet with [NFT Marketplace](https://goerli.etherscan.io/address/0x879f5a1608e4CEd89766a6A2e1051Fd7e1B13698) and [EventFactory](https://goerli.etherscan.io/address/0x6962d60830947e32d3D22bED3542E9e846CD3F01) right now. The Factory contract will generate EventContract instance using createEvent() function. Here is an example of [EventContract](https://goerli.etherscan.io/token/0xddf06971c21b916e912a474031daf5a08140a5d3) Template.  

The Event metadata will be stored in infura IPFS. Here is an example of [URI](https://gateway.pinata.cloud/ipfs/QmNMsrAEvpZFx7SXThYVZ5BiVw6nt4h9tgeUZmnZFxjJ6j) template. Our schema of graphQL is defined in [here](https://github.com/hlpangaa/subgraph-nft-ticketing/blob/main/schema.graphql). The queries used by frontend is [here](https://github.com/hlpangaa/nextjs-nft-ticketing-mui/blob/main/constants/subgraphQueries.js).


To use the service, install metamask in your OS. Connect to Wallet and change the network to Goerli.

## Sub-repositories
Backend (https://github.com/hlpangaa/hardhat-nft-ticketing)

Frontend (https://github.com/hlpangaa/nextjs-nft-ticketing-mui)

Subgraph (https://github.com/hlpangaa/subgraph-nft-ticketing)

## Application Workflow
- Deployed smart contracts in Ethereum network using hardhat framework, utilized a Next JS frontend to allow user to use Metamask to interact with the smart contract in a Web3 fashsion
- Hosted the frontend in Vercel(next-js foundation team) and connected with theGraph(indexing protocal) to listen the event emitted under the contracts, stored metadata in InterPlanetary File System(IPFS)


## Tech Stack Used
[Hardhat](https://hardhat.org/): Hardhat is a development environment for Ethereum software. It consists of different components for editing, compiling, debugging and deploying your smart contracts and dApps, all of which work together to create a complete development environment.

[TheGraph](https://thegraph.com/studio/subgraph/nftticketing/playground): The Graph is an indexing protocol for querying networks like Ethereum and IPFS. The event emited from the contracts developed will be listened and indexed in the Graph so our next JS frontend can get the data from blockchain and present fast. 

[Etherscan](https://goerli.etherscan.io/address/0x879f5a1608e4CEd89766a6A2e1051Fd7e1B13698): Etherscan is a Block Explorer and Analytics Platform for Ethereum, a decentralized smart contracts platform. It's for testing purpose.

[Vercel](https://vercel.com/dashboard) is a cloud-based platform for deploying, scaling, and collaborating on web applications. It allows developers to deploy websites and applications quickly and easily, with automatic scaling and a global content delivery network (CDN) to ensure fast performance.

[Infura](https://app.infura.io/) infura IPFS is a service provided by Infura, a company that offers scalable and reliable infrastructure for decentralized web technologies such as Ethereum and IPFS


## No longer used
Fleek - cannot store API key as encrpted envrionment variables
Pinata - issue for client side rendering because it has a package dependency of file system package(fs). There is no fs in client side.

[Fleek](https://app.fleek.co/#/sites/little-poetry-5496/settings/general?accountId=d5e70534-8482-4d48-bad2-440122944ad5): Fleek is a suite of tools with everything you need to build modern sites and apps on the Open Web and its protocols seamlessly. We hosted our frontend in the Fleek node so people can enquire the site via public internet.

[Pinata](https://app.pinata.cloud/pinmanager#): Pinata. cloud is a pinning service that allows users to host files on the IPFS network. We stored metadata and images in Pinata.

### ERC
- erc721 NFT
- ERC2981 Royalty payment
- ERC721 Storage

### Web3 developemnt library
- openzeppelin -- contract development
- infura -- ipfs-http-client to add file to IPFS
- apolo -- useQuery to interact with the Graph DB
- Wagmi -- useContractRead and useContractWrite hook
- Rainbowkit -- wallet connection

## Scope of functions
- [ ] 1. eventFactory.sol
- [ ] Demo Use case (Event Organizer): 
  - [ ] 1.1 create event with Deposit(Fig 4.2.2)
    - [ ] 1.1.1 upload images in return of IPFS links
    - [ ] 1.1.2 input info and generate a JSON
      - [ ] 1.1.2.1 event info (name; seat type, seat cap, price, celling, queing machanism, start date)
      - [ ] 1.1.2.2 IPFS link
  - [ ] 1.2 view historical event record
  - [ ] 1.3 view active record
  - [ ] 1.4 cancel event
- [ ] 2. eventContract.sol
- [ ]  Demo Use case (Ticket Holder): 
  - [ ] 2.1 buy ticket in primary market; (minting)
  - [ ] 2.2 buy and list ticket in secondary market (listing and purchase)
  - [ ] 2.3 view event under marketplace address 
  - [ ] 2.4 view event under current user address
  - [ ] 2.5 view transcational record under current user address
  - [ ] 2.6 royality payment protocal
  - [ ] 2.7 Withdraw fund
- [ ] 3. identityProvider.sol
- [ ] Demo Use Case (Identity Provider)
  - [ ] 3.1 create profile (Fig 4.2.1)
    - [ ] 3.1.1 mobile phone binding implementation
    - [ ] 3.1.2 incentive implementation
  - [ ] 3.2 validate event organizer 

## Project Team Shortcut
[Project Team One Drive](https://connecthkuhk-my.sharepoint.com/personal/u3590287_connect_hku_hk/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Fu3590287%5Fconnect%5Fhku%5Fhk%2FDocuments%2FFITE7001%5FA%2DTeam&FolderCTID=0x012000E1CEC5B499A6824BB24DB935A2B2CB10)

[Project Timeline](https://www.notion.so/ba99bc82597f40ea9b77d748156058a2?v=0cc4e4853e184202978bc97287c6416f)

[Diagram](https://lucid.app/lucidchart/e8a1a225-ec49-4732-baaa-f6fd0f8ebb50/edit?viewport_loc=100%2C-119%2C5565%2C2235%2C0_0&invitationId=inv_503a40d6-7409-4666-947f-a204a3633f7d)

## Remarks
### Use Goerli Network 
Currently deployed to test net only. Please swap to **Goerli** network to interact with the web and contract.

### Use new testing wallet
Event it's pre-production. Please do not use real wallet to interact. Do not just simply create a new testing account in your existing wallet as the seed(and private key) is the same. So using that testing account might leak your key.



# Reference
[Patrick Collins freeCodeCamp](https://github.com/smartcontractkit/full-blockchain-solidity-course-js)

[Factory Patterns](https://blog.logrocket.com/cloning-solidity-smart-contracts-factory-pattern/)

[openzeppelin-contracts](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol)

[solidity code sample](https://solidity-by-example.org/)

[deApp NFT Marketplace/NFT Factory/NFTcode](https://github.com/Fantom-foundation/Artion-Contracts/tree/5c90d2bc0401af6fb5abf35b860b762b31dfee02/contracts)

[Github NFTicket hackathon](https://github.com/Abbas-Khann/NFTicket)

[NFT Ticketing Market Analysis](https://www.leewayhertz.com/how-nft-ticketing-works/#How-does-NFT-work-for-Ticketing?)

[NFT Startup](https://nftnow.com/features/nft-tickets-are-the-future-of-live-music/)

[NFT Startup;](https://nftinvestorjournal.com/nft-ticketing-companies/)

[GET Protocol](https://www.youtube.com/watch?v=GsUkMxibzwo&t=2335s&ab_channel=GETProtocol)

[GET Summary](https://blog.guts.tickets/summary-of-the-get-protocol-c4812219d21d)

[GET faq](https://www.get-protocol.io/content/the-get-protocol-tokenomics-faq)

[Yellowheart Whitepaper](https://static.yh.io/about/assets/pdf/yellowheart-protocol-whitepaper.pdf)

[Yellowheart](https://static.yh.io/about/assets/pdf/yh-capabilities.pdf)

[yourtickerprovider.nl](https://www.yourticketprovider.nl/)

[DeTi](https://link.springer.com/article/10.1007/s10922-022-09675-3)
