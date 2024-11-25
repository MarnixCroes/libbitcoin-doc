# Frequently Asked Questions

### How does Initial Block Download (IBD) work?

Libbitcoin is designed to perform as high performance IBD as possible. This means that it will fully utilize peer connections and hardware resources (CPU, RAM).

IBD is done in the following way:
Libbitcoin connects to 100 peers and will request and validate block headers. Once it reaches the tip of the (strongest) header chain it will start downloading blocks from the peers. This is done in parrallel across the peers (the blocks don't have to be downloaded in order).

Downloaded blocks will have some basic checks that don't require previous blocks: block size *(insert rest)*. 
