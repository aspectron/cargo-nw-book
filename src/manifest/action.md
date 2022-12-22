# `[[action]]`

Actions allow execution of various operations at different stages of the package integration.  Current supported commands are:
- `run` executes an external application
- `copy` copy files
- `write` create a custom file with content
- `script` create and execute a custom shell script

Actions acceps filters that denote at which stage or in which environment the action should run.

The following example will execute a script `build-deps` on Linux and `build-deps.bat` on Windows and then copy all binary files from `deps/build/` to `$TARGET/bin`.
```toml
[[action]]
platform = ["windows","linux"]
stage = "build"
items = [
    { run = { cmd = "build-deps$BAT" }},
    { copy = { glob = ["deps/build/*$EXE"], to = "$TARGET/bin" }}
]
```

## Filters
Please note that filters can be specified at the top level (for the action) or for any specific action item, allowing filtering at the action and at the item level.

`stage` property can have the following values: 

- `build` execute the script before the integration begins (before any files are copied)
- `package` execute the script once the integration is complete (all files have been copied into the `$TARGET` folder)
- `deploy` executes the script after redistributables have been built (useful to automatically publish redistributables)
- `publish` executes the action only when user invokes `cargo nw publish` command.

`platform` list allows to specify one or more supported platforms:
- `windows`
- `linux`
- `macos`

`arch` list specifies the system architecture
- `ia32`
- `x64`
- (`aarch64` is not supported as of writing this document but is planned to be supported when NWJS starts releasing aarch64-compatible builds)

`family` specifies the platform family and can have the following values:
- `windows`
- `unix`

## Action Items

The following operations can be included in the list of action items:

- `run` - executes an application of a command on the underlying operating system
- `copy` - performs file copy
- `write` - creates and writes content to a file
- `script` - creates and executes a script on the underlying operating system

