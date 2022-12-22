# Installation

To install `cargo-nw` from source, you need to install Rust programming language (see [Dependencies](#dependencies) below)

Install `cargo-nw` using Cargo:
```bash
cargo install cargo-nw
```
Following that you can run:
```bash
cargo nw --help
```

## Dependencies
* [Rust Programming Language](https://www.rust-lang.org/tools/install) - to use `cargo` and if desirable, build WASM-based Node Webkit projects 
* [InnoSetup for Windows](https://jrsoftware.org/isdl.php) - allows creation of interactive Windows application installers
* [WASMPACK](https://rustwasm.github.io/wasm-pack/installer/) if building Node Webkit WASM applications in Rust
* [SnapCraft](https://snapcraft.io/install/snapcraft/ubuntu) + [LXD](https://linuxcontainers.org/lxd/getting-started-cli/) - allows building of redistributable images for compatible Linux distributions


## Operating Systems

To create installers you will need to run `cargo-nw` on each respective operating system. If you do not posess the hardware, you may be able to get around usign virtualization software such as [Virtual Box](https://www.virtualbox.org/) for Windows and Linux and [UTM for MacOS](https://mac.getutm.app/)