## Instructions to build NEAR contracts

### Install Rust compiler and the package manager
* [Rustup](https://rustup.rs/): Install Rust compiler
* [cargo](https://crates.io/): Install Rust package manager

### Install wasm32
```bash
$ rustup target add wasm32-unknown-unknown
```

### Build the project
```bash
$ cargo build --target wasm32-unknown-unknown
```
or run the `build.sh` file
```bash
$ chmod +x build.sh
$ ./build.sh
```

### Install near-cli
```bash
$ npm install -g near-cli
```

### Deploy the contract
```bash
$ near login
$ near create-account rmdsnft.sasikiran.testnet --masterAccount $ID
$ near deploy --accountId rmdsnft.sasikiran.testnet --wasmFile res/rmds_nft.wasm
```
You should be able to verify the transaction from the URL of the [output](https://explorer.testnet.near.org/transactions/FcEYGpumLBEZe2BiBj9ADRpx1QSNSjhPPNJJovKe7Z58)

### Initialize the contract
```bash
$ near call rmdsnft.sasikiran.testnet new_default_meta '{"owner_id": "sasikiran.testnet"}' --accountId sasikiran.testnet
```

### View the metadata
```bash
$ near view rmdsnft.sasikiran.testnet nft_metadata
```

### Mint an NFT
```bash
$ near call rmdsnft.sasikiran.testnet nft_mint '{"token_id": "0", "receiver_id": "'$ID'", "token_metadata": { "title": "White flowers", "description": "White flowers photo by Yulia", "media": "https://bafybeigyxcifz2eylcpq2a7fnfm3fc3jr5iuplwulz4erw7v4smbvssbsi.ipfs.nftstorage.link/Yulia.png", "copies": 1}}' --accountId $ID --deposit 0.1
```
You should see a response:
```
Scheduling a call: rmdsnft.sasikiran.testnet.nft_mint({"token_id": "0", "receiver_id": "sasikiran.testnet", "token_metadata": { "title": "White flowers", "description": "White flowers photo by Yulia", "media": "https://bafybeigyxcifz2eylcpq2a7fnfm3fc3jr5iuplwulz4erw7v4smbvssbsi.ipfs.nftstorage.link/Yulia.png", "copies": 1}}) with attached 0.1 NEAR
Doing account.functionCall()
Receipts: 3odCpJYNq33Kbpf7NwvDT3tQvZEurQ5rzcB7RGj2SoGz, Arbsn9L3mvkxJf3wgZvtg69tLf5S1sNvLtNRsmJnmtuZ
	Log [rmdsnft.sasikiran.testnet]: EVENT_JSON:{"standard":"nep171","version":"1.0.0","event":"nft_mint","data":[{"owner_id":"sasikiran.testnet","token_ids":["0"]}]}
Transaction Id 6VcU6Hzc95cPwg1oAB2wYbpE8PMZttu6vJNQnVuZKDz
To see the transaction in the transaction explorer, please open this url in your browser
https://explorer.testnet.near.org/transactions/6VcU6Hzc95cPwg1oAB2wYbpE8PMZttu6vJNQnVuZKDz
{
  token_id: '0',
  owner_id: 'sasikiran.testnet',
  metadata: {
    title: 'White flowers',
    description: 'White flowers photo by Yulia',
    media: 'https://bafybeigyxcifz2eylcpq2a7fnfm3fc3jr5iuplwulz4erw7v4smbvssbsi.ipfs.nftstorage.link/Yulia.png',
    media_hash: null,
    copies: 1,
    issued_at: null,
    expires_at: null,
    starts_at: null,
    updated_at: null,
    extra: null,
    reference: null,
    reference_hash: null
  },
  approved_account_ids: {}
}
```