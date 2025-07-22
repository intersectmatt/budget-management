# Guide: How to compile Treasury Contracts with Intersect configuration

This guide will help compile Intersect's 2025 Budget [Treasury Contracts](https://github.com/SundaeSwap-finance/treasury-contracts) instances.

## Aims

Aiming for the user to be able to verify the configuration and permissions of the script addresses used as part of the Intersect budget treasury withdrawals.

What we want to be able to verify
- the withdrawal address's logic (treasury reserve contract)
- the vendor contract script hash

## Prerequisites

- [Bun](https://bun.sh/)
- [Aikup](https://aiken-lang.org/installation-instructions)

## Steps

### 1. Clone the Treasury Contracts Github Repository

Clone the Sundae Labs treasury contracts repository.

```shell
git clone https://github.com/SundaeSwap-finance/treasury-contracts.git
```

Move into repository path.

```shell
cd treasury-contracts
```

### 2. Verify the build parameters

Before running the `build-intersect.sh` shell script,
lets first verify the parameters/config it uses for `$TREASURY_PARAMS` and `$VENDOR_PARAMS`

Run all aiken tests.

```shell
aiken check
```

This compiles the aiken scripts within `/lib/` including the `/lib/intersect.ak`.

`/lib/intersect.ak` does not contain any smart contract logic rather it is used to compile the chosen parameters and configurations for the Treasury and Vendor contracts.

Key information (which should match [treasury-contracts-config.json](./treasury-contracts-config.json))
- Permissions expressed as `MultisigScript` - defines required signatories for actions
- Expiration/ upperbounds

The scripts finishes by outputting the hex encoding of Treasury, Vendor and Seed UTxO to the users console.
These hex values represent Intersect's configuration of the Treasury Contracts system.

### 3. Compare parameters present within `build-intersect.sh`

Using a text editor look inside `build-intersect.sh`.

If you have VsCode command line installed you can:

```shell
code build-intersect.sh
```

We want to confirm that the values used for
- `$SEED_UTXO`
- `$TREASURY_PARAMS`
- `$VENDOR_PARAMS`

We want these values match produced within [Step 2.](#2-verify-the-build-parameters).

If they match we can continue.

### 4. Run `build-intersect.sh`

Now we can run the build script.

```shell
./build-intersect.sh
```

This output should look like:

```shell
...
File hashes:
  validators/treasury.ak              = b0130d0276ebf5efdfaa5dbc0d38e23e00657ccacc660b0999db0185b1fdee11
  validators/vendor.ak                = cfb359b9c823b993148ec51031591f287398e3ce3d3b81f1b3f87bb7f67cda2c
  validators/oneshot.ak               = 486b661193aa7d84e9e2cd8f284ee5e3b79b89dd458c1cbea0c773260f55bc03

  lib/types.ak                        = 4b5517f4cd9fcd75b545342f43ed610ebe8969b8ade0b7afb08ee6981363f41e
  lib/utilities.ak                    = 4697438429cd21d6cbd0315a26dd3022f2fbd01136a8bb0f3925675124973995
  lib/logic/treasury/disburse.ak      = 036c02aa5c0f287dea4ff9703b09906ff44467a9fbac78671a08b7b89bd2875c
  lib/logic/treasury/fund.ak          = 75d4bd6734e18b207c08e43a89943781d350ba9998868a6808b0e1b218849a3c
  lib/logic/treasury/reorganize.ak    = 5713f10f8f101a21c07cd9245312e5ef21dfdef8dcf9cce515c252227fce93ee
  lib/logic/treasury/sweep.ak         = a6d5282818ae8f8b2b62834afadbd4911fdd24cb4d3219a3404ecebef50112ab
  lib/logic/treasury/withdraw.ak      = a702bb19a814c376a0071ee15bcd4681ceaccaf0563e67745e9078b5e18a55d0
  lib/logic/vendor/adjudicate.ak      = 78ddcc86593503bde90911b5497ff14e3a3347fc2d6ffd8bb5a9b9136f26852f
  lib/logic/vendor/malformed.ak       = 0b03157fb8f01a80f34bb49d57ac74f4bab71ae179a3977c24b459d47bfd7041
  lib/logic/vendor/modify.ak          = 9c58a16ae2fce0aad52e64b03b60c5d78a8f03e5ab9cca3761ea2c64eee735c2
  lib/logic/vendor/sweep.ak           = 57e1a2763c3b497e598d5375814425bc6b68fa74c6619a5a103652963b3d35dc
  lib/logic/vendor/withdraw.ak        = 21d5021638f0e459bd718d6f453c4c6e0141957ca951596d2f5191efee4a3e2c

Compiling instance...

Script Hashes:
-e   Registry Policy ID         = \e[32m 9e65e4ed7d6fd86fc4827d2b45da6d2c601fb920e8bfd794b8ecc619 \e[0m
-e   Treasury Contract          = \e[32m 8583857e4a12ffe1e6f641a1785a0f2f036c565cfbe6ff9db8e5a469 \e[0m
-e   Vendor Contract            = \e[32m 882cbb37779b7f1f3dd2b7643662de1bfc180baf225ef820c3d8feae \e[0m
```

Important information
- Registry Policy ID: `9e65e4ed7d6fd86fc4827d2b45da6d2c601fb920e8bfd794b8ecc619`
- Treasury Contract: `8583857e4a12ffe1e6f641a1785a0f2f036c565cfbe6ff9db8e5a469`
- Vendor Contract: `882cbb37779b7f1f3dd2b7643662de1bfc180baf225ef820c3d8feae`

### 5. Compare these values against what can be seen on-chain

The treasury contract should match the withdrawal address for all Intersect 2025 budget treasury withdrawals.

Using your favorite block or governance explorer, we can see that the withdrawal stake address is:
- `stake17xzc8pt7fgf0lc0x7eq6z7z6puhsxmzktna7dluahrj6g6ghh5qjr`

If we transform this from Bech32 to hex (using [addressInspector](https://cardanoscan.io/addressInspector) or [bech32-buffer](https://slowli.github.io/bech32-buffer/)) we get
- `f18583857e4a12ffe1e6f641a1785a0f2f036c565cfbe6ff9db8e5a469`

where we see `f1` (address head bytes) + `8583857e4a12ffe1e6f641a1785a0f2f036c565cfbe6ff9db8e5a469` (script hash bytes)

The script hash bytes MUST match what was seen from [Step 4.](#4-run-build-intersectsh).
