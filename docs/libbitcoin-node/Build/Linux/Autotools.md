# Linux Autotools Build

The libbitcoin-node library can be build either [dynamic](/docs/libbitcoin-node/Build/Linux/Autotools.md#dynamic) or [static](/docs/libbitcoin-node/Build/Linux/Autotools.md#static).

GCC and Clang are officially supported.
The following steps assume you have either of these installed.

To build, follow these steps:

## Dynamic

### Prepare toolchain
```
sudo apt-get install git build-essential autoconf automake libtool pkg-config
```

{CPU flag could be determined in order to enable hash function optimizations, more information about this will be added to the docs later}

### Execute the install script

Change the `build-dir` and `prefix` location if desired.
And note that the arguments may be discarded.

```
./install.sh --build-dir=/home/libbitcoin-node/ --enable-isystem --prefix=/home/libbitcoin-node/prefix --disable-static --disable-ndebug  --build-boost  --build-secp256k1
```

The library, and dependent libraries will now be build in the specified directory.

---

## Static

### Prepare toolchain
```
sudo apt-get install git build-essential autoconf automake libtool pkg-config
```

{CPU flag could be determined in order to enable hash function optimizations, more information about this will be added to the docs later}

### Execute the install script

Change the `build-dir` and `prefix` location if desired.
And note that the arguments may be discarded.

```
./install.sh --build-dir=/home/runner/work/libbitcoin-node/ --enable-isystem --prefix=/home/runner/work/libbitcoin-node/prefix --disable-shared --enable-ndebug  --build-boost --build-icu --with-icu --build-secp256k1
```

The library, and dependent libraries will now be build in the specified directory.