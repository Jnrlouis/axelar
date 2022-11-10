# Axelar Bounty Submission

> Link to the contract address deployed in Axelar Testnet: `https://testnet.axelarscan.io/gmp/0xd4e9ab33c75b75ab11cd2cb4d87681de2ef7c288858813967da64dc125d14714`

## How it Works

- Clone this repo:

`git clone https://github.com/jnrlouis/axelar`

- Build contracts and tests:

`npm ci`
`npm run build`

- Set up deployer key

Create your .env file with your private keys

- Deploy Locally

`node scripts/deploy examples/call-contract [local|testnet]`

- Run Locally

`node scripts/deploy examples/call-contract-with-token [local|testnet]`
`node scripts/test examples/call-contract-with-token [local|testnet] ${"source-chain"} ${"destination-chain"} ${amount} ${account} ${"message"}`

Example: `node scripts/test examples/call-contract-with-token local "Moonbeam" "Ethereum" 100 0x91B6132cA348fbc5B884c9887F89f2eAC76E475e "Sending Breeze"`

## Modifications Made

Firstly, the `sendToMany` function in the solidity contract was adjusted to take an extra string parameter called `message`.
The message was encoded along with the receipient wallet address and parsed as bytes in the `payload` variable.

Then the `_executeWithToken` function was modified also, to decode the address and the message.

The respective `index.js` file was modified to accomodate the changes to successfully run tests, slicing the parsed arguements appropriately and accounting for the new string `message` parameter.