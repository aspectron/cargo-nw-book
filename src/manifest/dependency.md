# `[[dependency]]`

Dependency directives allow building of external dependencies from a git repository and copying the resulting files into the target redistributable.  This is useful when you integrate external applications as a part of your distributable.

Please note that if the dependency relies on 3rd-party build tools, these tools need to be installed and available in the system PATH environment variable.

Dependency processing steps:
- `git clone [-b branch]` (if exists, `git pull`)
- check last repository commit
- if commit has changed, execute `run` directive (otherwise skip)
- execute `copy` directive

`[[dependency]]` directive supports the following properties:

- `git` - an object specifying the git repository from which to fetch the given dependency. This object supports the following options:

    - `url` specifying the git repository URL
    - `branch` - *optional* - specifying the branch. Example: `git = { url = "https://github.com/org/repo", branch = "release" }`
\
\
        The `branch` option, if present, is relayed to the `git checkout` command. if omitted, `git` will use the default branch.

    Please note that if `branch` name is changed, you will need to run `cargo nw clean` command to reset the cached dependency repository.

- `run` - executes a command inside of the dependency folder. `run` supports the following options:

    - `cmd` - a string command to execute.  Please note that to execute such command, the string is broken down into an array of arguments separated by spaces. As such, if the string contains file paths or arguments that contain spaces, this may create interference and result in the incorrect parsing of the arguments. Please use `argv` to specify explicitly each argument as it should be passed to the application.
    - `argv` - list of arguments to be passed to the application. First argument must contain the application name available in the system PATH environment variable.
    - `cwd` - working directory in which the application should be executed.
    - `env` - an array of environment variables passed as pairs as follows: `["K1=V1","K2=V2"]`

    `run` supports the following filter options:

    - `platform` - platform filter
    - `arch` - architecture filter
    - `family` - platform family filter

- `copy` - copies files from the dependency folder. `copy` supports the following options:

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
[[dependency]]
name = "kaspad"
git = { url = "https://github.com/kaspanet/kaspad", branch = "release" }
run = [
    # commands are executed in the repository folder
    { cmd = "go build" },
    { cmd = "go build", folder = "cmd/genkeypair" },
    { cmd = "go build", folder = "cmd/kaspactl" },
    { cmd = "go build", folder = "cmd/kaspawallet" },
]
copy = [
    { regex = [
        "kaspad(.exe)?$",
        "genkeypair(.exe)?$",
        "kaspactl(.exe)?$",
        "kaspawallet(.exe)?$",
    ], to = "bin/$PLATFORM-$ARCH", flatten = true },
]
```