# Introduction

Cargo NW is a *redistributable package generator* for applications developed using the [Node Webkit](https://nwjs.io) application platform. Cargo NW generates application redistributables in a form of ready-to-use application folders, application archives, DMG images for MacOS, interactive installers powered by [InnoSetup](https://jrsoftware.org/isinfo.php) for Windows as well as [Snapcraft](https://snapcraft.io/) images for compatible Linux distributions.

Cargo NW was developed to support next-gen WASM-powered applications developed in Rust on top of the Node Webkit platform and provides an ability to easily generate and build Rust-WASM-based desktop application templates. 

While Cargo NW was designed to accomodate Rust WASM projects, it is capable of creating redistributables for traditional JavaScript projects. Cargo NW TOML manifest file format includes the ability to declare and build external dependencies and execute actions, allowing for customization of the application build process.

During the application integration process, Cargo NW will automatically download appropriate Node Webkit binaries, making it easy to switch between Node Webkit versions as well as the regular vs. SDK editions.

The goal of this tool is to simplify and automate the creation of redistributable packages, which in many cases can be an extremely tedious and a challenging process.


---

If you find this software useful, please consider supporting our development on Patreon. Your support allows us to improve and further customize this software for fellow developer needs. Please visit our website [https://aspectron.org](https://aspectron.org) more information.