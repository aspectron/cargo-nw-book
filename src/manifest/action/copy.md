# `copy`

`copy` directive provides file copy functionality.

`copy` supports the following options:

- `glob` - an array of glob patterns. Creates a source file set based on the supplied set of glob patterns.
- `regex` - an array of regular expressions. Creates a source file set based on the supplied list of regular expressions.
- `file` - selects a single source file relative to the 
- `to` - destination folder (if used with `glob` or `regex`) or destination file (if used with `file`)
- `flatten` - copies all files into the destination folder without preserving the original folder structure.
- `hidden` - copies hidden files and folders (files or folder names starting with `.`) that are otherwise ignored.

`copy` supports the following filter options:

- `platform` - platform filter
- `arch` - architecture filter
- `family` - platform family filter

Example:

```toml
[[action]]
name = "copy binaries"
items = [
    # copy all files in `bin` folder to $TARGET/bin
    { copy = { glob = ["**/bin/*"], to = "$TARGET/bin" }},

    # copy all files in `extern/bin` to $TARGET/bin
    { copy = { regex = ["extern/bin/[^/]+$"], to = "$TARGET/bin" }},

    # copy all files in `server/**/bin` and `client/**/bin` to $TARGET/bin
    # copy without preserving source folder structure (all files will copy to $TARGET/bin)
    { copy = { regex = ["server/.+/bin/[^/]+$", "client/.+/bin/[^/]+$"], to = "$TARGET/bin", flatten = true }},

    # copy all `.tpl` files from subfolders named `templates` and rename them to *.cfg
    # copy without preserving source folder structure (all files will copy to $TARGET/configs)
    { copy = { glob = ["**/templates/*.tpl"], to = "$TARGET/configs/*.cfg", flatten = true }},
]
```

```toml
[[action]]
name = "copy project config"
items = [
    # copy file and rename it
    { copy = { file = "template.cfg", to = "$TARGET/project.cfg" }}
]
```

