# The clean command

The clean command removes intermedia files produced by `cargo-nw`.

- `cargo nw clean` will delete build and cache folders )`target/nw/build` and `taget/nw/cache`)
- `cargo nw clean --deps` in addition to the above, will delete dependencies located in `$HOME/.cargo-nw`. This includes all downloaded NWJS releases and external dependencies.