# 0G-VALIDATOR-NODE_GUIDE
## Hardware Requirement
|Field|Value|
|:----|:----|
|Memory| 64 gb|
|Cpu|8 cores|
|Disk| 1 Tb NVME SSD|
|Bandwdith|100 mbps|

![0G-bg-2](https://github.com/user-attachments/assets/31bc7ec4-0330-49e3-a42c-eae4e20ea262)


# Validator node
## Install via CLI
```bash
git clone -b v0.2.3 https://github.com/0glabs/0g-chain.git
./0g-chain/networks/testnet/install.sh
source ~/.profile
```

**Set Chain ID**
```bash
0gchaind config chain-id zgtendermint_16600-2
```

## Initialize Node
```bash
0gchaind init <your_validator_name> --chain-id zgtendermint_16600-2
```

## Download th Genesis file and add seeds
```bash
sudo apt install -y unzip wget
rm ~/.0gchain/config/genesis.json
wget -P ~/.0gchain/config https://github.com/0glabs/0g-chain/releases/download/v0.2.3/genesis.json
0gchaind validate-genesis
```

**Add Seed Nodes**

to $HOME/.0gchain/config/config.toml:
```bash
[p2p]

# ...

# Comma separated list of seed nodes to connect to
seeds = "<node-id>@<ip>:<p2p port>"
```

## Start Testnet
```bash
0gchaind start
```
