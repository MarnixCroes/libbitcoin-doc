# Frequently Asked Questions

### How does Initial Block Download (IBD) work?

> Libbitcoin is designed to perform as high performance IBD as possible. This means that it will fully utilize peer connections and hardware resources (CPU, RAM).

IBD is done in the following way:

Libbitcoin connects to 100 peers and will request and validate block headers from all peers. Once the (strongest) header chain is current (defeault is 1h from tip) and contains the minimum work, it will start downloading blocks from the peers. This is done in parrallel across the peers (the blocks don't have to be downloaded in order). By default this is done in concurrencies of 50000 blocks.

Validation will be done of the downloaded blocks after each concurrency. Meaning that, by default, it will download 50k blocks -> validate the blocks -> download the next 50k blocks -> validate, and so forth until the tip.

Validation means doing the consensus checks of each block, including full validation of the scripts and transactions of the blocks.

As a final phase is the _confirmation phase_.
This does the fully ordered check of the full chain. For example, no double spends across the chain.

### How is Libbitcoin different from Bitcoin Core?

_Libbitcoin_ and _Bitcoin Core_ are two different implementations of the Bitcoin protocol.

The main architectural differences are:

- *Libbitcoin is a developer toolkit, with a modular design*

Libbitcoin has several separate libraries that can be used independently, meaning that things like node, network and database are separate from each other.
Whereas Bitcoin Core has a monolithic architecture where everything is in the same codebase and interconnected.

- *Libbitcoin focuses on performance and scaling of the software*

Libbitcoin has an asynchronous design that allows for efficient event-driven actions and parallelism. 
Better hardware and bandwidth results in better node performance (like faster IBD). 
This makes the software scalable and future proof (as hardware specs and bandwidth keep increasing (Moore's Law)).

- *No UTXO set*

Libbitcoin does not store a UTXO set (like Bitcoin Core) but stores the full indexed chain.

- *Libbitcoin keeps it minimal*

Things like new wallet features and GUI's are not being worked on, they can be built on top of or used with Libbitcoin but are not part of Libbitcoin itself.

### Does Libbitcoin support Taproot?

Yes, Taproot is supported since Libbitcoin version 4.

> Wallet functionalities such as P2TR address generation and transaction building are not yet supported.

### How to run a Libbitcoin node?

> To run a Libbitcoin node, a Libbitcoin Server should be run.
However, as the Server is still a work in progress, solely the node can be run for testing purposes.

Install the required dependencies: boost & libsecp256k1.

Build the required libraries: libbitcoin-system, libbitcoin-network, libbitcoin-database & libbitcoin-node.

Then run the resulting `bn` executable.

See step-by-step instructions [here](/guides/RunningLibbitcoin/RunNode/).

### What are the dependencies?

Libbitcoin uses as few dependencies as possible:

A minimal libbitcoin build requires boost and libsecp256k1. 
ZeroMQ is needed for client and/or server.
ICU (International Components for Unicode) is an optional dependency which is only required when BIP 38 and BIP 39 are being used with libbitcoin-explorer.

![](/assets/dependenciesgraph.png)

### Which BIP's are supported?

BIP-9, BIP-16\*, BIP-21, BIP-30\*, BIP-31, BIP-32, BIP-34\*, BIP-35, BIP-38, BIP-39, BIP-42\*, BIP-61, BIP-65\*, BIP-66\*, BIP-68\*, BIP-90\*, BIP-112\*, BIP-113\*, BIP-130, BIP-133, BIP-141\*, BIP-143\*, BIP-144, BIP-147\*, BIP-152, BIP-155, BIP-157, BIP-341\*, BIP-342\*.

*soft fork, enabled by default

### Does Libbitcoin support pruning?

No, Libbitcoin does not allow to prune the chain.

The two main reason are:

- If everyone would prune the chain, new nodes would not be able to bootstrap.
- Disk space is cheap and becoming cheaper every year. As the chain growth is lineair (fixed size) and hardware growth is exponential (Moore's law) disk space is even less of a worry each year.

### Is it possible to mine using Libbitcoin?

Libbitcoin does not currently have a mining interface, although anyone is free to build on top of/using Libbitcoin.

Implementing a mining interface is a future plan.

### Does Libbitcoin have a GUI?

No, Libbitcoin does not have a Graphical User Interface.
However, Libbitcoin can build an Electrum index which can be used to connect a GUI (wallet), like Electrum.

### Does a different node implementation, like Libbitcoin, have unintentional chain split risk?

Bitcoin is a highly complex system, as a result each update to client software can contain unintentional chain split risk.
In fact, this has happened twice to Bitcoin Core ([BIP 50](https://github.com/bitcoin/bips/blob/master/bip-0050.mediawiki), [BIP 66](https://github.com/bitcoin/bips/blob/master/bip-0066.mediawiki)).

Libbitcoin has not had such an unintentional fork since it's existence and believes that multiple implementations strengthen the network, as in such a case only a subset of the network is affected instead of the whole network being stalled.

### How does a libbitcoin node bootstrap, does it use seed nodes?

> Currently libbitcoin uses the same seed nodes as Bitcoin Core.

By default, a Libbitcoin node will connect to the default DNS names, which point to _libbitcoin.net_ (which currently are offline).

If specified, it will connect to the configured peers, which can be IP addresses or DNS names and port.
The seed nodes and manual nodes can be specified in the config file and/or prepopulated in the address cache file with the same values.
The node won't start unless it has 500 (connect batch size (5) * outbound connections (100)) unique addresses in the cache, either from seeding or otherwise.
Seeding is bypassed if the address cache is sufficiently populated, and the seed nodes are dropped once seeding has completed.

### What build system does Libbitcoin use?

Libbitcoin supports multiple build systems:

- Autotools
- CMake (CMake Lists & CMake presets)
- VSCode
- Visual C++ (MSVC) (Windows)

GCC and Clang are officially supported and tested for these build systems.

### What is the transaction relay policy of a Libbitcoin node?

The Bitcoin P2P network does not implement consensus rules, therefore Libbitcoin only has minimum fee rules to protect against DoS attacks.

> Currently, a Libbitcoin node does not relay any transactions. Transaction relay is a WIP.

### How does Libbitcoin work without a UTXO set?

Libbitcoin stores the fully indexed chain.

It is a common misconception that Bitcoin uses a UTXO set.
Bitcoin uses blocks, a UTXO set is an (Bitcoin Core) implementation specific concept.

### Can Libbitcoin be used on testnet/regtest?

Yes, Libbitcoin supports both testnet3 and regtest.
Libbitcoin does currently not support testnet4 or signet.

### What are the minimal requirements to run Libbitcoin?

#### Operating System
Libbitcoin is offically supported and tested on Ubuntu 24.04, latest macOS and latest Windows.

#### Dependencies
- Boost: 1.86.0
- secp256k1: v0.7.0
- ICU: 55.2 (optional dependency)

#### Hardware
It should run on as low as 8 GiB RAM, however Libbitcoin contributors do not spend time and resources on supporting lower level hardware as this hardware will become obsolete in the near future.

32 GiB RAM minimum is recommended.
1 TB disk is required to store the chain.

### How does a Libbitcoin node manage peers?

By default, a Libbitcoin node targets to have 100 outbound connections, and has 0 inbound connections (disabled).

New outbound connections are made in batches of 5 (default), where the first one to complete the handshake gets connected and the others get dropped.

New connection establishments have a time limit of 5 seconds (default), peers that fail to establish a connection within this time are dropped.

Stalled channels are dropped. A channel is considered stalled after 10 seconds (default) of inactivity.

Slow channel(s) are also dropped. A channel is considered slow if the underperformance to the standard deviation is 1.5 (default) or more.

Download rates are measured for each channel to perform standard deviation computation across all of them (can be disabled).

Specified peers (in the config) will be reconnected on drop.

Seed nodes are dropped after completion or time-out.

A peer is immediately dropped if it violates the protocol or exceeds resource limits. Libbitcoin does not use a banning mechanism.

### What are the executables?

There are 3 executables:

- `bs` is the Bitcoin-Server.
- `bx` is the Bitcoin-Explorer.
- `bn` is the Bitcoin-Node.

Note that `bn` is part of Bitcoin-Server, and it's execution is for developer and/or testing purposes.

### How does Libbitcoin handle soft/hard forks?

Any fork, both soft and hard forks, are configuration options.
Users are never forced to accept a fork when upgrading the software.

### Does Libbitcoin have a wallet?

Libbitcoin does not have a wallet.

However, Libbitcoin System and Libbitcoin Explorer do have commands like the generation of private keys, addresses, mnemonics, bitcoin URI encoding etc.

These functionalities in the `libbitcoin-system` library may be used by developers, whereas the commands in Libbitcoin Explorer can be used by end users.

> To use a Libbitcoin node with a wallet, an Electrum index can be used to connect a wallet.

### Does Libbitcoin have a RPC interface?

No, Libbitcoin does not have a RPC interface.

Libbitcoin Server contains a Client Server Interface, using [ZeroMQ](https://zeromq.org/), that enables queries.

### How can I donate to the project?

Currently, the best way is to donate to individual contributors.

Financial contributions are highly welcome and necessary for some of the contributors.

### What database does Libbitcoin use?

Libbitcoin uses a custom memory mapped (mmap) database.

The store is fully write concurrent, asynchronous and lock free.

It allows to use all the cores, meaning that the entire store can remain in memory if sufficient RAM is available.
