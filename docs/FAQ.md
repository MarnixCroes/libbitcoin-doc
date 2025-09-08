# Frequently Asked Questions

### How does Initial Block Download (IBD) work?

> Libbitcoin is designed to perform as high performance IBD as possible. This means that it will fully utilize peer connections and hardware resources (CPU, RAM).

IBD is done in the following way:

Libbitcoin connects to 100 peers and will request and validate block headers from all peers. Once the (strongest) header chain is current (defeault is 1h from tip) and contains the minimum work, it will start downloading blocks from the peers. This is done in parrallel across the peers (the blocks don't have to be downloaded in order). By default this is done in concurrencies of 50000 blocks.

Validation will be done of the downloaded blocks after each concurrency. Meaning that, by default, it will download 50k blocks -> validate the blocks -> download the next 50k blocks -> validate, and so forth until the tip.

The downloaded blocks are considered the _candidate chain_, ready for validation.

Validation means doing the consensus checks of each block, including full validation of the scripts and transactions of the blocks.

As a final phase is the _confirmation phase_.
This does the fully ordered check of the full chain. For example, no double spends across the chain.

### Does Libbitcoin support Taproot?

No, Taproot is currently not supported.
This is on the roadmap.
