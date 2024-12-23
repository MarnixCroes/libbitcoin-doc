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

### I've heard about the Milk Sad vulnerability, does this mean Libbitcoin is unsafe?

The [Milk Sad vulnerability](https://github.com/libbitcoin/libbitcoin-explorer/wiki/CVE-2023-39910) was about the _bx seed_ command using a weak Pseudo-Random Number Generator (PRNG).

The command was supposed to be used for testing purposes, as randomness from the Operating System should not be considered secure.
The documentation always clearly stated this.
However, some external resources used the command as example for generating seeds without mentioning this.
As a result, money got stolen from these low entropy seeds.

The command has been removed to prevent further misuse.

> This vulnerability never affected Libbitcoin as an full node implementation.
