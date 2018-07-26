# How to Setup an Ethereum Classic Node | macOS

< etc node & apple icon >

< input summary >

# Prerequisites

*Double check project websites for latest installation instructions*

#### Homebrew

[Homebrew](https://brew.sh/) - package manager for macOS

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
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
xcode-select --install
```

# Install

Install Classic Geth using Homebrew
```
brew install ethereumproject/classic/geth
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
