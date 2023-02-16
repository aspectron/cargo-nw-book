# The run command

The run command allows you to run your application using a downloaded version of NW runtime.

Executing `cargo nw run` is equivalent to running `nw .` in the application folder, with exception that `cargo nw run` does not require any additional system configuration (i.e. the application will run "out of the box").

### Runtime versions

The main advantage of using `run` command is that it accepts the `--nw-version` argument.

For example, running the following command: 
```
cargo nw run --nw-version=0.60.0
``` 
will run your application with the runtime version v0.60.0 while running 
```
cargo nw run --nw-version=0.73.0
```

will run it using v0.73.0.

If the runtime for the requested version is not currently available, it will be downloaded from [https://dl.nwjs.io](https://dl.nwjs.io/)

In many ways, this is similar to NVM - a node version manager that allows you to dynamically switch between different versions of the Node.js runtime.

`cargo nw run` does not affect the system environment.  It simply starts your application with the specified version of the runtime.

NW runtimes are downloaded and extracted in the `~/.cargo-nw/` folder.

