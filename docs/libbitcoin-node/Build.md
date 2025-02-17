# Libbitcoin-node build instructions

## Linux Debian/Ubuntu

### Using install.sh

Get the build requirements:
`sudo apt-get install git build-essential autoconf automake libtool pkg-config`

`wget` is needed for the install script to download the required dependencies.

In the libbitcoin-node root directory, execute the install script:

`./install.sh --build-dir=/home/user/libbitcoin-node/ --enable-isystem --prefix=/home/user/libbitcoin-node/prefix --disable-static --disable-ndebug  --build-boost  --build-secp256k1`

It will show the libbitcoin-node installer configuration and download and install the dependencies in the specified `--build-dir`.
The `--prefix` is where the _bin_, _etc_, _include_ and _lib_ and _share_ directories will be located.

_bin_ contains the `bn` executable, _etc_ contains the _bn.cfg_ file, which is an example config file (changing values will not take effect).
