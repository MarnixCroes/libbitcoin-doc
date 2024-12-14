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
