# `script`

`script` allows for creation of a custom script during the integration process and execution of this script


`script` supports the following options:
- `type` - script type: `bash`,`sh`,`zsh`,`bat`,`cmd`,`ps1`
- `name` - *optional* - script file name
- `interpreter` - *optional* the interpreter used to run the script (by default the interpreter is derived from the script `type` property)
- `script` - script content

`script` supports the following filter options:
- `platform` - platform filter
- `arch` - architecture filter
- `family` - platform family filter


```toml
[[action]]
items = [
# this is bash script that will run only 
# on Linux and MacOS dur to family filter
{ script = { type = "bash", family = "unix", script = """
echo "running Bash!"
""" }},
# this is CMD script that will run only 
# on Windows due to family filter
{ script = { type = "cmd", family = "windows", script = """
echo "running CMD!"
""" }},
]
```