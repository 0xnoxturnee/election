# E-Voting - DApp Development


Fixed a couple syntax issues from orginal repo.

## Dependencies

Prerequisites; 

- NPM: https://nodejs.org
- Truffle: https://github.com/trufflesuite/truffle
- Ganache: http://truffleframework.com/ganache/
- Metamask: https://metamask.io/

## 1. Prepare tools, test frameworks.


## 2. Install dependencies, write code.


## 3. Starting Ganache.


## 4. Compile & Deploy Election Smart Contract
You must migrate the election smart contract each time your restart ganache.


## 5. Configure Metamask, import from Ganache.


## 6. Run the Front End Application.

`$ npm run dev`
http://localhost:3000

---

## IMPORTANT NOTES

1. Use `web3.eth.getAccounts()` to get accounts now
2. To bootstrap sample truffle project, use command `truffle unbox pet-shop`

---

## Deploy to rinkeby test network

1. Run geth node

```bash
geth --rinkeby --http --http.api personal,eth,net,web3 --allow-insecure-unlock
```

This can take dozens of hours, depending on your machine configuration and internet speed.  
This will cost you close to 100GB or so of hard drive space.

2. Create a new account

```bash
geth --rinkeby account new
```

3. Attach into geth console

```bash
geth --rinkeby attach
```

And you can do many things in geth console

```bash
eth.syncing     #check the syncing status
eth.accounts    #check all accounts
eth.getBalance(eth.accounts[0]) #check account balance
personal.unlockAccount(eth.accounts[0],null,1200)   #unlock a certain accont for 20 minutes
```

4. Acquire eth from https://www.rinkeby.io/#faucet

Here they require that you have to post a twitter or facebook, which is disgusting.

5. Migrate

```bash
truffle migrate --reset --compile-all --network rinkeby
```

6. Verify deployment

```bash
geth --rinkeby attach
```

```bash
var contractAddress = "Your_Contract_Address"
var contractAbi = [Your_ABI_Array] #copy the abi array in build/contracts/Election.json, turn it into one line style
var electionContract = web3.eth.contract(contractAbi)
var electionInstance = electionContract.at(contractAddress)
electionInstance.candidates(1)
electionInstance.vote(1, {from: eth.accounts[0]});
```
