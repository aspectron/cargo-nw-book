# `[snap]`

- `channel` - `stable` or `devel` - detailed information is available [here](https://snapcraft.io/docs/channels).

- `confinement` - `strict`, `classig` or `devmode` - detailed information is available [here](https://snapcraft.io/docs/snap-confinement).

- `interfaces` - additional interfaces that should be included in the application snap file. Default interfaces incuded are             `browser-support`, `network`, `network-bind`, `opengl`, `x11`, `upower-observe`. A complete list of interfaces available can be found [here](https://snapcraft.io/docs/supported-interfaces).

- `packages` - list of additional packages that should be included for ELF (dynamic linkage) resolution.  This is only needed if you are including additional external binaries in your application. When including additional binaries, Snapcraft may produce ELF errors specifying missing libraries. You can then take the library prefix (name) and search for the packages that includes this library using the following command `apt list | grep <package-substring>`. Once the package has been identified, you can include it in the `snap.packages` list. 

Please note: during the build Snapcraft may produce warnings about incorrect ELF paths. This is normal and as long as `.snap` file is produced, the application will function correctly.

Please note: if using `strict` confinement, Node Webkit will not be able to access GPU hardware and will fallback to software rendering mode. Depending on the functionality offered by your application, it is possible that it may experience other constraints. To mitigate this, you can try identifying and including required [interfaces](https://snapcraft.io/docs/supported-interfaces) in the `snap.interfaces` list or use the `classic` confinement.