# Templates

Cargo NW can create Node Webkit project templates. It can generate a basic Rust WASM application or only a manifest file (if integrating with an existing project).

To create a WASM template run the following:
```bash
cargo nw init
```
Similarly to `npm init` or `cargo init` this will create a project in the current folder, using the folder as a project name.

The `init` command accepts the following arguments:

- `name` - (optional) name of the project. If omitted, `cargo nw` will use the current folder name and confirm the name with a prompt.  If `cargo nw` detects an existing `Cargo.toml` or `package.json` file in the same folder, it will use the name from these pre-existing manifests.
- `js` - (TODO) generate a classic Node Webkit JavaScript-based project (no WASM)
- `manifest` - create `nw.toml` manifest file only
- `force` - force overwrite any existing files (by default, `cargo nw` will abort if it detects any existing files)

