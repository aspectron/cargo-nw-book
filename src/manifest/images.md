# `[images]`

Images section allows overriding default filenames for application icons.

NOTE: For Windows, application icon should be at least 512x512.  For MacOS the application icon should be at 1024x1024 and preferably follow Apple design guidelines (you can download MacOS icon templates from [here](https://developer.apple.com/design/resources/#macos-apps))

`cargo-nw` will automatically resize icon images and convert their formats where needed and embed them into all appropriate resources and application manifests.

### Default image filenames

When searching for application icons, `cargo-nw` will search the resource files for the following images:

For application icon:
- `<platform>-application.png`
- `application.png`
- `default-application-icon.png`

For document icon:
- `<platform>-application.png`
- `application.png`
- `default-application-icon.png`

For DMG:
- `macos-disk-image-backgroun.png`

For InnoSetup icon:
- `innosetup.png`
- `windows-application.png`
- `application.png`
- `default-application-icon.png`

For InnoSetup Wizard Large Image:
- `innosetup-wizard-large.png`

For InnoSetup Wizard Small Image:
- `innosetup-wizard-small.png`

### Overriding image filenames

To change default filenames, you can specify the following properties under the `[images]` section.  Please note that property names provide OS-specific overides with a fallback to default icons.

All images should be in the PNG format.

- `document` - document icon (fallback)
- `windows-document` - windows-specific document icon
- `linux-document` - linux-specific document icon
- `macos-document` - macos-specific document icon
- `application` - application icon (fallback)
- `windows-application` - windows-specific application icon
- `linux-application` - linux-specific application icon
- `macos-application` - macos-specific application icon
- `macos-disk-image` - DMG background image
- `innosetup-icon` - InnoSetup (fallback is the `windows-application`, followed by `application`)
- `innosetup-wizard-small` - InnoSetup Small Wizard Image
- `innosetup-wizard-large` - InnoSetup Large Wizard Image

