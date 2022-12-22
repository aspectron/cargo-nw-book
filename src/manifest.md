# Manifest File Format

`cargo-nw` manifest file uses [TOML](https://toml.io/) configuration file format.  By default, `cargo-nw` searches for `nw.toml` file in the current directory, however, you can specify an alternate file by specifying relative path or a path with a filename only. i.e. `cargo nw app-lite build all` (will use `app-lite.toml` file) or `cargo nw ../build/app-full build all` (will use `../build/app-full.toml` file)

Most of the values specified in the manifest (except in the application section and script contents) can use internal variables that use $ prefix with the variable name in upper case (i.e. "$SOMEVAR"). For example:

```toml
[application]
...
version = "1.2.3"
title = "App Lite"
...
[windows]
resources = [{ ProductName = "$TITLE $VERSION" }]
```

There are two sections that can be present multiple times in the manifest: `[[action]]` and `[[dependency]]`. Sections that can be present multiple times are denoted by double brackets.  These sections are processed in the order specified in the manifest.

The manifest contains the following sections:

- [[application]](./manifest/application.md) - application options
- [[description]](./manifest/description.md) - application description
- [[package]](./manifest/package.md) - integration options
- [[node-webkit]](./manifest/node-webkit.md) - node-webkit options (redistributable version etc.)
- [[[action]]](./manifest/action.md) - *optional* - integration actions
- [[[dependency]]](./manifest/dependency.md) - *optional* - dependency build options
- [[macos-disk-image]](./manifest/macos-disk-image.md) - *optional* - (MacOS) - DMG Finder window layout.
- [[windows]](./manifest/windows.md) - *optional* - windows specific options
- [[images]](./manifest/images.md) - *optional* - image filename overrides
- [[languages]](./manifest/languages.md) - *optional* - (InnoSetup) - installer languages
- [[firewall]](./manifest/firewall.md) - *optional* - (InnoSetup) - firewall rules for your application (should be present if your application makes network requests)
- [[snap]](./manifest/snap.md) - *optional* - (Snap) - Snap configuration properties.