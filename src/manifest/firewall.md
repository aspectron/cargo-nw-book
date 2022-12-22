# `[firewall]`

The firewall section currently works on Windows only and functions by embedding a call to `netsh advfirewall` into the InnoSetup script to be executed after the application installation.

The following properties are supported:

- `application`  an object containing `direction` property which can be set to contain `in` and `out` strings, depending on whether the application desires to be an outbound and/or inbound access.
- `rules` - *optional* - a set of rules for additional executables that may be included with the application - an array of objects containing `name`, `program` and `direction` properties, where `name` is the firewall rule name, `program` is the executable filename relative to the program installation path and `direction` specifying the access direction (`in` and/or `out`)

Example:
```toml
[firewall]
application = { direction = "in+out" }
rules = [
    { name = "MyChildService", program = "bin\\windows-x64\\my-child-service.exe", direction="in+out" }
]
```
