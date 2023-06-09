## Inspiration

Our inspiration for Rainsurance came from recognizing a common issue faced by many vacationers. People often save up and wait months to take their dream vacations, investing significant amounts of money and time planning their trips. However, unexpected bad weather can mar the experience. We saw a need for a solution that would provide peace of mind to tourists in case of adverse weather conditions, allowing them to fully enjoy their vacations.

We are passionate about decentralized technologies and we want to promote the crypto revolution. The intersection of smart contracts and insurance presented an incredible opportunity to onboard many people about the benefits of blockchain technology. 

A major issue for insurance customers is the claim process. We are confident that through the use of Blockchain and Oracles like Chainlink, we can provide automation, transparency and fast response time and thus address this issue at its root. In doing so, we believe we can add a lot of value to the travel and events industries around the world.

## What it does

Rainsurance leverages Chainlink functions, the Etherisc GIF framework, and the Meteoblue API to provide a decentralized weather insurance protocol. It offers financial protection to tourists and event-goers against bad weather. If an event gets canceled due to weather, or a vacation is spoiled by rain, the payout from the insurance can cover additional costs incurred.

## How we built it

<img src="[https://github.com/Liquidity-Wars/.github/blob/main/profile/imgs/RewardsRatioAndEarnings.png](https://github.com/Rainsurance/.github/blob/master/profile/imgs/technical-diagram.jpg)" alt="technical-diagram" width="800" height="450"/>

We used Etherisc's GIF framework - Brownie.
We used Chainlink Functions starter kit - Hardhat.
We built our frontend from scratch using Next.js/React.

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

## Accomplishments that we're proud of

We are proud to have created a solution that addresses a real-world problem and has the potential to disrupt the travel industry, all using blockchain and web3. We successfully built the project leveraging robust technologies/frameworks/partners, thus after some validation during the MVP phase, we are confident that we have a production-ready solution at hand.
On top of that we managed to overcome all the technical challenges described in the previous section, which made us very happy and proud.

## What we learned

First of all, we have learned a lot about the insurance market and the techinalities behind weather forecasting.
We now have an intermediate to advanced level of knowledge about Etherisc's GIF which can be leveraged for this insurance proposed here or any other type of decentralized insurance we might be working in the future.
We also had the opportunity to learn in practice the recently launched Chainlink service - Chainlink Functions.
The intersection of smart contracts and insurance presented an incredible opportunity to onboard many people about the benefits of blockchain technology and the use of oracles. A pain point for insurance customers is the claim process, and we are confident that the benefits of oracles like Chainlink will open up a lot of new use cases. We also aim to deliver more value to the travel industry and event organizers around the world. 

## What's next for Rainsurance
We plan to continue improving and expanding our service through an extensive roadmap, some of the key milestones being:
- Onboard more regular travelers (not only web3 users) by enabling other payment methods like credit cards and PIX for the brazilian market;
- Introduce a new user type of user: the investor, which will be able to stake USDC in the risk pool and in return will receive a percentage of the premium paid by the clients.;
- Develop a Landing Page for explaing in details our offering and advantages for potencial customers;
- Establish partnerships with online agencies and booking services to enable a streamlined, one-click type of solution, for enrolling new customer into our rain insurance;

Don't let the rain ruin your vacation or events! Rainsurance has got you covered. We believe that these developments will take Rainsurance to new heights.
