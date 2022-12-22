# `write`


`write` allows you to create a file with custom content as a part of the action execution.

`write` supports the following options:

- `file` - name of the target file
- `content` - file content

`write` support the following filter options:

- `platform` - platform filter
- `arch` - architecture filter
- `family` - platform family filter

Example:

```toml
[[action]]
items = [
    { write = { file = "$TARGET/config/project.toml", content = """
    [config]
    name = "$NAME"
    """}},
    { write = { file = "$TARGET/package.json", content = """
    {
        "name": "$NAME",
        "version" : "$VERSION"
    }
    """}}
]
```