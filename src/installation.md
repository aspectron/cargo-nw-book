# Installation

You can install `cargo-nw` from source using `cargo`. If Rust is not available, please see the [`Installing Rust`](#installing-rust) section below.

Install and run `cargo-nw` using `cargo`:
```bash
cargo install cargo-nw

cargo nw --help
```

## Installing Rust

To install `cargo-nw` from source, you need to install the Rust programming language as follows:

On Unix systems (Linux & MacOS) run:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
For Windows systems, download and run: [rustup-init.exe](https://static.rust-lang.org/rustup/dist/i686-pc-windows-gnu/rustup-init.exe)

Alternatively, see [other installation methods](https://forge.rust-lang.org/infra/other-installation-methods.html).

## Dependencies

* [InnoSetup for Windows](https://jrsoftware.org/isdl.php) - allows creation of interactive Windows application installers
* [SnapCraft](https://snapcraft.io/install/snapcraft/ubuntu) + [LXD](https://linuxcontainers.org/lxd/getting-started-cli/) - allows building of redistributable images for compatible Linux distributions
* [WASMPACK](https://rustwasm.github.io/wasm-pack/installer/) if you want to build Node Webkit WASM applications in Rust


## Operating Systems

To create installers you will need to run `cargo-nw` on each respective operating system. If you do not posess the hardware, you may be able to get around usign virtualization software such as [Virtual Box](https://www.virtualbox.org/) for Windows and Linux and [UTM for MacOS](https://mac.getutm.app/)