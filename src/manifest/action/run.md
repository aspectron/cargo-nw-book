# `run`

`run` directive allows execution of an external application

Example:
```toml
[[action]]
items = [{ run = { cmd="echo \"source: $SOURCE target: $TARGET\""} }]
```
or
```toml
[[action]]
items = [{ run = { argv=["echo","source: $SOURCE target: $TARGET"], cwd = "$TARGET" } }]
```

`run` supports the following options:

- `cmd` - a string command to execute.  Please note that to execute such command, the string is broken down into an array of arguments separated by spaces. As such, if the string contains file paths or arguments that contain spaces, this may create interference and result in the incorrect parsing of the arguments. Please use `argv` to specify explicitly each argument as it should be passed to the application.
- `argv` - list of arguments to be passed to the application. First argument must contain the application name available in the system PATH environment variable.
- `cwd` - working directory in which the application should be executed.
- `env` - an array of environment variables passed as pairs as follows: `["K1=V1","K2=V2"]`

`run` supports the following filter options:

- `platform` - platform filter
- `arch` - architecture filter
- `family` - platform family filter

