# `[package]`

Package directive controls the packaging properties of the redistributable.

- `archive` - ZIP archive format.  Currenly only `DEFLATE` and `STORE` formats are supported. Cargo NW supports `BZIP2` and `ZSTD`, unfortunately target operating systems do not alwasy support these formats and they should not be used.

- `signatures` - when set to `true` this will generate `.sha256sum` files containing SHA256 hash of the resulting file. This can be used to fingerprint and validate the validity of the downloadable file. Beware - this is a superficial validation and does not protect you from malicious activity. For proper validation of redistributables you should use GPG key signing.

- `source` - the source folder of the project relative to the `nw.toml` manifest.

- `build` - The build directive supports two objects: `WASM` and `NPM`.
    * `WASM` will run `wasmpack` on the root folder before the integration process begins.
    * `NPM` will run `npm install --omit dev` on the root folder before the integration process begins.

- `resources` - location of setup resources (icon files) relative to the location of the manifest file. By default this folder is `resources/setup`

- `include` - include filters allowing glob or regex selection of the files that should be copied from the application root folder into the redistributable. By default, all files are included.

- `exclude` - exclusion filter allowing glob or regex filtering of the files being copied to the redistributable application folder.  In a typical configuration these should be set to exclude all folders that should be be a part of your redistributable, for example `exclude = { glob = ["{bin/*,src/*,target/*,test/*,*.lock,*.toml,.git*}"]}` If needed, you can specify multiple glob and regex entries that will be combined during the filtering process.

