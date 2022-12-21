# `[node-webkit]`

This section supports the following properties:

- `version` - a string version of the node webkit that should be used during the integration.

- `sdk` - a boolean `true` or `false` value that enables inclusion of `NWJS SDK` runtime in your application redistributable.  This property can also be speified from the command line during the project build time as follows: `cargo nw --sdk build all`.  Please note that including the SDK functionality into the redistributable can result in users gaining access to the internals of your application, as such, it is recommended to omit this flag (it is set to `false` by default) and specify it from the command-line when needed.

- `ffmpeg` a boolean `true` or `false` value that enables inclusion of a fully-enabled community-built FFMPEG libraries available at [https://github.com/iteufel/nwjs-ffmpeg-prebuilt/releases/](https://github.com/iteufel/nwjs-ffmpeg-prebuilt/releases/) (please see below for licensing information)


PLEASE NOTE: Using MP3 and H.264 codecs requires you to pay attention to the patent royalties and the license of the source code. Consult a lawyer if you do not understand the licensing constraints and using patented media formats in your application. For more information about the license of the source code, please check [here](https://chromium.googlesource.com/chromium/third_party/ffmpeg.git/+/master/CREDITS.chromium).
