# cross-chain-bridge

build a cross-chain bridge to allow users to stake tokens, create liquidity pools, and interact with our ERC-20 for minimal gas fees.

1 - deploy the ERC-20 on another chain. now our token is on two chains.

2 - subscribe to smart contract event, so we know when a user deposits tokens

```
const query = new Moralis.Query('tokenDeposit');
const subscription = await query.subscribe();
```

3 - send tokens from user to protocol
```
const options = {type: "erc20", 
                 amount: Moralis.Units.Token("0.5", "18"), 
                 receiver: "0x..",
                 contract_address: "0x.."}
let result = await Moralis.transfer(options)
```

4- define handler for event emitter and send tokens on other chain


**todo: figure out how to handle wallet addresses**

- https://docs.moralis.io/moralis-server/database/live-queries#create-a-subscription
- https://docs.moralis.io/moralis-server/sending-assets
