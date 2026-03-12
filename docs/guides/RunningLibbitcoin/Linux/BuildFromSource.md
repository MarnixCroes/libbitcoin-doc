# Build Libbitcoin Server from source

 Instructions on how to run Libbitcoin

!!! warning
    Libbitcoin v4 is still under development. Use it for testing purposes._

> This guide is for people who want to test Libbitcoin v4
## Debian/Ubuntu

### Using install.sh

The easiest way to run a libbitcoin node is by cloning the libbitcoin-node repository and then run the install script.

Clone the libbitcoin-node repository and get the build requirements:

`sudo apt-get install git build-essential autoconf automake libtool pkg-config`

`wget` is needed for the install script to download the required dependencies.

In the libbitcoin-node root directory, execute the install script:

`./install.sh --build-dir=/home/user/libbitcoin-server/ --enable-isystem --prefix=/home/user/libbitcoin-server/prefix --disable-static --disable-ndebug  --build-boost  --build-secp256k1`

It will show the libbtcoin-server installer configuration and download and install the dependencies in the specified `--build-dir`.
The `--prefix` is where the _bin_, _etc_, _include_ and _lib_ and _share_ directories will be located.

_bin_ contains the `bs` executable, _etc_ contains the _bn.cfg_ file, which is an example config file (changing values here will not take effect).

Now run the `bs` executable and the Libbitcoin server, including a Bitcoin node, will start and create outbound connections.
