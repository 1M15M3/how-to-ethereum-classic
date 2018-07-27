# How to Setup an Ethereum Classic Node | macOS

![etcnode icon](https://scontent-ort2-2.xx.fbcdn.net/v/t1.0-9/37861558_253984231873696_3855588271853666304_n.png?_nc_cat=0&oh=dd32597e88b8ee46b36c7cf59c33e790&oe=5BCE499A)

< input summary >

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

This example shows the local node has downloaded and synced blocks `#151305 of  #6031258`. Simply allow the node to sync. This process can take hours. When the local node has reach the current block height, it will continue to import new blocks.

Closing geth will stop the local node and starting the node will continue to sync where it left off.

# Commands & Flags

While geth is running, open a new terminal and view list of commands and flags.

`$ geth -h`, `$ geth help`, `$ geth -help`

```
$ geth help
NAME:
   geth - the go-ethereum command line interface

USAGE:
   geth [options] <command> [command options] [arguments...]

VERSION:
   v5.5.0-382aa8f

COMMANDS AND FLAGS:

ETHEREUM
------------------------------------------------------------------------

    import					Import a blockchain file
    export					Export blockchain into file
    dump-chain-config, dumpchainconfig		Dump current chain configuration to JSON file [REQUIRED argument: filepath.json]
    dump					Dump a specific block from storage
    rollback, roll-back, set-head, sethead	Set current head for blockchain, purging antecedent blocks
    recover					Attempt blockchain data recovery in case of data corruption
    reset					Reset (remove) the chain database

  --data-dir, --datadir "/Users/stev/Library/EthereumClassic"	Data directory for the databases and keystore
  --chain value							Chain identifier (default='mainnet', test='morden') or path to JSON chain configuration file (eg './path/to/chain.json'). (default: "mainnet")
  --network-id value, --networkid value				Network identifier (integer: 1=Homestead, 2=Morden) (default: 1)
  --dev								Developer mode: pre-configured private network with several debugging flags
  --identity value, --name value				Custom node name
  --fast							Enable fast syncing through state downloads
  --cache value							Megabytes of memory allocated to internal caching (min 16MB / database forced) (default: 1024)
  --light-kdf, --lightkdf					Reduce key-derivation RAM & CPU usage at some expense of KDF strength
  --sputnikvm							Use SputnikVM Ethereum Virtual Machine implementation
  --blockchain-version value, --blockchainversion value		Blockchain version (integer) (default: 3)

ACCOUNT
------------------------------------------------------------------------

    account	Manage accounts

	list	Print account addresses
	new	Create a new account
	update	Update an existing account
	import	Import a private key into a new account
	index	Build persistent account index

    wallet	Ethereum presale wallet

	import	import ethereum presale wallet

    atxi-build	Generate index for transactions by address

  --keystore 				Directory path for the keystore
  --unlock value			Comma separated list of accounts to unlock
  --password value			Password file to use for non-inteactive password input
  --index-accounts, --indexaccounts	Enable key-value db store for indexing large amounts of key files
  --atxi, --add-tx-index		Toggle indexes for transactions by address. Pre-existing chaindata can be indexed with command 'atxi-build'
  --atxi.autobuild, --atxi.auto-build	Begins automatic concurrent indexes building process that runs alongside a normally running geth.

API AND CONSOLE
------------------------------------------------------------------------

    console	Geth Console: interactive JavaScript environment
    attach	Geth Console: interactive JavaScript environment (connect to node)
    js		Executes the given JavaScript files in the Geth JavaScript VM
    api		Run any API command

  --rpc							Enable the HTTP-RPC server
  --rpc-addr value, --rpcaddr value			HTTP-RPC server listening interface (default: "localhost")
  --rpc-port value, --rpcport value			HTTP-RPC server listening port (default: 8545)
  --rpc-api value, --rpcapi value			API's offered over the HTTP-RPC interface (default: "eth,net,web3")
  --ws							Enable the WS-RPC server
  --ws-addr value, --wsaddr value			WS-RPC server listening interface (default: "localhost")
  --ws-port value, --wsport value			WS-RPC server listening port (default: 8546)
  --ws-api value, --wsapi value				API's offered over the WS-RPC interface (default: "eth,net,web3")
  --ws-origins value, --wsorigins value			Origins from which to accept websockets requests
  --ipc-disable, --ipcdisable				Disable the IPC-RPC server
  --ipc-api value, --ipcapi value			API's offered over the IPC-RPC interface (default: "admin,debug,eth,miner,net,personal,shh,txpool,web3,geth")
  --ipc-path, --ipcpath "geth.ipc"			Filename for IPC socket/pipe within the datadir (explicit paths escape it)
  --rpc-cors-domain value, --rpccorsdomain value	Comma separated list of domains from which to accept cross origin requests (browser enforced)
  --js-path loadScript, --jspath loadScript		JavaScript root path for loadScript and document root for `admin.httpGet` (default: ".")
  --exec value						Execute JavaScript statement (only in combination with console/attach)
  --preload value					Comma separated list of JavaScript files to preload into the console

NETWORKING
------------------------------------------------------------------------
  --bootnodes value				Comma separated enode URLs for P2P discovery bootstrap
  --port value					Network listening port (default: 30303)
  --max-peers value, --maxpeers value		Maximum number of network peers (network disabled if set to 0) (default: 25)
  --max-pend-peers value, --maxpendpeers value	Maximum number of pending connection attempts (defaults used if set to 0) (default: 0)
  --nat value					NAT port mapping mechanism (any|none|upnp|pmp|extip:<IP>) (default: "any")
  --no-discover, --nodiscover			Disables the peer discovery mechanism (manual peer addition)
  --nodekey value				P2P node key file
  --nodekey-hex value, --nodekeyhex value	P2P node key as hex (for testing)

MINER
------------------------------------------------------------------------

    make-dag, makedag	Generate ethash dag (for testing)

  --mine						Enable mining
  --miner-threads value, --minerthreads value		Number of CPU threads to use for mining (default: 8)
  --miner-gpus value, --minergpus value			List of GPUs to use for mining (e.g. '0,1' will use the first two GPUs found)
  --auto-dag, --autodag					Enable automatic DAG pregeneration
  --etherbase value					Public address for block mining rewards (default = first account created) (default: "0")
  --target-gas-limit value, --targetgaslimit value	Target gas limit sets the artificial target gas floor for the blocks to mine (default: "4712388")
  --gas-price value, --gasprice value			Minimal gas price to accept for mining a transactions (default: "20000000000")
  --extra-data value, --extradata value			Freeform header field set by the miner

GAS PRICE ORACLE
------------------------------------------------------------------------
  --gpo-min value, --gpomin value		Minimum suggested gas price (default: "20000000000")
  --gpo-max value, --gpomax value		Maximum suggested gas price (default: "500000000000")
  --gpo-full value, --gpofull value		Full block threshold for gas price calculation (%) (default: 80)
  --gpo-base-down value, --gpobasedown value	Suggested gas price base step down ratio (1/1000) (default: 10)
  --gpo-base-up value, --gpobaseup value	Suggested gas price base step up ratio (1/1000) (default: 100)
  --gpo-base-cf value, --gpobasecf value	Suggested gas price base correction factor (%) (default: 110)

LOGGING AND DEBUGGING
------------------------------------------------------------------------

    version		Print ethereum version numbers
    status		Display the status of the current node
    monitor		Geth Monitor: node metrics monitoring and visualization
    mdoc		Generate mlog documentation
    gpu-info, gpuinfo	GPU info
    gpu-bench, gpubench	Benchmark GPU

  --verbosity value							Logging verbosity: 0=silent, 1=error, 2=warn, 3=info, 4=core, 5=debug, 6=detail (default: 5)
  --vmodule value							Per-module verbosity: comma-separated list of <pattern>=<level> (e.g. eth/*=6,p2p=5)
  --log-dir value, --logdir value					Directory in which to write log files (default: "/Users/stev/Library/EthereumClassic/<chain>/log")
  --log-max-size value, --log-maxsize value				Maximum size of a single log file (in bytes) (default: "30M")
  --log-min-size value, --log-minsize value				Minimum size of a log file, to be considered for log-rotation (in bytes) (default: "0")
  --log-total-max-size value, --log-totalmaxsize value			Maximum total size of all (current and archived) log files (in bytes) (default: "0")
  --log-rotation-interval value						Log rotation interval, one of values: never, hourly, daily, weekly, monthly (default: "hourly")
  --log-max-age value, --log-maxage value				Maximum age of the oldest log file, valid time units: h, d, w (hours, days, weeks) (default: "0")
  --log-compress, --log-gzip						Enable/disable GZIP compression of archived log files (enabled by default)
  --log-status value							Configure interval-based status logs: comma-separated list of <pattern>=<interval>. Use 'off' or '0' to disable. (default: "sync=60s")
  --display value							Display verbosity: 0=silent, 1=basics, 2=status, 3=status+events (default: 3)
  --display-fmt value							Display format (experimental). Current possible values are [basic|green|dash|gitlike]. (default: "basic")
  --neckbeard								Use verbose->stderr defaults for logging (verbosity=5,log-status='sync=60')
  --mlog value								Set machine-readable log format: [plain|kv|json|off] (default: "off")
  --mlog-dir "/Users/stev/Library/EthereumClassic/mainnet/mlogs"	Directory in which to write machine log files
  --mlog-components value						Set machine-readable logging components, comma-separated.
									Use a '!'-prefix to disabled listed components instead. (default: "blockchain,txpool,downloader,fetcher,discover,server,state,headerchain,miner,client,wire")
  --backtrace value							Request a stack trace at a specific logging statement (e.g. "block.go:271") (default: :0)
  --metrics value							Enables metrics reporting. When the value is a path, either relative or absolute, then a log is written to the respective file.
  --fake-pow, --fakepow							Disables proof-of-work verification

EXPERIMENTAL
------------------------------------------------------------------------
  --shh			Enable Whisper
  --natspec		Enable NatSpec confirmation notice
  --display value	Display verbosity: 0=silent, 1=basics, 2=status, 3=status+events (default: 3)
  --display-fmt value	Display format (experimental). Current possible values are [basic|green|dash|gitlike]. (default: "basic")
  --neckbeard		Use verbose->stderr defaults for logging (verbosity=5,log-status='sync=60')

LEGACY
------------------------------------------------------------------------

    upgrade-db, upgradedb	Upgrade chainblock database

  --testnet		[Use: --chain=morden] Morden network: pre-configured test network with modified starting nonces (replay protection)
  --oppose-dao-fork	Use classic blockchain (always set, flag is unused and exists for compatibility only)

MISCELLANEOUS
------------------------------------------------------------------------
  --solc value				Solidity compiler command to be used (default: "solc")
  --pprof value				Enable runtime profiling with web interface (default: 0)
  --pprof-interval value		Set interval in seconds for runtime profiling (default: 5)
  --doc-root, --docroot "/Users/stev"	Document Root for HTTPClient file scheme
  --help, -h				show help
```
