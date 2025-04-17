# Run a Libbitcoin Node

 Instructions how to run a Libbitcoin node

!!! warning
    Running a Libbitcoin node by using `bn` should only be used by developers/for testing purposes. A Libbitcoin Server should be run for production, it contains the Bitcoin node and address indexing and a client-server interface._

> This guide is for people who want to test Libbitcoin v4
## Debian/Ubuntu

### Using install.sh

The easiest way to run a libbitcoin node is by cloning the libbitcoin-node repository and then run the install script.

Clone the libbitcoin-node repository and get the build requirements:

`sudo apt-get install git build-essential autoconf automake libtool pkg-config`

`wget` is needed for the install script to download the required dependencies.

In the libbitcoin-node root directory, execute the install script:

`./install.sh --build-dir=/home/user/libbitcoin-node/ --enable-isystem --prefix=/home/user/libbitcoin-node/prefix --disable-static --disable-ndebug  --build-boost  --build-secp256k1`

It will show the libbitcoin-node installer configuration and download and install the dependencies in the specified `--build-dir`.
The `--prefix` is where the _bin_, _etc_, _include_ and _lib_ and _share_ directories will be located.

_bin_ contains the `bn` executable, _etc_ contains the _bn.cfg_ file, which is an example config file (changing values here will not take effect).

The `bn` can be executed, however it will not be able to connect to the Bitcoin network as the default seed nodes currently do not work.
To connect to the Bitcoin network create a config file with specified seed nodes or use a prepopulated hosts.cache file (which contains peers).

- Config file:
Create a config file, for example called _bn.cfg_, and specify seed node(s):

```
[network]
seed = ip:port
seed = host:port
```

- host.cache file:
Have a preppopulated hosts.cache file in _~/libbitcoin-node/prefix/bin/_

Then run the `bn` executable with specifying the config file, for example:
`./bn --config=/home/user/Documents/bn.cfg`

Now the node should start and create outbound connections.
