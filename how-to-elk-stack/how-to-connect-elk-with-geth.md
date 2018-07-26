# How to Connect ELK Stack with Geth

< input banner or preview image >
< input summary >

# Prerequisites

#### Classic Geth

You should have a local node.

< link to tutorial to setup node >

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

#### ELK Stack

[Elastic's](https://www.elastic.co/) (Filebeat) -
**E**lasticsearch
**L**ogstash
**K**ibana (ELK)

![**](https://img.etsystatic.com/il/782712/1452353281/il_570xN.1452353281_7ter.jpg?version=0)

Install ELK Stack in terminal.

```
$ brew install filebeat logstash elasticsearch kibana
```

Terminal 1:

```
$ geth  --mlog=json
```

returned:

```
$ geth --mlog=json
2018-07-26 15:31:08 Geth Classic version: v5.5.0-382aa8f
2018-07-26 15:31:08 Blockchain: Ethereum Classic Mainnet
2018-07-26 15:31:08 Chain database: /Users/stev/Library/EthereumClassic/mainnet/chaindata
2018-07-26 15:31:08 Blockchain upgrades configured: 6
2018-07-26 15:31:08  1150000 Homestead
2018-07-26 15:31:08  1920000 The DAO Hard Fork (0x94365e3a8c0b35089c1d1195081fe7489b528a84b22199c916180db8b28ade7f)
2018-07-26 15:31:08  2500000 GasReprice
2018-07-26 15:31:08  3000000 Diehard
2018-07-26 15:31:08  5000000 Gotham
2018-07-26 15:31:08  5900000 Defuse Difficulty Bomb
2018-07-26 15:31:08 Using 10 configured bootnodes
2018-07-26 15:31:08 Use Sputnik EVM: false
2018-07-26 15:31:08 No etherbase set and no accounts found as default
2018-07-26 15:31:08 Allotted 1024MB cache and 1024 file handles to /Users/stev/Library/EthereumClassic/mainnet/chaindata
2018-07-26 15:31:09 Allotted 16MB cache and 16 file handles to /Users/stev/Library/EthereumClassic/mainnet/dapp
2018-07-26 15:31:09 Protocol Versions: [63 62], Network Id: 1, Chain Id: 61
2018-07-26 15:31:10 Genesis block: 0xd4e56740f876aef8c010b86a40d5f56745a118d0906a34e69aec8c0db1cb8fa3 (mainnet)
2018-07-26 15:31:10 Local head header:     #1726362 [0x8a49c8…] TD=28611031196284468246
2018-07-26 15:31:10 Local head full block: #1726362 [0x8a49c8…] TD=28611031196284468246
2018-07-26 15:31:10 Local head fast block: #1726362 [0x8a49c8…] TD=28611031196284468246
2018-07-26 15:31:10 Starting server...
2018-07-26 15:31:10 UDP listening. Client enode: enode://ecd2ce8dfb150d57ff3c4481bd33f37f629d5c4177a2b4f16dd3b0d0e8668784044a7c208ba4f07f405013420e8b4a5e93c39ae540d123874a89ad12cab51508@[::]:30303
2018-07-26 15:31:10 IPC endpoint opened: /Users/stev/Library/EthereumClassic/mainnet/geth.ipc
2018-07-26 15:31:10 Debug log config: verbosity=5 log-dir=/Users/stev/Library/EthereumClassic/mainnet/log vmodule=*
2018-07-26 15:31:10 Display log config: display=3 status=sync=1m0s
2018-07-26 15:31:10 Machine log config: mlog=json mlog-dir=/Users/stev/Library/EthereumClassic/mainnet/mlogs 2018-07-26 15:32:10 Sync      #1726362              8a49c8f1     0/   0/ 0 blk/txs/mgas sec  2/25 peers
2018-07-26 15:33:10 Sync      #1726378 of  #6035300 957fe26f     0/   2/ 0 blk/txs/mgas sec  4/25 peers

// continues to sync
```


---

I create a config-files folder to contain my config files...

/config-files/filebeat.geth.mlog.json.yml

/config-files/ls-pipeline-json.config

Terminal 2:

Turn file beat on. Pointing to .yml config file.


```
filebeat -e -path.config=. -c /usr/local/etc/filebeat/filebeat.geth.mlog.json.yml -d "publish"
```
```
filebeat -e -path.config=. -c /usr/local/Cellar/filebeat/6.2.4/.bottle/etc/filebeat/filebeat.geth.mlog.json.yml -d "publish"
```







logstash -f /Users/stev/Documents/GitHub/how-to-ethereum-classic/how-to-elk-stack/config-files/ls-pipeline-json.conf --config.reload.automatic
