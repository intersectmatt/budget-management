# Treasury Contracts Configuration

This document describes permissions that Intersect will use for it's 2025 Budget instance of the [Treasury Contracts](https://github.com/SundaeSwap-finance/treasury-contracts) system.

This document attempts to replicate the data from [treasury-contracts-config.json](./treasury-contracts-config.json) in a human readable way.

TRSC - Treasury Reserve Smart Contract

PSSC - Project Specific Smart Contract

## Overview

Configuration
- TRSC Expires: August 1st, 2028 (2028-08-01 00:00:00)
- PSSC Expires: February 1st, 2028 (2028-02-01 00:00:00)
- PSSC Maximum milestone date: February 1st, 2028 (2028-02-01 00:00:00)

## Oversight Committee Permission

## Permission Instance Summary

| Operation       | Intersect Admin | Intersect Leadership | Trusted Entities |
|-----------------|-----------------|----------------------|------------------|
| TRSC Fund       | 2 of 3          | 1 of 2               | 3 of 5           |
| TRSC Disperse   | 2 of 3          | ALL (2 of 2)         | 3 of 5           |
| TRSC Sweep      | 1 of 3          | 1 of 2               | Not required     |
| TRSC Reorganize | 2 of 3          | Not required         | 3 of 5           |
| PSSC Pause      | 2 of 3          | 1 of 2               | Not required     |
| PSSC Resume     | 2 of 3          | 1 of 2               | Not required     |
| PSSC Modify     | 2 of 3          | 1 of 2               | 3 of 5           |

### Treasury Reserve Contracts

#### 1. Fund Operation

**Requirements:** ALL of the following groups must approve:

- **Intersect Admin** (2 out of 3 required)
  - Intersect Admin 1 (either of 2 keys)
  - Intersect Admin 2 (either of 2 keys)
  - Intersect Admin 3 (either of 2 keys)

- **Intersect Leadership** (1 out of 2 required)
  - Intersect Leadership 1 (either of 2 keys)
  - Intersect Leadership 2 (either of 2 keys)

- **Trusted Entities** (2 out of 5 required)
  - Cardano Foundation (either of 2 keys)
  - Sundae Labs (either of 2 keys)
  - Xerberus (either of 2 keys)
  - NMKR (either of 2 keys)
  - DQuadrant (either of 2 keys)

- **Note:** This permissions matches PSSC Modify

#### 2. Disperse Operation

**Requirements:** ALL of the following groups must approve:

- **Intersect Admin** (2 out of 3 required)
  - Intersect Admin 1 (either of 2 keys)
  - Intersect Admin 2 (either of 2 keys)
  - Intersect Admin 3 (either of 2 keys)

- **Intersect Leadership** (ALL 2 required)
  - Intersect Leadership 1 (either of 2 keys)
  - Intersect Leadership 2 (either of 2 keys)

- **Trusted Entities** (3 out of 5 required)
  - Cardano Foundation (either of 2 keys)
  - Sundae Labs (either of 2 keys)
  - Xerberus (either of 2 keys)
  - NMKR (either of 2 keys)
  - DQuadrant (either of 2 keys)

#### 3. Sweep Treasury Operation

**Requirements:** ALL of the following groups must approve:

- **Intersect Admin** (1 out of 3 required)
  - Intersect Admin 1 (either of 2 keys)
  - Intersect Admin 2 (either of 2 keys)
  - Intersect Admin 3 (either of 2 keys)

- **Intersect Leadership** (1 out of 2 required)
  - Intersect Leadership 1 (either of 2 keys)
  - Intersect Leadership 2 (either of 2 keys)

- **Note:** Trusted Entity approval is NOT required for sweep treasury

#### 4. Reorganize Operation

**Requirements:** ALL of the following groups must approve:

- **Intersect Admin** (2 out of 3 required)
  - Intersect Admin 1 (either of 2 keys)
  - Intersect Admin 2 (either of 2 keys)
  - Intersect Admin 3 (either of 2 keys)

- **Trusted Entities** (3 out of 5 required)
  - Cardano Foundation (either of 2 keys)
  - Sundae Labs (either of 2 keys)
  - Xerberus (either of 2 keys)
  - NMKR (either of 2 keys)
  - DQuadrant (either of 2 keys)

- **Note:** Intersect Leadership approval is NOT required for reorganization

### Project Specific Smart Contract Permissions

#### 1. Pause Operation

**Requirements:** ALL of the following groups must approve:

- **Intersect Admin** (2 out of 3 required)
  - Intersect Admin 1 (either of 2 keys)
  - Intersect Admin 2 (either of 2 keys)
  - Intersect Admin 3 (either of 2 keys)

- **Intersect Leadership** (1 out of 2 required)
  - Intersect Leadership 1 (either of 2 keys)
  - Intersect Leadership 2 (either of 2 keys)

- **Note:** Trusted Entity approval is NOT required for pause

#### 2. Resume Operation

**Requirements:** ALL of the following groups must approve:

- **Intersect Admin** (2 out of 3 required)
  - Intersect Admin 1 (either of 2 keys)
  - Intersect Admin 2 (either of 2 keys)
  - Intersect Admin 3 (either of 2 keys)

- **Intersect Leadership** (1 out of 2 required)
  - Intersect Leadership 1 (either of 2 keys)
  - Intersect Leadership 2 (either of 2 keys)

- **Note:** Trusted Entity approval is NOT required for pause

#### 3. Modify Operation

**Requirements:** ALL of the following groups must approve:

- **Intersect Admin** (2 out of 3 required)
  - Intersect Admin 1 (either of 2 keys)
  - Intersect Admin 2 (either of 2 keys)
  - Intersect Admin 3 (either of 2 keys)

- **Intersect Leadership** (1 out of 2 required)
  - Intersect Leadership 1 (either of 2 keys)
  - Intersect Leadership 2 (either of 2 keys)

- **Trusted Entities** (2 out of 5 required)
  - Cardano Foundation (either of 2 keys)
  - Sundae Labs (either of 2 keys)
  - Xerberus (either of 2 keys)
  - NMKR (either of 2 keys)
  - DQuadrant (either of 2 keys)

- **Note:** This permissions matches TRSC Fund
