# Frequently Asked Questions

### Does Libbitcoin support Taproot?

No, Taproot is currently not supported.
This is on the roadmap.

### Which BIP's are supported?

BIP-9, BIP-16\*, BIP-21, BIP-30\*, BIP-31, BIP-32, BIP-34\*, BIP-35, BIP-38, BIP-39, BIP-42\*, BIP-61, BIP-65\*, BIP-66\*, BIP-68\*, BIP-90\*, BIP-112\*, BIP-113\*, BIP-130, BIP-133, BIP-141\*, BIP-143\*, BIP-144, BIP-147\*, BIP-152, BIP-157, BIP-341\*, BIP-342\*.

*soft fork, enabled by default

### Does Libbitcoin support pruning?

No, Libbitcoin does not allow to prune the chain.

The two main reason are:

- If everyone would prune the chain, new nodes would not be able to bootstrap.
- Disk space is cheap and becoming cheaper every year. As the chain growth is lineair (fixed size) and hardware growth is exponential (Moore's law) disk space is even less of a worry each year.
