# The clean command

The clean command removes intermedia files produced by `cargo-nw`.

`cargo nw clean` will delete build and cache folders (`target/nw/build` and `taget/nw/cache`).

`cargo nw clean <flags>` will clean intermediate files according to flags as follows:

- `--deps` in addition to the above, will delete dependencies folder `target/nw/deps`

- `--dist` will delete downloaded Node Webkit redistriutable releases folder `$HOME/.cargo-nw`

- `--all` will perform all operations above

