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

### Does a different node implementation, like Libbitcoin, have unintentional chain split risk?

Bitcoin is a highly complex system, as a result each update to client software can contain unintentional chain split risk.
In fact, this has happened twice to Bitcoin Core ([BIP 50](https://github.com/bitcoin/bips/blob/master/bip-0050.mediawiki), [BIP 66](https://github.com/bitcoin/bips/blob/master/bip-0066.mediawiki)).

Libbitcoin has not had such an unintentional fork since it's existence and believes that multiple implementations strengthen the network, as in such a case only a subset of the network is affected instead of the whole network being stalled.
