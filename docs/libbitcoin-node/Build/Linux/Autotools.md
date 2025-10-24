# Linux Autotools Build

The libbitcoin-node library can be build either dynamic or static.

GCC and Clang are officially supported.
The following steps assume you have either of these installed.

To build, follow these steps:
## Install the required dependencies
```
sudo apt-get install git build-essential autoconf automake libtool pkg-config
```

{CPU flag could be determined in order to enable hash function optimizations, more information about this will be added to the docs later}

## Clone the repository

```
git clone https://github.com/libbitcoin/libbitcoin-node.git
```

## Execute the install script

Navigate to the cloned repository and then execute the install script.

`./install.sh --help` will display all the options.

It can be either a `dynamic` build or a `static` build:

---

> Change the `build-dir` and `prefix` location if desired and use the desired parameters.

> The default build directory is /user/local. However, creating diretories usually requires (sudo) privileges. Which is why `build-dir` and `prefix` are set.

### Dynamic

Build with the default options and dynamic linking:
```
./install.sh --build-dir=/home/user/libbitcoin-node/ --enable-isystem --prefix=/home/user/libbitcoin-node/prefix --disable-static --disable-ndebug  --build-boost  --build-secp256k1
```

### Static

Build with static linking and ICU support:
```
./install.sh --build-dir=/home/user/libbitcoin-node/ --enable-isystem --prefix=/home/user/libbitcoin-node/prefix --disable-shared --enable-ndebug  --build-boost --build-icu --with-icu --build-secp256k1
```

---

The library, and dependent libraries will now be build in the specified directory.
