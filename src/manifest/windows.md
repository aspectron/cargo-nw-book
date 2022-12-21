# `[windows]`

Windows section of the manifest contains Windows-specific definitions used by the interactive installer (InnoSetup)

Following properties must be set:
- `uuid`- a UUID string identifying the application in the windows registry.  This UUID is used by the installer during updates and the uninstall process.

- `group` - a string value containing the name of the Start menu folder in which the application should be placed. 

- `run_on_startup` - a string value containing one of the following two values: `"everyone"` and `"user"`.  If `"everyone"` is specified, the application will auto-start for any user login.  If `"user"` is specified, the application will auto-start only for the user that has installed the application.

- `run_after_setup` - a boolean value `true` or `false` indicating whether the interactive installer should offer the user to run the application after the completion of the installation.

- `resources` - contains a list of windows resource strings that should be included in the executable. For example, the following declaration will add `CompanyName` record set to the organization name and a custom resource value `NW Project` containing the application title: `
resources = [
    { CompanyName = "$ORGANIZATION" },
    { Custom = { name = "NW Project", value = "$TITLE" }},
]
`\
\
Winows resource strings and values can be arbitrary. The following list of resource names is considered to be standard on Windows:
    - `CompanyName`
    - `FileDescription`
    - `FileVersion`
    - `InternalName`
    - `LegalCopyright`
    - `LegalTrademarks`
    - `OriginalFilename`
    - `PrivateBuild`
    - `ProductName`
    - `ProductVersion`

Please note that `ProductName`, `ProductVersion`, `CompanyName`, `FileVersion`, `InternalName` are set automatically to match the properties specified in the `[application]` section.  Specifying them under the `[resources]` section will override the `[application]` section values.

