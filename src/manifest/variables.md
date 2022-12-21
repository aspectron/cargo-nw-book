# Variables

Most of the manifest properties (other than the `[application]` section) support injection of variables provided by `cargo-nw` during the integration process.

`cargo-nw` offers a set of internal variables created in the context of the ongoing integration combined with environment variables available at the time of execution.

Internal variables are:

- `$SOURCE` - source project folder (specified in the manifest by `package.root` property)
- `$TARGET` - destination folder (target application folder)
- `$TEMP` - temporary folder (located inside of the `target/` folder) used by cargo-nw to store temporary information. This is not a system temp folder.
- `$PLATFORM` operating system platform (`windows`,`linux` or `macos`)
- `$ARCH` operating system architecture (`ia32` or `x64`)
- `$NAME` - manifest `application.name`value
- `$TITLE` - manifest `application.title` value
- `$VERSION` manifest `application.version` value
- `$ORGANIZATION` - manifest `application.organization` value
- `$SHORT` - manifest `description.short` value
- `$LONG` - manifest `description.long` value
- `$EXE`- `.exe` on Windows and empty on unix
- `$BAT` - `.bat` on Windows and empty on unix
- `$CMD` - `.cmd` on Windows and empty on unix
- `$PS1` - `.ps1` on Windows and empty on unix
- `$SH` - empty on Windows and `.sh` on unix

`$EXE` variable can be used to construct a binary filename where the filename on unix family of platforms may not have a filename extension, while on windows the extension may be `.exe`, as such specifying `cmd = "my-app$EXE"` will result in `my-app.exe` on Windows and `my-app` on unix.

Similarly, if you have a bash build script with an extension `.sh` and a PowerShell script with an extension `.ps1` you can construct a filename `my-file$SH$PS1` that will result in `my-file.ps1` on unix and `my-file.sh` on unix.

In addition, environment variables available at the execution time of the `cargo-nw` are also available.  As such, you can specify custom variables when running `cargo-nw` as follows:
```sh
MYVAR="ALPHA" cargo nw my-app.toml build all
```
Where the manifest file can use `$MYVAR` to spply options to internal actions, resource strings etc. For example:
```toml
[[action]]
items = [
    { run = { cmd = "myproc $HOME $MYVAR" }}
]
```


