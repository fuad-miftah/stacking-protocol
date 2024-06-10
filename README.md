# Chromia Staking Protocol

**Name**: Fuad Miftah

**Email**: fuadmiftah9@gmail.com

## Project Description
This project implements a staking protocol using Chromia Rell and the FT4 library. Users can stake FT4 tokens, earn a 10% annual yield, and unstake tokens with a two-week notice period. Unfortunately, I couldn't complete the frontend integration due to difficulties in registering accounts using EVM and the FT4 module.

## How It Works
1. **FT4 Token Creation**: An FT4 token is created for the staking protocol.
2. **Admin Account**: An admin account is created when the program first runs. Users send assets to this account to buy NFTs.
3. **User Account**: Users create accounts and are assigned 1000 CHR by default. They can then buy NFTs and stake them.
4. **Staking**: Users stake FT4 tokens and start earning a 10% annual yield.
5. **Yield Calculation**: Yield is calculated using simple interest: `Principal × Rate × Time`.
6. **Claim Yield**: Users can claim their accumulated yield at any time.
7. **Unstaking**: Users can initiate an unstake request, which can be completed after a two-week notice period.

## Setup Instructions
1. Clone the repository:
    ```sh
    git clone https://github.com/fuad-miftah/stacking-protocol.git
    ```
2. Navigate to the project directory:
    ```sh
    cd stacking-protocol
    ```
3. Install dependencies:
    ```sh
    chr install
    ```
4. Create account owner for the dapp
   ```sh
     chr keygen --file .chroma/dapp-account
   ```
5. Open chromia.yaml file and add this in the moduleArgs
   ```sh
    stacking_protocol:
        dapp_account_signer: x"pubkey created in step 4"
   ```
7. Run tests:
    ```sh
    chr test
    ```
    - Note: To run the tests successfully, change the entity `unstake_request` in `nft.rell` `process_at` field to `op_context.last_block_time - (60 * 60 * 24 * 14)`.
8. For manual testing:
    ```sh
    chr start
    ```
    - Run tests in another terminal.

## Usage Instructions
1. **Admin Account**: An admin account is created on the first run. Users send assets to buy NFTs.
2. **User Account**: Users create accounts and are assigned 1000 CHR by default. They can then buy NFTs and stake them to earn a 10% annual yield.
3. **Staking Interface**: Although the frontend integration is incomplete, the staking process can be managed through the CLI.

## Known Issues
- **Frontend Integration**: The frontend interface could not be completed due to issues with registering accounts using EVM and the FT4 module.

## Additional Information
- The project uses simple interest for yield calculation.
- Unstake requests are processed after a two-week period.
