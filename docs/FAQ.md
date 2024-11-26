# Frequently Asked Questions

### How does Initial Block Download (IBD) work?

Libbitcoin is designed to perform as high performance IBD as possible. This means that it will fully utilize peer connections and hardware resources (CPU, RAM).

IBD is done in the following way:
Libbitcoin connects to 100 peers and will request and validate block headers. Once it reaches the tip of the (strongest) header chain it will start downloading blocks from the peers. This is done in parrallel across the peers (the blocks don't have to be downloaded in order).

Downloaded blocks will have some basic consensus checks that don't require previous blocks: block is not empty (not to be confused with blocks that contain no transactions), is not oversized, first transaction is coinbase, only 1 coinbase transaction, related transaction(s) are in chronological order, no double-spends (in the block), merkle root is valid, is not overweight, coinbase script is valid, hash limit is not exceeded and that the witness commitment is valid.



### Does Libbitcoin support Taproot?

No, Taproot is currently not supported.
This is on the roadmap.
