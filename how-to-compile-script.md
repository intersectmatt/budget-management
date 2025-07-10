# Guide: How to compile Treasury Contracts with Intersect configuration

This guide will help compile Intersect's 2025 Budget [Treasury Contracts](https://github.com/SundaeSwap-finance/treasury-contracts) instances.

Aiming to be able to verify the configuration and permissions of the script addresses.

## Prerequisites

- [Bun](https://bun.sh/)

## Steps

### 1. Clone the Treasury Contracts Github Repository

```shell
git clone https://github.com/SundaeSwap-finance/treasury-contracts.git
```

### 2. Navigate to the off-chain directory

```shell
cd ./treasury-contracts/off-chain
```

### 3. Install packages

```shell
bun install
```

### 4. Test that CLI works

```shell
bun run ./cli/cli.js -h
```

### 5. Test that CLI works