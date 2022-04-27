# MetaCoin
Project of a simple token to learn and understand more about how to create a token and see the interaction between accounts sending and receiving balances

Instructions of how to run the program and interact with the token.

You will first need to have Truffle installed, you can do with the command below:

```
npm install -g truffle
```

Then you will compile your smart contracts before creating a local blockchain and interacting with it.

```
truffle compile
```

To deploy our smart contracts, we're going to need to connect to a blockchain. Truffle has a built-in personal blockchain that can be used for testing. This blockchain is local to your system and does not interact with the main Ethereum network.

You can create this blockchain and interact with it using Truffle Develop.

```
truffle develop
```

After, you will see some information that seems like this (your's gonna be different, but alike)

```
Truffle Develop started at http://127.0.0.1:9545/

Accounts:
(0) 0x627306090abab3a6e1400e9345bc60c78a8bef57
(1) 0xf17f52151ebef6c7334fad080c5704d77216b732
(2) 0xc5fdf4076b8f3a5357c5e395ab970b5b54098fef
(3) 0x821aea9a577a9b44299b9c15c88cf3087f3b5544
(4) 0x0d1d4e623d10f9fba5db95830f7d3839406c6af2
(5) 0x2932b7a2355d6fecc4b5c0b6bd44cc31df247a2e
(6) 0x2191ef87e392377ec08e7c08eb105ef5448eced5
(7) 0x0f4f2ac550a1b4e2280d04c21cea7ebd822934b5
(8) 0x6330a553fc93768f612722bb8c2ec78ac90b3bbc
(9) 0x5aeda56215b167893e80b4fe645ba6d5bab767de

Private Keys:
(0) c87509a1c067bbde78beb793e6fa76530b6382a4c0241e5e4a9ec0a0f44dc0d3
(1) ae6ae8e5ccbfb04590405997ee2d52d2b330726137b875053c36d94e974d162f
(2) 0dbbe8e4ae425a6d2687f1a7e3ba17bc98c673636790f1b8ad91193c05875ef1
(3) c88b703fb08cbea894b6aeff5a544fb92e78a18e19814cd85da83b71f772aa6c
(4) 388c684f0ba1ef5017716adb5d21a053ea8e90277d0868337519f97bede61418
(5) 659cbb0e2411a44db63778987b1e22153c086a95eb6b18bdf89de078917abc63
(6) 82d052c865f5763aad42add438569276c00d3d88a2d062d36b2bae914d58b8c8
(7) aa3680d5d48a8283413f7a108367c7299ca73f553735860a87b08f39395618b7
(8) 0f62d96d6675f32685bbdb8ac13cda7c23436f63efbb9d07700d8669ff12b7c4
(9) 8d5366123cb560bb606379f90a0bfd4769eecc0557f1b362dcae9012b548b1e5

Mnemonic: candy maple cake sugar pudding cream honey rich smooth crumble sweet treat

⚠️  Important ⚠️  : This mnemonic was created for you by Truffle. It is not secure.
Ensure you do not use it on production blockchains, or else you risk losing funds.

truffle(development)>
```

This shows ten accounts (and their private keys) that can be used when interacting with the blockchain.

After running this you will be in truffle develop prompt, so you don't need anymore to use the prefix `truffle`, to migrate your contracts do the blockchain only use the command below

```
migrate
```

You will see something like this in your prompt 

```
Starting migrations...
======================
> Network name:    'develop'
> Network id:      4447
> Block gas limit: 6721975

1_initial_migration.js
======================

   Deploying 'Migrations'
   ----------------------
   > transaction hash:    0x3fd222279dad48583a3320decd0a2d12e82e728ba9a0f19bdaaff98c72a030a2
   > Blocks: 0            Seconds: 0
   > contract address:    0xa0AdaB6E829C818d50c75F17CFCc2e15bfd55a63
   > account:             0x627306090abab3a6e1400e9345bc60c78a8bef57
   > balance:             99.99445076
   > gas used:            277462
   > gas price:           20 gwei
   > value sent:          0 ETH
   > total cost:          0.00554924 ETH

   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:          0.00554924 ETH

2_deploy_contracts.js
=====================

   Deploying 'ConvertLib'
   ----------------------
   > transaction hash:    0x97e8168f1c05fc40dd8ffc529b9a2bf45cc7c55b07b6b9a5a22173235ee247b6
   > Blocks: 0            Seconds: 0
   > contract address:    0xfb39FeaeF3ac3fd46e2123768e559BCe6bD638d6
   > account:             0x627306090abab3a6e1400e9345bc60c78a8bef57
   > balance:             99.9914458
   > gas used:            108240
   > gas price:           20 gwei
   > value sent:          0 ETH
   > total cost:          0.0021648 ETH

   Linking
   -------
   * Contract: MetaCoin <--> Library: ConvertLib (at address: 0xfb39FeaeF3ac3fd46e2123768e559BCe6bD638d6)

   Deploying 'MetaCoin'
   --------------------
   > transaction hash:    0xee4994097c10e7314cc83adf899d67f51f22e08b920e95b6d3f75c5eb498bde4
   > Blocks: 0            Seconds: 0
   > contract address:    0x6891Ac4E2EF3dA9bc88C96fEDbC9eA4d6D88F768
   > account:             0x627306090abab3a6e1400e9345bc60c78a8bef57
   > balance:             99.98449716
   > gas used:            347432
   > gas price:           20 gwei
   > value sent:          0 ETH
   > total cost:          0.00694864 ETH

   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:          0.00911344 ETH

Summary
=======
> Total deployments:   3
> Final cost:          0.01466268 ETH
```

This shows the transaction IDs and addresses of your deployed contracts. It also includes a cost summary and real-time status updates.

Now that we have our blockchain set up with the smart contracts migrated, we will do some interaction with it.

Begin by establishing both the deployed MetaCoin contract instance and the accounts created by either Truffle's built-in blockchain:

```truffle(development)> let instance = await MetaCoin.deployed()
truffle(development)> let accounts = await web3.eth.getAccounts()
```

We can then check the metacoin balance of the account that deployed the contract. To better understande, when we deployed the contract the blockchain used our first account (here will be refered as `account[0]`) so this account will have a stating balance of Metacoin, since our contract set this to the owner of the contract.

Use the command below:

```truffle(development)> let balance = await instance.getBalance(accounts[0])
truffle(development)> balance.toNumber()
```

We will see a result like 100000 because it's the starting balance that our contract is configured to set to the address that call the create function.

See how much ether that balance is worth (and note that the contract defines a metacoin to be worth 2 ether). In here we call the function that is in the ConvertLib.sol that converts our MetaCoin in a value equivalent in ether.

```
truffle(development)> let ether = await instance.getBalanceInEth(accounts[0])
truffle(development)> ether.toNumber()
```

We can now send some MetaCoin from the account that created the contract to a second account, with the following command: 

```truffle(development)> instance.sendCoin(accounts[1], 500)```

We wil have transfered 500 MetaCoins from `account[0]` to `account[1]`. To check this, use the command below:

```truffle(development)> let received = await instance.getBalance(accounts[1])
truffle(development)> received.toNumber()
```

You will see a result as 500.

We can also check the balance of the `account[0]` from where was sent the transaction to the `account[1]`, with the command below:

```truffle(development)> let newBalance = await instance.getBalance(accounts[0])
truffle(development)> newBalance.toNumber()
```

That's it!

This was a simple project with a creation of a coin and demonstration of how to set up a local blockchain and interact with it, using the truffle development console.

All references to the quickstart of [Truffle](https://trufflesuite.com/docs/truffle/quickstart/);



