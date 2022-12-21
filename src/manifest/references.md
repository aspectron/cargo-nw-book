# References

Certain manifest properties can reference external values.  This is done by specifying an external `.toml` or `.json` file and a variable path as follows:

```toml
[application]
name = "Cargo.toml::application.name"
version = "Cargo.toml::application.version"
...
[description]
short = "Cargo.toml::application.description"
...
```
or
```toml
[aplication]
version = "package.json::version"
```

The reference contains 2 parts: `<filename>::<variable-path>` where `<variable-path>` is a dot-delimited path to the required sub-object property.  The specified property must contain a string value.

This method makes it easier to track such values as a project version by allowing it to be set in a single location, especially when integrating `cargo-nw` into an existing project.
