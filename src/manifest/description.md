# `[description]`

Description contains short and long descriptions of the application.

Both short and long descriptions are used in the Snapcraft package as a summary (short) and description (long). Due to Snapcraft restrictions, short description must not be longer than 78 characters.

Windows resources use short description to define `FileDescription` property, visible in the explorer application property window.

Long description can be multiline.  The description section can be defined as follows:

```toml
[description]
short = "Neque porro quisquam est qui dolorem ipsum quia dolor sit amet..."
long = """
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod 
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, 
quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo 
consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse 
cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat 
non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
"""
```


