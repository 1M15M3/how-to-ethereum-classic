# How to Setup an Ethereum Classic Node | macOS

![etcnode icon](https://scontent-ort2-2.xx.fbcdn.net/v/t1.0-9/37861558_253984231873696_3855588271853666304_n.png?_nc_cat=0&oh=dd32597e88b8ee46b36c7cf59c33e790&oe=5BCE499A)

`Geth` is the command line interface for running a full Ethereum based node in Go. By running a full node, you take part in the network.

**Capabilities of running a full node:**
- mine ether (particularly effective to mine testnet Ether)
- manage accounts and funds
- create contracts and transactions
- explore block history
- and more.

**Why run a full node:**
- third party nodes (light nodes, remote nodes, etc...) are usually reliable, but have high traffic and controlled by a third party. Using a personal node ensures more user control and oversight of performed functions with the network.
-  more independent nodes on the network ensures the security and resiliency of the network.
- more nodes reduce the latency of the network.
- developers can use a personal node for various dApp tasks
- support the blockchain revolution!

# Prerequisites

*Double check project websites for latest installation instructions*

#### Homebrew

[Homebrew](https://brew.sh/) - package manager for macOS

```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
Simply follow through installation in terminal.

Check installation in terminal.

```
$ brew -v
Homebrew 1.7.1
Homebrew/homebrew-core (git revision b87a; last commit 2018-07-25)
```

#### Go lang. and a C compilar (xcode)

Easily install Go Programming Language by downloading a binary distribution at the [Go Lang.](https://golang.org/) website.

Check installation in terminal.

```
$ go version
go version go1.10.3 darwin/amd64
```

Install xcode.

```
$ xcode-select --install
```

# Install

Install Classic Geth using Homebrew
```
$ brew install ethereumproject/classic/geth
```
Example of the output:
```
$ brew install ethereumproject/classic/geth
==> Tapping ethereumproject/classic
Cloning into '/usr/local/Homebrew/Library/Taps/ethereumproject/homebrew-classic'...
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 5 (delta 0), reused 2 (delta 0), pack-reused 0
Unpacking objects: 100% (5/5), done.
Tapped 2 formulae (30 files, 22.6KB).
==> Installing geth from ethereumproject/classic
==> Downloading http://builds.etcdevteam.com/go-ethereum/v5.5.x/geth-classic-osx
######################################################################## 100.0%
🍺  /usr/local/Cellar/geth/5.5.0: 3 files, 40.5MB, built in 4 seconds
```

Check installation in terminal.

```
$ geth version
Geth
Version: v5.5.0-382aa8f
Protocol Versions: [63 62]
Network Id: 1
Go Version: go1.9.3
Go OS: darwin
Go Arch: amd64
Machine ID: fbe5f99f
GOPATH=
GOROOT=/usr/local/Cellar/go/1.9.3/libexec
```

Update Geth if applicable.

Classic Geth is maintained by the Ethereum Classic developer community. You can upgrade geth version by running `brew upgrade geth` in terminal.

# Initialize

Initialize Classic Geth by running `geth` however consider reading on before running geth.

```
$ geth
```

`--fast` Increase performance to sync at the cost of downloading only block state data.

`--cache=VALUE` Further increase performance by adjusting memory (megabytes) allowance of the database. Default is 1024 MB.

```
$ geth --fast --cache=1024
```

Running Classic Geth downloads and syncs the entire Ethereum Classic blockchain. Geth returns the sync status. E.g.:

```
2018-07-25 22:51:36 Sync       #151305 of  #6031258 36529b08   638/ 517/12 blk/txs/mgas sec  8/25 peers
```

This example shows the local node has downloaded and synced blocks `#151305 of  #6031258`. Simply allow the node to sync. This process can take hours. When the local node has reach the current block height, it will continue to import new blocks. Closing Geth will stop the instance of the Ethereum Classic blockchain. Running Geth again, will continue to sync the blockchain from the last instance of the node to the current blockchain and so on.

# Commands & Flags

While geth is running, open a new terminal and view list of commands and flags.

`$ geth -h`, `$ geth help`, `$ geth -help`

# Using Geth - Basics

**Default Data Directory**

`$HOME/Library/EthereumClassic/`

Overview of the file structure

```
$ cd ./Library/EthereumClassic/mainnet/
$ ls
chaindata	geth.ipc	log		nodekey
dapp		keystore	mlogs		nodes
```
`chaindata` - the Ethereum Classic database `keystore` - keystore files for accounts created in geth

## Accounts

**Import Account**

Import an existing ETC account using a keystore file or existing private key. Private keys can be saved in a .txt or .csv file, then pointed to for import.

```
$ geth account import < KEYSTORE FILE OR PRIVATE_KEY.txt >
// Another example, assume "Stev" saved his keystore or private key in Downloads directory
$ geth account import /Users/stev/Downloads/privatekey.txt
```

The account will be imported and a keystore file will be generated at `./Library/EthereumClassic/mainnet/keystore`. Always backup keystore files and private keys incase of the event to recover an account.

**Create Account**

Create a new ETC account.

```
$ geth account new
```

**List Accounts**

```
$ geth account list
```
