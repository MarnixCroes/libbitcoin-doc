# Frequently Asked Questions

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

Taproot is currently not supported.
The Libbitcoin v4 release will include Taproot support.

### What are the dependencies?

Libbitcoin uses as few dependencies as possible:

A minimal libbitcoin build requires boost and libsecp256k1. 
ZeroMQ is needed for client and/or server.
ICU (International Components for Unicode) is an optional dependency which is only required when BIP 38 and BIP 39 are being used with libbitcoin-explorer.

![](/assets/dependenciesgraph.png)

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
However, Libbitcoin can build an Electrum index which can be used to connect a (GUI) wallet, like Electrum.

### Does a different node implementation, like Libbitcoin, have unintentional chain split risk?

Bitcoin is a highly complex system, as a result each update to client software can contain unintentional chain split risk.
In fact, this has happened twice to Bitcoin Core ([BIP 50](https://github.com/bitcoin/bips/blob/master/bip-0050.mediawiki), [BIP 66](https://github.com/bitcoin/bips/blob/master/bip-0066.mediawiki)).

Libbitcoin has not had such an unintentional fork since it's existence and believes that multiple implementations strengthen the network, as in such a case only a subset of the network is affected instead of the whole network being stalled.

### How does a libbitcoin node bootstrap, does it use seed nodes?

By default, a Libbitcoin node will connect to the default DNS names, which point to _libbitcoin.net_ (which currently are offline).

If specified, it will connect to the configured peers, which can be IP addresses or DNS names and port.
The seed nodes and manual nodes can be specified in the config file and/or prepopulated in the address cache file with the same values.
The node won't start unless it has 500 (connect batch size (5) * outbound connections (100)) unique addresses in the cache, either from seeding or otherwise.
Seeding is bypassed if the address cache is sufficiently populated, and the seed nodes are dropped once seeding has completed.

### What build system does Libbitcoin use?

Libbitcoin supports multiple build systems:

- Autotools
- CMake (CMake Lists & CMake presets)
- MSBuild

GCC and Clang are officially supported and tested for the Autotools and CMake builds.

The MSBuild supports Microsoft Visual Studio Code (MSVC) on Linux, macOS and Windows.

### What is the policy of a Libbitcoin node?

The Bitcoin P2P network does not implement consensus rules, therefore Libbitcoin only has minimum fee rules to protect against DoS attacks.

## Can Libbitcoin be used on testnet/regtest?

Yes, Libbitcoin supports both testnet3 and regtest.
Libbitcoin does currently not support testnet4 or signet.

### What are the minimal requirements to run Libbitcoin?

Libbitcoin is offically supported and tested on Ubuntu 24.04, latest macOS and latest Windows.

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
