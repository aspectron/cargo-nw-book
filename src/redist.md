# Registributables

## InnoSetup

To build InnoSetup interactive installation redistributables, you need to download and install InnoSetup on your build system.

- [InnoSetup Download](https://jrsoftware.org/isdl.php)
- [InnoSetup Help](https://jrsoftware.org/ishelp/index.php)

## DMG

DMG builds do not require any additional tooling as DMG generation relies on the `hdiutil` included with MacOS.

## Snap

- [SnapCraft Home](https://snapcraft.io/install/snapcraft/ubuntu)
- [LXD Home](https://linuxcontainers.org/lxd/getting-started-cli/) 

Snap requires snapcraft to be installed on the linux operating system.

```bash
sudo apt install libssl-dev
sudo snap install snapcraft
sudo snap install lxd
sudo adduser <username> lxd
sudo service snap.lxd.daemon restart
# you may need to restart the system
```

When creating SNAP files, to install them locally you need to run:
```bash
# when building with `strict` containment
snap install --dangerous <yourfile>.app
# when building with `clssic` containment
snap install --dangerous --classic <yourfile>.app
```
