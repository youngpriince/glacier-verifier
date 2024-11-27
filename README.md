# Glacier-Verifier

## Hardware Requirements
![image](https://github.com/user-attachments/assets/eb109899-3204-4356-b7ea-79a595b27273)

## Install Docker
```console
# Update & Install Packages
sudo apt update & sudo apt upgrade -y
sudo apt install ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev curl git wget make jq build-essential pkg-config lsb-release libssl-dev libreadline-dev libffi-dev gcc screen unzip lz4 -y

# Install Docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
docker version

# Install Docker-Compose
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)

curl -L "https://github.com/docker/compose/releases/download/"$VER"/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose
docker-compose --version

# Docker Permission to user
sudo groupadd docker
sudo usermod -aG docker $USER
```
## Bridge tBNB to opBNB
* Claim tBNB tokens on BNB [here](https://www.bnbchain.org/en/testnet-faucet)
* Bridge tBNB from BNB to opBNB [here](https://opbnb-testnet-bridge.bnbchain.org/deposit)

## Run the node
```console
# change $YOUR_PRIVATE_KEY to your private key
docker run -d -e PRIVATE_KEY=$YOUR_PRIVATE_KEY --name glacier-verifier docker.io/glaciernetwork/glacier-verifier:v0.0.2
```
## Note
* You'll get a non-transferable NFT once your node goes live. It will take some minutes before you receive the NFT
* You can scan your [address](https://testnet.opbnbscan.com) to check if you've received the NFT
* You can check the status of the node [here](https://testnet.nodes.glacier.io/status)
