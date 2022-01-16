#Install the Solana Tool Suite
sh -c "$(curl -sSfL https://release.solana.com/v1.9.4/install)"
sudo $(command -v solana-sys-tuner) --user $(whoami) > sys-tuner.log 2>&1 &
#SET Solana to DEVNET or TEST NET 
solana config set --url https://api.devnet.solana.com
solana config set --url https://api.testnet.solana.com
#Generate identity
solana-keygen new -o ~/environment/identity-keypair.json
solana config set --keypair ~/environment/identity-keypair.json 
#get some fund AIRDROP 
solana balance 
#Install SPL TOKEN 
# install rust and cargo 
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
sudo yum install rust cargo
# install spl-token-cli
sudo cargo install spl-token-cli
