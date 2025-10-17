# Run a Libbitcoin Node

 Instructions how to run a Libbitcoin node

!!! warning
    Running a Libbitcoin node by using `bn` should only be used by developers/for testing purposes. A Libbitcoin Server should be run for production, it contains the Bitcoin node and address indexing and a client-server interface._

> This guide is for people who want to test Libbitcoin v4
## Windows

### Using MSBuild

The easiest way to run a libbitcoin node is by cloning the libbitcoin-node repository and then run the install script.

Clone the libbitcoin-node repository:

`git clone https://github.com/libbitcoin/libbitcoin-node.git`

In the libbitcoin-node root directory, execute the install script:

`.\build.cmd .. x64 StaticRelease x64 vs2022`

It will show the libbitcoin-node installer configuration and download and install the dependencies.

The resulting `bn.exe` executable can be found at:
`C:\Users\UserName\libbitcoin-node/builds/msvc/vs2022/libbitcoin-node/x64/Release/bn.exe`

Now run the `bn.exe` and the node will start and create outbound connections.
