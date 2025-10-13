# macOS Autotools Build

The libbitcoin-system library can be build either dynamic or static.

Clang compiler is officially supported.
The following steps assume you have it installed.

To build, follow these steps:
## Install the required dependencies
```
brew install autoconf automake libtool icu4c
```

{CPU flag could be determined in order to enable hash function optimizations, more information about this will be added to the docs later}

## Clone the repository

```
git clone https://github.com/libbitcoin/libbitcoin-system.git
```

## Execute the install script

Navigate to the cloned repository and then execute the install script.

`./install.sh --help` will display all the options.

It can be either a `dynamic` build or a `static` build:

---

> Change the `build-dir` and `prefix` location if desired and use the desired parameters.

### Dynamic

Build with the default options and dynamic linking:
```
./install.sh --build-dir=/Users/libbitcoin-system/ --enable-isystem --prefix=/Users/libbitcoin-system/prefix --disable-static --enable-ndebug  --build-boost  --build-secp256k1
```

### Static

Build with static linking:
```
./install.sh --build-dir=/Users/libbitcoin-system/ --enable-isystem --prefix=/Users/libbitcoin-system/prefix --disable-shared --enable-ndebug  --build-boost  --build-secp256k1
```

---

The library, and dependent libraries will now be build in the specified directory.
