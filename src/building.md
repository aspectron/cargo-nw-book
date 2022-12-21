# Building

Builing redistributables with `cargo nw` for different operating systems requires you to perform the build on the target operating system.

To build a redistributable you can use the following command:
```bash
cargo nw build <target>
```

Each target, except `archive` is specific to the operating system `cargo nw` is running on.

Following targets are available:
- `all` - build all targets available on the current OS
- `archive` - create a ZIP archive of the redistributable
- `dmg` - (MacOS) - generate a DMG image
- `innosetup` - (Windows) - generate an InnoSetup interactive installer
- `snap` - (Linux*) - generate a Snapcraft redistributable image

*) Please note that `snap` is compatible only with Ubuntu-compatible linux systems that support Snapcraft.

The `build` command supports the following options:
- `--sdk` - builds the application using Node Webkit SDK runtime.
- `--dry-run` - performs integration, but does not generate a redistributable image.  You can find resulting files in the `target/nw/build/` folder. If needed, you can test-run the application from the build folder.
- `--channel <'stable' or 'devel'>` - (Linux only) builds a snap image using the specified channel.
- `--confinement <'strict', 'classic' or 'devmode'>` (Linux only) builds a snap image using the specified confinement.
- `--arch <'x64' or 'ia32'>` builds a redistributable for the specified architecture (can be used to build an `ia32` build on `x64` systems)

