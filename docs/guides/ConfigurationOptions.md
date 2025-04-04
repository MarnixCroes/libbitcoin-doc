# Configuration Options

There is one configuration file for the Client stack and one configuration file for the Server stack.

## Libbitcoin Server (node) configuration

As the v4 Server is currently still a WIP and only the node can be run, the Node config file is used here.

A Libbitcoin node has one configuration file, separated in 6 sections: bitcoin, database, forks, log, network, node.
All config options have a comment with description and the default value.

```
# Libbitcoin Node configuration file

[bitcoin]
# The activation time for bip16 in unix time, defaults to 1333238400.
bip16_activation_time = <value>
# The number of blocks considered for bip34 style soft fork activation, defaults to 1000.
bip34_activation_sample = <value>
# The number of new version blocks required for bip34 style soft fork activation, defaults to 750.
bip34_activation_threshold = <value>
# The number of new version blocks required for bip34 style soft fork enforcement, defaults to 950.
bip34_enforcement_threshold = <value>
# The block height to freeze the bip34 softfork for bip90, defaults to 227931.
bip34_freeze = <value>
# The block height to freeze the bip65 softfork for bip90, defaults to 388381.
bip65_freeze = <value>
# The block height to freeze the bip66 softfork for bip90, defaults to 363725.
bip66_freeze = <value>
# The hash:height checkpoint for bip9 bit0 activation, defaults to 000000000000000004a1b34462cb8aeebd5799177f7a29cf28f2d1961716b5b5:419328.
bip9_bit0_active_checkpoint = <value>
# The target block period, defaults to 600.
block_spacing_seconds = <value>
# The blockchain checkpoints, defaults to the consensus set.
checkpoint = <value>
# The genesis block, defaults to mainnet.
genesis_block = <value>
# The initial block subsidy, defaults to 50.
initial_block_subsidy_bitcoin = <value>
# A block presumed to be valid but not required to be present, defaults to 00000000000000000001a0a448d6cf2546b06801389cc030b2b18c6491266815:804000.
milestone = <value>
# The minimum work for any branch to be considered valid, defaults to 000000000000000000000000000000000000000052b2559353df4117b7348b64.
minimum_work = <value>
# The proof of work limit, defaults to 486604799.
proof_of_work_limit = <value>
# The difficulty retargeting factor, defaults to 4.
retargeting_factor = <value>
# The difficulty retargeting period, defaults to 1209600.
retargeting_interval_seconds = <value>
# The subsidy halving period, defaults to 210000.
subsidy_interval = <value>
# The future timestamp allowance, defaults to 7200.
timestamp_limit_seconds = <value>

[database]
# The number of buckets in the address table head, defaults to '1459791875' (0 disables).
address_buckets = <value>
# The percentage expansion of the address table body, defaults to '5'.
address_rate = <value>
# The minimum allocation of the address table body, defaults to '29390853398'.
address_size = <value>
# The percentage expansion of the candidate table body, defaults to '5'.
candidate_rate = <value>
# The minimum allocation of the candidate table body, defaults to '2523423'.
candidate_size = <value>
# The percentage expansion of the candidate table body, defaults to '5'.
confirmed_rate = <value>
# The minimum allocation of the candidate table body, defaults to '2523423'.
confirmed_size = <value>
# The number of buckets in the header table head, defaults to '524493'.
header_buckets = <value>
# The percentage expansion of the header table body, defaults to '5'.
header_rate = <value>
# The minimum allocation of the header table body, defaults to '20397669'.
header_size = <value>
# The percentage expansion of the input table body, defaults to '5'.
input_rate = <value>
# The minimum allocation of the input table body, defaults to '90116786234'.
input_size = <value>
# The number of buckets in the neutrino table head, defaults to '524493' (0 disables).
neutrino_buckets = <value>
# The percentage expansion of the neutrino table body, defaults to '5'.
neutrino_rate = <value>
# The minimum allocation of the neutrino table body, defaults to '2656071402'.
neutrino_size = <value>
# The percentage expansion of the output table body, defaults to '5'.
output_rate = <value>
# The minimum allocation of the output table body, defaults to '24315563831'.
output_size = <value>
# The blockchain database directory, defaults to 'blockchain'.
path = <value>
# The number of buckets in the point table head, defaults to '546188501'.
point_buckets = <value>
# The percentage expansion of the point table body, defaults to '5'.
point_rate = <value>
# The minimum allocation of the point table body, defaults to '8389074978'.
point_size = <value>
# The percentage expansion of the puts table body, defaults to '5'.
puts_rate = <value>
# The minimum allocation of the puts table body, defaults to '6059682874'.
puts_size = <value>
# The number of buckets in the spend table head, defaults to '1459791875'.
spend_buckets = <value>
# The percentage expansion of the spend table body, defaults to '5'.
spend_rate = <value>
# The minimum allocation of the spend table body, defaults to '15364630530'.
spend_size = <value>
# The number of buckets in the strong_tx table head, defaults to '551320125'.
strong_tx_buckets = <value>
# The percentage expansion of the strong_tx table body, defaults to '5'.
strong_tx_rate = <value>
# The minimum allocation of the strong_tx table body, defaults to '2987563554'.
strong_tx_size = <value>
# The number of buckets in the tx table head, defaults to '551320125'.
tx_buckets = <value>
# The percentage expansion of the tx table body, defaults to '5'.
tx_rate = <value>
# The minimum allocation of the tx table body, defaults to '15435744998'.
tx_size = <value>
# The number of buckets in the txs table head, defaults to '524493'.
txs_buckets = <value>
# The percentage expansion of the txs table body, defaults to '5'.
txs_rate = <value>
# The minimum allocation of the txs table body, defaults to '999581257'.
txs_size = <value>
# The number of buckets in the validated_bk table head, defaults to '524493'.
validated_bk_buckets = <value>
# The percentage expansion of the validated_bk table body, defaults to '5'.
validated_bk_rate = <value>
# The minimum allocation of the validated_bk table body, defaults to '8290'.
validated_bk_size = <value>
# The number of buckets in the validated_tx table head, defaults to '551320125'.
validated_tx_buckets = <value>
# The percentage expansion of the validated_tx table body, defaults to '5'.
validated_tx_rate = <value>
# The minimum allocation of the validated_tx table body, defaults to '47068879'.
validated_tx_size = <value>

[forks]
# Add check-sequence-verify op code, defaults to true (soft fork).
bip112 = <value>
# Use median time past for locktime, defaults to true (soft fork).
bip113 = <value>
# Segregated witness consensus layer, defaults to true (soft fork).
bip141 = <value>
# Version 0 transaction digest, defaults to true (soft fork).
bip143 = <value>
# Prevent dummy value malleability, defaults to true (soft fork).
bip147 = <value>
# Add pay-to-script-hash processing, defaults to true (soft fork).
bip16 = <value>
# Disallow collision of unspent transaction hashes, defaults to true (soft fork).
bip30 = <value>
# Require coinbase input includes block height, defaults to true (soft fork).
bip34 = <value>
# Finite monetary supply, defaults to true (soft fork).
bip42 = <value>
# Add check-locktime-verify op code, defaults to true (soft fork).
bip65 = <value>
# Require strict signature encoding, defaults to true (soft fork).
bip66 = <value>
# Add relative locktime enforcement, defaults to true (soft fork).
bip68 = <value>
# Assume bip34, bip65, and bip66 activation if enabled, defaults to true (hard fork).
bip90 = <value>
# Require difficult blocks, defaults to true (use false for testnet).
difficult = <value>
# Retarget difficulty, defaults to true.
retarget = <value>
# Fix target overflow for very low difficulty, defaults to false (hard fork).
retarget_overflow_patch = <value>
# Use scrypt hashing for proof of work, defaults to false (hard fork).
scrypt_proof_of_work = <value>
# Fix time warp bug, defaults to false (hard fork).
time_warp_patch = <value>

[log]
# Enable application logging, defaults to true.
application = <value>
# Enable local fault logging, defaults to true.
fault = <value>
# The maximum byte size of each pair of rotated log files, defaults to 1000000.
maximum_size = <value>
# Enable news logging, defaults to true.
news = <value>
# The log files directory, defaults to empty.
path = <value>
# Enable protocol logging, defaults to false.
protocol = <value>
# Enable proxy logging, defaults to false.
proxy = <value>
# Enable quitting logging, defaults to false.
quitting = <value>
# Enable remote fault logging, defaults to true.
remote = <value>
# Enable session logging, defaults to true.
session = <value>
# Path to windows debug build symbols file (.pdb).
symbols = <value>
# Enable verbose logging, defaults to false.
verbose = <value>

[network]
# The lower bound for address selection divisor, defaults to 5.
address_lower = <value>
# The upper bound for address selection divisor, defaults to 10.
address_upper = <value>
# IP address to bind, multiple entries allowed, defaults to 0.0.0.0:8333.
bind = <value>
# IP address to disallow as a peer, multiple entries allowed.
blacklist = <value>
# The age limit for any connection, defaults to 1440.
channel_expiration_minutes = <value>
# The time between ping messages, defaults to 5.
channel_heartbeat_minutes = <value>
# The inactivity time limit for any connection, defaults to 10.
channel_inactivity_minutes = <value>
# The number of concurrent attempts to establish one connection, defaults to 5.
connect_batch_size = <value>
# The time limit for connection establishment, defaults to 5.
connect_timeout_seconds = <value>
# Enable address messages, defaults to true.
enable_address = <value>
# Enable alert messages, defaults to false.
enable_alert = <value>
# Enable internet protocol version 6 (IPv6), defaults to false.
enable_ipv6 = <value>
# Allow connections from the node to itself, defaults to false.
enable_loopback = <value>
# Enable reject messages, defaults to false.
enable_reject = <value>
# Enable transaction relay, defaults to true.
enable_transaction = <value>
# The time limit to complete the connection handshake, defaults to 30.
handshake_timeout_seconds = <value>
# The maximum number of peer hosts in the pool, defaults to 10000.
host_pool_capacity = <value>
# The magic number for message headers, defaults to 3652501241.
identifier = <value>
# The target number of incoming network connections, defaults to 0.
inbound_connections = <value>
# The advertised services that cause a peer to be dropped, defaults to 176.
invalid_services = <value>
# The minimum retained read buffer size, defaults to 4000000.
minimum_buffer = <value>
# The target number of outgoing network connections, defaults to 100.
outbound_connections = <value>
# The peer address cache file directory, defaults to empty.
path = <value>
# A persistent peer node, multiple entries allowed.
peer = <value>
# The maximum network protocol version, defaults to 70012.
protocol_maximum = <value>
# The minimum network protocol version, defaults to 31800.
protocol_minimum = <value>
# The peer download rate limit in bytes per second, defaults to 1024.
rate_limit = <value>
# The time delay for failed connection retry, defaults to 1.
retry_timeout_seconds = <value>
# A seed node for initializing the host pool, multiple entries allowed.
seed = <value>
# The time limit for obtaining seed addresses, defaults to 30.
seeding_timeout_seconds = <value>
# IP address to advertise, multiple entries allowed.
self = <value>
# The maximum services exposed by network connections, defaults to 9 (full node, witness).
services_maximum = <value>
# The minimum services exposed by network connections, defaults to 1 (full node).
services_minimum = <value>
# The minimum number of threads in the network threadpool, defaults to 16.
threads = <value>
# The node user agent string, defaults to '/libbitcoin:4.0.0/'.
user_agent = <value>
# Validate the checksum of network messages, defaults to false.
validate_checksum = <value>
# IP address to allow as a peer, multiple entries allowed.
whitelist = <value>

[node]
# Allowable underperformance standard deviation, defaults to 1.5 (0 disables).
allowed_deviation = <value>
# Time from present that blocks are considered current, defaults to 60 (0 disables).
currency_window_minutes = <value>
# Obtain current header chain before obtaining associated blocks, defaults to true.
headers_first = <value>
# Maximum number of blocks to download concurrently, defaults to '50000' (0 disables).
maximum_concurrency = <value>
# Maximum block height to populate, defaults to 0 (unlimited).
maximum_height = <value>
# Sampling period for drop of stalled channels, defaults to 10 (0 disables).
sample_period_seconds = <value>
# Downloaded bytes that triggers snapshot, defaults to '107374182400' (0 disables).
snapshot_bytes = <value>
# Completed validations that trigger snapshot, defaults to '100000' (0 disables).
snapshot_valid = <value>
```
