## Inspiration

Our inspiration for Rainsurance came from recognizing a common issue faced by many vacationers. People often save up and wait months to take their dream vacations, investing significant amounts of money and time planning their trips. However, unexpected bad weather can mar the experience. We saw a need for a solution that would provide peace of mind to tourists in case of adverse weather conditions, allowing them to fully enjoy their vacations.

We are passionate about decentralized technologies and we want to promote the crypto revolution. With that in mind we see the intersection of smart contracts and insurance as an incredible opportunity to onboard many more new people about the benefits of blockchain technology. 

A major issue for insurance customers is the claim process. We are confident that through the use of Blockchain and Oracles like Chainlink, we can provide automation, transparency and fast response time and thus address this issue at its root. In doing so, we believe we can add a lot of value to the travel and events industries around the world.

## What it does

Rainsurance leverages Chainlink functions, the Etherisc GIF framework, and the Meteoblue API to provide a decentralized weather insurance protocol. It offers financial protection to tourists and event-goers against bad weather. If an event gets canceled due to weather, or a vacation is spoiled by rain, the payout from the insurance can cover additional costs incurred.

## How we built it

<img src="https://github.com/Rainsurance/.github/blob/master/profile/imgs/technical-diagram.jpg" alt="technical-diagram"/>

We used Etherisc's [GIF framework] (https://github.com/etherisc) - Brownie.

We used Chainlink's [Functions starter kit] (https://github.com/smartcontractkit/functions-hardhat-starter-kit) - Hardhat.

Frontend: Next.js/React.

## Challenges we ran into

Technically speaking there were many:
- The complexity behind the Etherisc framework and the lack of a compreehensive documentation;

- Etherisc Sandbox and example projects were all developed using Brownie, this was our fisrt experience with such framework;

- On the other hand, Chainlink Functions starter kit uses Hardhat. It wasn't easy to mix these two frameworks to offer a unique solution for the problem at hand;

- Chainlink Functions is dependent on Solidity ^0.8.7 and Etherisc's GIF is freezed to 0.8.2. We had to downgrade (and tweak) all Chainlink Funcions contract to make then fully compatible with 0.8.2;

- Chainlink Functions fullfillRequest currently has a gasLimit of 300k, which got us in trouble as callbacks triggered by the GIF are way more expensive than that. Thus we had to split the fulfillment process in two. First we just store the response inside the consumer contract; then a Chainlink Keeper periodically checks if new responses are available and executes the rest of the expensive callbacks when needed;

- ethers.js v6 currently has a bug with the BytesLike conversion necessary for passing the secrets for the Chainlink functions call. We had to downgrade to ethers.js v5;

With regard to the weather data, it took us some time to fully understand the complexity/accuracy of the simulated data and the difference with respect to real measurements, which in fact are extremely limited in certain locations. That's one the reasons why, by suggestion of our partner Meteoblue, we are starting with a small footprint (Miami, Rome, London).

Finally, product-wise, one of the biggest challenges we faced was finding the right balance between the needs of our potential customers and the insurance companies that might want to participate in our platform. Understanding the dynamics of the insurance market, the risk factors involved, and the expectations of the customers was a complex task.

## What's next for Rainsurance
We plan to continue improving and expanding our service through an extensive roadmap, some of the key milestones being:
- Onboard more regular travelers (not only web3 users) by enabling other payment methods like credit cards and PIX for the brazilian market;
- Introduce a new user type of user: the investor, which will be able to stake USDC in the risk pool and in return will receive a percentage of the premium paid by the clients.;
- Develop a Landing Page for explaing in details our offering and advantages for potencial customers;
- Establish partnerships with online agencies and booking services to enable a streamlined, one-click type of solution, for enrolling new customer into our rain insurance;

## Contracts, repositores and project structure

### GIF instance

Address: [0xc74170ad97c9eF3AdA552427Ea3163500D484961](https://mumbai.polygonscan.com/address/0xc74170ad97c9eF3AdA552427Ea3163500D484961)

### GIF Product (RainProduct)
This is our main contract where all logic behind our produto (rain insurance) is implemented, including the payout calculation.

Address: [0xab7DA5B6D9EB2DCA7f04c4DE9b9FeCD1e70fdA05](https://mumbai.polygonscan.com/address/0xab7DA5B6D9EB2DCA7f04c4DE9b9FeCD1e70fdA05#code)

### GIF Oracle (RainOracleCLFunctions)
This is the Chainlink Functions consumer contract and the Chainlink Keeper target.

Address: [0x0963e107D43b2452c825eaa02743083dcc723045](https://mumbai.polygonscan.com/address/0x0963e107D43b2452c825eaa02743083dcc723045#code)

### GIF RiskPool (RainRiskpool)
Here is where all logic behind the Riskpool is implemented. This is 

Address: [0x3D5cB3c62b17f3C37AdaDbf207A69018C65B6086](https://mumbai.polygonscan.com/address/0x3D5cB3c62b17f3C37AdaDbf207A69018C65B6086#code)

