# Windows MSBuild

The libbitcoin-protocol library can be build either as a static debug version or a static release version, and Win32 or x64.

To build, follow these steps:

## Clone the repository

```
git clone https://github.com/libbitcoin/libbitcoin-protocol.git
```

## Execute the install script

Navigate to the cloned repository and then execute the install script.

_(.\build.cmd .. ${ platform } ${ configuration } x64 ${ version })_

### Static Debug

Build with the default options and static linking:
```
.\build.cmd .. x64 StaticDebug x64 vs2022
```

### Static Release

Build with static linking:
```
.\build.cmd .. x64 StaticRelease x64 vs2022
```

---

The library, and dependent libraries will now be build.

