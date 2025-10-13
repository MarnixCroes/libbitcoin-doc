# Linux CMake List Build

The libbitcoin-protocol library can be build either dynamic or static.

GCC and Clang compilers are officially supported.
The following steps assume you have either of these installed.

To build, follow these steps:
## Install the required dependencies
```
sudo apt-get install git build-essential autoconf automake libtool pkg-config 
```

{CPU flag could be determined in order to enable hash function optimizations, more information about this will be added to the docs later}

## Clone the repository

```
git clone https://github.com/libbitcoin/libbitcoin-protocol.git
```

## Execute the install script

Navigate to the cloned repository and then execute the install script.

`./install-cmake.sh --help` will display all the options.

It can be either a `dynamic` build or a `static` build:

---

> Change the `build-dir` and `prefix` location if desired and use the desired parameters.

### Dynamic

Build with the default options and dynamic linking:
```
./install-cmake.sh --build-dir=/home/user/libbitcoin-protocol/  --prefix=/home/user/libbitcoin-protocol/prefix --disable-static --disable-ndebug -Denable-ndebug=no  --build-boost  --build-secp256k1 --build-zmq
```

### Static

Build with static linking and ICU support:
```
./install-cmake.sh --build-dir=/home/user/libbitcoin-protocol/  --prefix=/home/user/libbitcoin-protocol/prefix --disable-shared --enable-ndebug -Denable-ndebug=yes  --build-boost --build-icu --with-icu --build-secp256k1 --build-zmq
```

---

The library, and dependent libraries will now be build in the specified directory.
