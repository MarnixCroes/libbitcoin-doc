# Frequently Asked Questions

### Does Libbitcoin support Taproot?

Taproot is currently not supported.
The Libbitcoin v4 release will include Taproot support.

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

### What is the policy of a Libbitcoin node?

The Bitcoin P2P network does not implement consensus rules, therefore Libbitcoin only has minimum fee rules to protect against DoS attacks.

