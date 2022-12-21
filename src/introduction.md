# Introduction

Cargo NW is a utility built to package Node Webkit (NWJS) applications as multi-platform redistributable packages - archives as well as interactive installers that can run on Window, MacOS and Linux and provide a platform-native installation experience for applications built using Node Webkit.

Node Webkit is a unique application in that it combines The Chromium browser JavaScript interpreter (V8) with NodeJS JavaScript interpreter (which is also V8), providing access to all NodeJS functionailty from within the web page DOM.

This allows an application to achieve functionality like this:
```JavaScript
    let html = fs.readFileSync("myfile);
    document.getElementById("my-text").setInnerHTML(html);
```

Cargo NW was developed as a part of an initiative to bring Rust WebAssembly to Node Webkit and allow development of Rust-based Web-enabled desktop applications.

While Cargo NW was designed to accomodate Rust WASM projects, it is perfectly capable of creating redistributables for any type of project. It natievly supports running NPM for update or if needed an installation of `node_modules` (which can also be exposed to Rust via [`wasm_bindgen`](https://crates.io/crates/wasm-bindgen)) or custom execution of tools can be setup to run during any stage of the redistributable integration.

Cargo NW reads the manifest file (by default named `nw.toml`) and using information provided in it packages an archive, a DMG image for MacOS or generates installation scripts for InnoSetup (Windows) or SnapCraft (Linux).

The goal of this tool is to automate the creation of redistributable packages, which in many cases can be an extremely tedious and challenging process.