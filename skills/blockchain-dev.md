---
name: blockchain-dev
description: Solidity + Hardhat blockchain development. Use when writing/debugging smart contracts, deploying to local Hardhat chain, integrating Web3 with backend, or troubleshooting on-chain interactions.
---

# Blockchain Development

You are a blockchain developer specializing in Solidity + Hardhat for Ethereum-compatible chains.

## Stack
- **Solidity 0.8.x** — smart contracts
- **Hardhat** — local development network
- **ethers.js v6** — frontend/script interaction
- **Web3j** — Java backend integration

## Smart Contract Best Practices

### Gas Optimization
- Use events instead of on-chain string storage
- Batch operations when possible
- Use `calldata` instead of `memory` for read-only parameters
- Avoid loops over unbounded arrays

### Access Control
```solidity
modifier onlyOwner() {
    require(msg.sender == owner, "Not authorized");
    _;
}
```

### Events
```solidity
event Transaction(
    uint256 indexed txId,
    address indexed from,
    address indexed to,
    uint256 amount,
    uint256 timestamp
);
```

### Error Handling
- Solidity 0.8.x has built-in overflow protection
- Use `require()` with descriptive revert messages
- Custom errors (0.8.4+) save gas over string requires

## Hardhat Commands
```bash
npx hardhat compile        # Compile
npx hardhat node            # Start local chain
npx hardhat test            # Run tests
npx hardhat run scripts/deploy.js --network localhost
```

## Common Issues
| Symptom | Fix |
|---------|-----|
| Nonce too low | Reset Hardhat node |
| Out of gas | Optimize contract, increase gas limit |
| Revert without reason | Add descriptive `require()` messages |
| Bytecode > 24KB | Split contract or use libraries |
| Contract not found | Check deployed address file |
