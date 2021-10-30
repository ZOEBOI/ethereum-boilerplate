# `ethereum-boilerplate`

> React components and hooks for fast building dApps without running own backend

This boilerplate is built on [react-moralis](https://github.com/MoralisWeb3/react-moralis) and [Moralis](https://moralis.io/). Also has its own context provider for quick access to `chainId` or `ethAddress`

There are many components in this boilerplate that do not require an active web3 provider, they use Moralis Web3 API. Moralis supports the most popular blockchains and their test networks. You can find a list of all available networks in [Moralis Supported Chains](https://docs.moralis.io/moralis-server/web3-sdk/intro#supported-chains)

Please check the [official documentation of Moralis](https://docs.moralis.io/#user) for all the functionalities of Moralis.

![dapp](https://user-images.githubusercontent.com/78314301/139121325-0239399e-bcdc-4ca0-b0ec-a25286774e39.gif)

# ⭐️ `Star us`
If this boilerplate helps you build Ethereum dapps faster - please star this project, every star makes us very happy!

# 🚀 Quick Start

📄 Clone or fork `ethereum-boilerplate`:
```sh
git clone https://github.com/ethereum-boilerplate/ethereum-boilerplate.git
```
💿 Install all dependencies:
```sh
cd ethereum-boilerplate
yarn install 
```
✏ Provide your appId and serverUrl from [Moralis](https://moralis.io/) ([How to start Moralis Server](https://docs.moralis.io/moralis-server/getting-started/create-a-moralis-server)) to `<MoralisProvider>` in `src/index.js`:
```jsx
<MoralisProvider appId={APP_ID} serverUrl={SERVER_URL}>
  <App />
</MoralisProvider>
```
🚴‍♂️ Run your App:
```sh
yarn start
```

# 🧭 Table of contents

- [`ethereum-boilerplate`](#ethereum-boilerplate)
- [🚀 Quick Start](#-quick-start)
- [🧭 Table of contents](#-table-of-contents)
- [🏗 Ethereum Components](#-ethereum-components)
  - [`<AddressInput />`](#addressinput-)
  - [`<Chains />`](#chains-)
  - [`<CoinPrice />`](#coinprice-)
  - [`<ERC20Balance />`](#erc20balance-)
  - [`<ERC20Transfers />`](#erc20transfers-)
  - [`<DEX />`](#dex-)
  - [`<Wallet />`](#wallet-)
  - [`<Blockie />`](#blockie-)
  - [`<NativeBalance />`](#nativebalance-)
  - [`<Contract />`](#contract-)
- [🧰 Ethereum Hooks](#-ethereum-hooks)
  - [`useAPIContract()`](#useapicontract)  
  - [`useWeb3Contract()`](#useweb3contract)  
  - [`useERC20Balance()`](#useerc20balance)
  - [`useERC20Transfers()`](#useerc20transfers)
  - [`useNativeBalance()`](#usenativebalance)
  - [`useNativeTransactions()`](#usenativetransactions)
  - [`useNFTBalance()`](#usenftbalance)
  - [`useNFTTransfers()`](#usenfttransfers)
  - [`useNFTTransfers()`](#usenfttransfers)
  - [`useIPFS()`](#useipfs)
  - [`useChain()`](#usechain)
  - [`useTokenPrice()`](#usetokenprice)
  - [`useInchDex()`](#useinchdex)

# 🏗 Ethereum Components

🛠 The ready for use react-components are located in `src/components`. They are designed to be used anywhere in your dApp. 

> ⚡ Note that many components may get params like `chain`, `address`, `size` and etc.

### `<Address />`

![address](https://user-images.githubusercontent.com/78314301/138753150-aefb426c-9481-4f41-91a3-d4e4fd424b8f.gif)

📨 `<Address />` : Displays an Ethereum address with [Blockie](https://www.npmjs.com/package/react-blockies) avatar. 

**Options**:
- copyable (optional): display icon for copying. 
- avatar (optional): display blockie avatar. 
- size (optional): text size.

```jsx
<Address />
<Address avatar />
<Address avatar copyable />
<Address avatar copyable size="4"  />
```


### `<AddressInput />`

![addressInput](https://user-images.githubusercontent.com/78314301/138753917-53007fa1-b053-4723-8c18-aec9ecfe5479.gif)

📫 `<AddressInput />` : Input for eth address. Displays [Blockie](https://www.npmjs.com/package/react-blockies) avatar for the entered wallet. Helps to validate addresses. After entering 42 characters (wallet length) freezes inout and calls `setValidatedAddress`

**Options**:
- autoFocus (optional): focuses object after rendering the component. 
- placeholder (optional): text to display before entering address.
- onChange (required): your setState hook.

```jsx
const [address, setAddress] = useState();

<AddressInput autoFocus placeholder="Input your Address" onChange={setReceiver} />
```


### `<Chains />`

![chains](https://user-images.githubusercontent.com/78314301/138943009-560c3501-8b83-4643-a6f5-0b8f9ff5ef0a.gif)

⛓ `<Chains />` : Active network switch. Supports Ethereum, Polygon, BSC and Avalacnhe blockchains. Works only with networks that have already been added to Injected Wallet. You can find a guide on how to programmatically add a new network [here](https://docs.moralis.io/moralis-server/web3/web3#addnetwork). Easily customizable, you can add other networks

**Options**:
- props (optional): networks to display. Added by default: polygon, eth, bsc and avalanche

```jsx
<Chains polygon eth bsc avalanche />
```


### `<CoinPrice />`

![price](https://user-images.githubusercontent.com/78314301/138944095-ac5aebb0-0e69-4b9e-83ec-2a29d0404cbd.gif)

💵 `<CoinPrice />` : displays the price of the token specified in the settings. Uses Moralis Web3API (does not require an active web3 provider).

**Options**:
- address (required): Token contract address 
- chain (optional): The network to which the token is deployed. Default: ETH
- image (optional): local path or link to token logo
- size (optional): logo size

```jsx
<CoinPrice address="0x1...3" chain="eth" image="https://img.png" size="40px" />
```

### `<ERC20Balance />`

![image](https://user-images.githubusercontent.com/78314301/138942560-722b03ef-09db-47ce-8b73-7965bae81646.png)

💰 `<ERC20Balance />` : displays the ERC20 balance of an address. Uses Moralis Web3API (does not require an active web3 provider).

**Options**:
- chain (optional): network for displaying balances on. Will use your wallet network if you do not specify `chain` yourself

```jsx
<ERC20Balance chain="polygon" />
```


### `<ERC20Transfers />`

![image](https://user-images.githubusercontent.com/78314301/138941033-127dca78-1424-41ce-94da-ae1b3b865261.png)

💸 `<ERC20Transfers />` : displays the ERC20 transfers of an address. Uses Moralis Web3API (does not require an active web3 provider).

**Options**:
- chain (optional): network for displaying transfers on. Will use your wallet network if you do not specify `chain` yourself

```jsx
<ERC20Transfers chain="polygon" />
```

### `<DEX />` 

![dex2](https://user-images.githubusercontent.com/78314301/139118630-9c98dbcf-73bc-4b47-af09-9f81a1181d0b.gif)

💱 `<InchDex />` : interface for [Moralis 1Inch Plugin](https://moralis.io/plugins/1inch/). This plugin integrates the DeFi / DEX aggregator 1Inch to any project that uses Moralis. There is a 1% transaction fee on each swap.

**Options**:
- chain (optional): network. Available: Ethereum (“eth”), Binance Smart Chain (“bsc”), Polygon (“polygon”)

```jsx
<InchDex chain="eth" />
```


### `<Wallet />`

![wallet](https://user-images.githubusercontent.com/78314301/138942356-f72346dc-14c7-43c5-9ae3-802d219f866f.gif)

💼 `<Wallet />` : example interface for interacting with your wallet. Uses components from the boilerplate:  `<Blockie />`, `<Address />`, `<NativeBalance />`, `<AddressInput />`. Has the functionality to send tokens

```jsx
<Wallet />
```


### `<Blockie />` 


### `<NativeBalance />`

### `<Contract />`

# 🧰 Ethereum Hooks

### `useAPIContract()`

📋 Runs a given function of a contract abi and returns readonly data. Uses Moralis Web3API (does not require an active web3 provider).

**Options**:
- `chain` (optional): The blockchain to get data from. Valid values are listed on the intro page in the Transactions and Balances section. Default value Eth.
- `functionName` (required): The function name
- `address` (required): A smart contract address
- `abi` (required): contract or function ABI(should be provided as an array)

**Example**:
```jsx
const ShowUniswapTotalSupplyLP = () => {
  const { runContractFunction, contractResponse, error, isLoading } = useAPIContract({
    abi: usdcEthPoolAbi,
    address: usdcEthPoolAddress,
    functionName: "totalSupply",
  });

  return (<div>
    {error && <ErrorMessage error={error} />}
    <button onClick={() => runContractFunction()} disabled={isLoading}>Fetch data</button>
    {data && <pre>
      {JSON.stringify(contractResponse),
        null,
        2,
      )}
    </pre>}
  </div>)
}
```

### `useWeb3Contract()`

📋 Runs on-chain functions. Requires active Web3 Provider.

**Options**:
- `chain` (optional): The blockchain to get data from. Valid values are listed on the intro page in the Transactions and Balances section. Default value Eth.
- `functionName` (required): The function name
- `contractAddress` (required): A smart contract address
- `abi` (required): contract or function ABI(should be provided as an array)
- `params` (optional): Parameters needed for your specific function

**Example**:
```jsx
const ShowUniswapObserveValues = () => {
  const { runContractFunction, contractResponse, error, isLoading } = useWeb3Contract({
    abi: usdcEthPoolAbi,
    contractAddress: usdcEthPoolAddress,
    functionName: "observe",
    params: {
      secondsAgos: [0, 10],
    },
  });

  return (<div>
    {error && <ErrorMessage error={error} />}
    <button onClick={() => runContractFunction()} disabled={isLoading}>Fetch data</button>
    {data && <pre>
      {JSON.stringify(contractResponse),
        null,
        2,
      )}
    </pre>}
  </div>)
}
```

### `useERC20Balance()` 

### `useERC20Transfers()` 

### `useNativeBalance()` 

### `useNativeTransactions()` 

Gets the transactions from the current user or address. Returns an object with the number of transactions  and the array of native transactions 

**Options**:
- `chain` (optional): The blockchain to get data from. Valid values are listed on the intro page in the Transactions and Balances section. Default value Eth.
- `address` (optional): A user address (i.e. 0x1a2b3x...). If specified, the user attached to the query is ignored and the address will be used instead.
- `from_date` (optional): The date from where to get the transactions (any format that is accepted by momentjs). Provide the param 'from_block' or 'from_date' If 'from_date' and 'from_block' are provided, 'from_block' will be used.
- `to_date` (optional):  Get the transactions to this date (any format that is accepted by momentjs). Provide the param 'to_block' or 'to_date' If 'to_date' and 'to_block' are provided, 'to_block' will be used.
- `from_block` (optional): The minimum block number from where to get the transactions Provide the param 'from_block' or 'from_date' If 'from_date' and 'from_block' are provided, 'from_block' will be used.
- `to_block` (optional): The maximum block number from where to get the transactions. Provide the param 'to_block' or 'to_date' If 'to_date' and 'to_block' are provided, 'to_block' will be used.
- `offset` (optional): Offset.
- `limit` (optional): Limit.

**Returns** (Array) : native transactions

### `useNFTBalance()` 

### `useNFTTransfers()` 

### `useChain()` 

### `useInchDex()` 

### `useTokenPrice()` 

### `useIPFS()` 
