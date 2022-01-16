# Mint A Token in Solana 
- Full documentation is available at https://spl.solana.com
- The following are steps to run Solana node in Cloud9 in AWS https://aws.amazon.com/console/

# Install the Solana Tool Suite

```sh
sh -c "$(curl -sSfL https://release.solana.com/v1.9.4/install)"
sudo $(command -v solana-sys-tuner) --user $(whoami) > sys-tuner.log 2>&1 &
```
## SET Solana Config to devnet or test net so we can use free sol for our experiment  
- solana config set --url https://api.devnet.solana.com
- solana config set --url https://api.testnet.solana.com
## Generate identity
```sh
solana-keygen new -o ~/environment/identity-keypair.json
solana config set --keypair ~/environment/identity-keypair.json 
```
## get some fund AIRDROP 
```sh
solana balance 
```
# Install SPL TOKEN 
### Install rust and cargo 
```sh
sudo amazon-linux-extras install rust1
sudo yum install libudev-devel
```
### Install spl-token-cli
```sh
sudo cargo install spl-token-cli
```
# Now mint the token 
```sh 
mkdir solana-cafe-secrets
cd solana-cafe-secrets/
solana config set --url https://api.devnet.solana.com
solana-keygen new -o identity-key.json 
solana config set --keypair identity-key.json 
solana config get 
solana airdrop 1
spl-token create-token 
spl-token create-account 9PwtrMQ7uLY1SQPYJe8n1rgwtUsurggqjA1XBmq33q1q
spl-token balance 9PwtrMQ7uLY1SQPYJe8n1rgwtUsurggqjA1XBmq33q1q
spl-token mint 9PwtrMQ7uLY1SQPYJe8n1rgwtUsurggqjA1XBmq33q1q 1000000
spl-token balance 9PwtrMQ7uLY1SQPYJe8n1rgwtUsurggqjA1XBmq33q1q
spl-token accounts 
solana airdrop 1
solana balance 
spl-token create-account 9PwtrMQ7uLY1SQPYJe8n1rgwtUsurggqjA1XBmq33q1q
 
#create reciver address
solana address 
spl-token transfer 9PwtrMQ7uLY1SQPYJe8n1rgwtUsurggqjA1XBmq33q1q 50 9sBaRezo6xohe3xnpXSg4vmvsDa2YC2ya3Vk7djnEtFC
```
