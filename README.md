# SimpleStorage — Foundry Project

A beginner-friendly Solidity project built with :contentReference[oaicite:0]{index=0}.

This project demonstrates:

- Solidity basic data types
- State variables
- Structs
- Arrays
- Mappings
- Memory vs Storage vs Calldata
- Reading & writing blockchain state
- Deploying contracts with Foundry scripts

---

# Project Structure

```text
.
├── src/
│   └── SimpleStorage.sol
│
├── script/
│   └── DeploySimpleStorage.sol
│
├── test/
│
├── foundry.toml
└── README.md
```

---

# Smart Contract

## `SimpleStorage.sol`

A simple contract that stores and retrieves a favorite number while showcasing common Solidity concepts.

### Features

- Store and update a number
- Retrieve stored value
- Add people with favorite numbers
- Map names to favorite numbers
- Demonstrates:
  - `bool`
  - `uint`
  - `int`
  - `string`
  - `address`
  - `bytes32`
  - arrays
  - structs
  - mappings

---

# Functions

## Store a Number

```solidity
function store(uint256 _favNum) public
```

Updates the stored favorite number.

---

## Retrieve Stored Number

```solidity
function retrieve() public view returns (uint256)
```

Returns the current favorite number.

---

## Add a Person

```solidity
function addPerson(string memory _name, uint256 _favNum) public
```

Adds a person and maps their name to a favorite number.

---

# Deployment Script

## `DeploySimpleStorage.sol`

Deploys the `SimpleStorage` contract using Foundry scripting.

Uses:

- `vm.startBroadcast()`
- `vm.stopBroadcast()`

to send deployment transactions.

---

# Getting Started

## Clone the Repository

```bash
git clone <REPOSITORY_URL>
```

---

## Navigate to the Project Directory

```bash
cd <PROJECT_DIRECTORY>
```

---

## Install Foundry

If Foundry is not installed:

Follow the up to date installation through this [link](https://www.getfoundry.sh/introduction/installation)


---

# Build

Compile the smart contracts.

```bash
forge build
```

---

# Test

Test files are not included yet.

A dedicated test suite using Forge will be added in future updates.

Example command once tests are implemented:

```bash
forge test
```
---

# Format

Format Solidity files.

```bash
forge fmt
```
---

# Start Local Node

Run a local Ethereum development node using Anvil.

```bash
anvil
```
---

# Secure Local Deployment

## 1. Create an Encrypted Keystore

```bash
cast wallet import local-deployer --interactive
```

You will:
- paste your private key once
- create a secure password

The key will be encrypted and stored locally.

---

## 2. Deploy the Contract

```bash
forge script script/DeploySimpleStorage.sol:DeploySimpleStorage \
--rpc-url http://localhost:8545 \
--account local-deployer \
--broadcast
```

Foundry will securely prompt for your password.

---

# After Deployment (Interact with Contract)

Once the contract is deployed, you can interact with it using `cast`.

---

## 1. Save Your Contract Address

After deployment, copy the deployed contract address

---

## 2. Set a New Favorite Number (Transaction)

This sends a transaction to update the state.

```bash
cast send <CONTRACT_ADDRESS> \
"store(uint256)" 42 \
--rpc-url http://localhost:8545 \
--account local-deployer
```

- `store(uint256)` → function being called  
- `42` → new favorite number  
- `--account local-deployer` → your saved wallet  

---

## 3. Read the Stored Value (No Transaction)

This is a read-only call (no gas spent).

```bash
cast call <CONTRACT_ADDRESS> \
"retrieve()(uint256)" \
--rpc-url http://localhost:8545
```

---

## 4. Optional: Check Account Balance

```bash
cast balance <YOUR_ADDRESS> --rpc-url http://localhost:8545
```

---

## 5. Verify Transaction Details (Optional)

You can inspect a transaction hash:

```bash
cast tx <TX_HASH> --rpc-url http://localhost:8545
```

---

# Summary

- `cast send` → writes to blockchain (state change)
- `cast call` → reads from blockchain (no gas)
- `--account [NAME]` → uses your secure wallet


---

# Helpful Commands

## Convert HEX to Decimal

```bash
cast --to-base 0xfd31c dec
```

---

# Concepts Covered

## Data Locations

### Storage
Permanent blockchain data.

### Memory
Temporary and modifiable during execution.

### Calldata
Temporary, read-only function input data.

---

# Tools Used

Foundry, which includes:

- **Forge** → testing framework
- **Cast** → blockchain interaction CLI
- **Anvil** → local Ethereum node
- **Chisel** → Solidity REPL

---

# Documentation

- [Foundry Book](https://book.getfoundry.sh.com)
- [Solidity Docs](https://docs.soliditylang.org.com)

---

# License

MIT