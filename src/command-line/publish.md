# The publish command

Publish command executes all actions with the `stage` option set to `publish`.  Unlike the `deploy` stage, that executes automatically after the integration process, `publish` stage is executed explicitly from the command line.

This command is useful to perform manual deployment of the generated redistributables.

Example of an action that runs at the `publish` stage:
```toml
[[action]]
stage = "publish"
items = [{ run = { cmd = "scp $NAME-$VERSION* user@host:releases/", cwd = "$OUTPUT"}}]
```
