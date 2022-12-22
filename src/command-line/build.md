# The build command

Builing redistributables with `cargo nw` for different operating systems requires you to perform the build on the target operating system.

To build a redistributable you can use the following command:
```bash
cargo nw build <target>
```

Each target, except `archive` is specific to the operating system `cargo nw` is running on. `archive` targets are universal and produce a `.zip` file usable on the target operating system.

Following targets are available:
- `all` - build all targets available on the current OS
- `archive` - create a `.zip` archive of the redistributable
- `dmg` - (MacOS) - generate a MacOS DMG image
- `innosetup` - (Windows) - generate an InnoSetup interactive installer
- `snap` - (Linux*) - generate a Snapcraft redistributable image

*) Please note that `snap` is compatible only with Linux distributions that support Snapcraft.

The `build` command supports the following options:
- `--sdk` - builds the redistributable using Node Webkit SDK runtime (overriding the setting in the manifest file).
- `--dry-run` - performs integration, but does not generate a redistributable image.  You can find resulting files in the `target/nw/build/` folder. If needed, you can test-run the application from the build folder.
- `--channel <'stable' or 'devel'>` - *Linux only* - builds a snap image using the specified channel (overrides the setting in the manifest file).
- `--confinement <'strict', 'classic' or 'devmode'>` - *Linux only* - builds a snap image using the specified confinement (overrides the setting in the manifest file).
- `--arch <'x64' or 'ia32'>` builds a redistributable for the specified architecture (overrides the architecture of the current platform; can be used to build an `ia32` build on `x64` systems)


