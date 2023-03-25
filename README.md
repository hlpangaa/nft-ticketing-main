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

## Architecture Diagram 

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/reference-arc-diagram.png)
[Reference from thenewstack.io](https://thenewstack.io/web3-architecture-and-how-it-compares-to-traditional-web-apps/)

In our architecture diagram, the user's browser acts as the entry point for the application. The frontend application is built using Next.js and relies on several JavaScript libraries, including Rainbowkit for connecting to the user's Metamask wallet, Wagmi for interacting with the Ethereum network, Infura for accessing IPFS, and Apollo Client for fetching data from TheGraph network.

The Ethereum network hosts the smart contracts written in Solidity and developed using tools such as Hardhat, Remix and Ganache. The IPFS system provides a decentralized file storage system for storing JSON and image files. TheGraph network provides an indexing protocol for querying the blockchain.

When a user logs into their Metamask wallet, they can interact with the smart contracts on the Ethereum network through the frontend application. The frontend can also upload and retrieve files from IPFS, as well as fetch data from TheGraph network using Apollo Client.


## Tech Stack Used
[Hardhat](https://hardhat.org/): Hardhat is a development environment for Ethereum software. It consists of different components for editing, compiling, debugging and deploying your smart contracts and dApps, all of which work together to create a complete development environment.

[TheGraph](https://thegraph.com/studio/subgraph/nftticketing/playground): The Graph is an indexing protocol for querying networks like Ethereum and IPFS. The event emited from the contracts developed will be listened and indexed in the Graph so our next JS frontend can get the data from blockchain and present fast. 

[Vercel](https://vercel.com/dashboard) is a cloud-based platform for deploying, scaling, and collaborating on web applications. It allows developers to deploy websites and applications quickly and easily, with automatic scaling and a global content delivery network (CDN) to ensure fast performance.

[Infura](https://app.infura.io/) infura IPFS is a service provided by Infura, a company that offers scalable and reliable infrastructure for decentralized web technologies such as Ethereum and IPFS

[Etherscan](https://goerli.etherscan.io/address/0x879f5a1608e4CEd89766a6A2e1051Fd7e1B13698): Etherscan is a Block Explorer and Analytics Platform for Ethereum, a decentralized smart contracts platform. It's for testing purpose.

## Screenshow:

### 1. Recent-Event
1. Display all active event created by eventFactory contract. It's public visible page.

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Recent-Event.png)

### 2. Create-Event
1. Allow users to create event via eventFactory Contract. With input form to configure their own event and upload button to upload the image to IPFS.

2. Poster image together with the event data will be uploaded to IPFS. The URI of the json file will be returned before contract creation.

3. The URI will be bundled with the eventContract as contractURI and can be later using to set tokenURI.

4. IPFS file cannot be overwritten as the content ID (CID) is a generated by cryptographical hash. So the event data will not be modified unless reset the entile contract URI.

5. user need to sign this transcation in metamask as this is a write contract function and they have to pay incurred fee. (no platform fee setting currently, just gas fee)

6. Loading status will be rendered in the frontend page during the transaction in progress. Contract transcation hash and will be displayed when transcation receipt return.

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/create-event.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Waiting-for-approval.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/ethscan-tx-hash.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/IPFS-json.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/IPFS-Image.png)

### 2. Ticket Swap
1. Allow users to Trade the tickets. Offer providers (seller) can update and delist the offer. Buyer can buy the offer.

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Ticket-Swap2.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Update-Offer.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Delist-Offer.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Buy-Offer.png)

### 3. My Event
1. A Page to show events owned by signer addgress. 

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Recent-Event.png)

### 4. Event Detail
1. Allow user to mint the ticket.

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/My-Event-Mint.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/My-Event-NFT-Minted.png)

### 5. My Ticket
1. A Page to show tickets owned by signer addgress.

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/My-Ticket.png)

### 6. Ticket Detail
1. Allow users to Trade the tickets

2. User need to approve NFT marketplace to trade first.

3. non-owner can still access the page but cannot interact with the any function.

4. user can view the URI in clear format by clicking hidden/display URI

5. QR code can be used for entering the evnet.

6. The ticket price should between 0 to price celling. Otherwise, error message will be shown and block the dialog window closing.

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Ticket-Detail-no-Approve.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Ticket-Detail-listed.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Approve-Marketplace.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Ticket-Detail-has-approve.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Sell-Ticket.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Sell-Ticket--veCase.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Sell-Ticket-Trans.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/Ticket-Detail-listedItem.png)


### 7. Payment History and withdraw fund
1. user can view the payment history in the marketplace. 

2. user can view the fund deposited in the marketplace (fund come from selling ticket in P2P market), they can withdrwa the fund as well.

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/PaymentHistory.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/WithDraw%20Proceeds.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/WithDrawl-fund-in-progress.png)

![screenshoot](https://raw.githubusercontent.com/hlpangaa/nft-ticketing-main/master/Assets/WithDrawl-fund-completed.png)

### No longer used
Fleek - cannot store API key as encrpted envrionment variables.  
Pinata - issue for client side rendering because it has a package dependency of file system package(fs). There is no fs in client side.  

[Fleek](https://app.fleek.co/#/sites/little-poetry-5496/settings/general?accountId=d5e70534-8482-4d48-bad2-440122944ad5): Fleek is a suite of tools with everything you need to build modern sites and apps on the Open Web and its protocols seamlessly. We hosted our frontend in the Fleek node so people can enquire the site via public internet.

[Pinata](https://app.pinata.cloud/pinmanager#): Pinata. cloud is a pinning service that allows users to host files on the IPFS network. We stored metadata and images in Pinata.

### ERC
- ERC721 NFT
- ERC2981 Royalty payment -- to ensure the artist can have a share of secondary market trade
- ERC721 Storage Extension. -- to implement URI.

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
