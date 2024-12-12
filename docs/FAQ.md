# Frequently Asked Questions

### Does Libbitcoin support Taproot?

No, Taproot is currently not supported.
This is on the roadmap.

### What are the dependencies?

Libbitcoin uses as few dependencies as possible:

A minimal libbitcoin build requires boost and libsecp256k1. 
ZeroMQ is needed for client and/or server.
ICU (International Components for Unicode) is required for libbitcoin-explorer.

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

### How does a libbitcoin node bootstrap, does it use seed nodes?

By default, a Libbitcoin node will connect to the default DNS names, which point to _libbitcoin.net_.

If specified, it will connect to the configured peers, which can be IP addresses or DNS names and port.
The seed nodes and manual nodes can be specified in the config file and/or prepopulated in the address cache file with the same values.
The node won't start unless it has 500 (connect batch size (5) * outbound connections (100)) unique addresses in the cache, either from seeding or otherwise.
Seeding is bypassed if the address cache is sufficiently populated, and the seed nodes are dropped once seeding has completed.

