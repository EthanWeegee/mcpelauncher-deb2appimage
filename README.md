# mcpelauncher-deb2appimage
Config for deb2appimage to create an AppImage for the Linux Minecraft: Bedrock Edition launcher

This config file is to be used with [deb2appimage](https://github.com/simoniz0r/deb2appimage), to make a working AppImage of the [MCPE Linux launcher](https://github.com/minecraft-linux/mcpelauncher-manifest) from the prebuilt `.deb`s in the Ubuntu repository.

---

### Instructions to create AppImage
- Visit [the Ubuntu repository](http://mcpelauncher.mrarm.io/apt/ubuntu/) and locate the `.deb`s in `pool/main/m` [(Link)](http://mcpelauncher.mrarm.io/apt/ubuntu/pool/main/m/)
- Under each of these four directories, make sure the file link is the same as the corresponding link in `config.json`. If not, copy the link of the `~xenial` file and paste it in `config.json` over the old one.
  - You can optionally change `"version": "20190729",` to the date the `.deb` lists in the file name.
- Download [the latest release of deb2appimage](https://github.com/simoniz0r/deb2appimage/releases/latest). Mark it as executable if it isn't already.
- In a terminal, run `/path/to/deb2appimage.AppImage -j /path/to/config.json`. You can optionally specify an output directory with ` -o ./`. If you don't do this, the output will be in your $HOME directory.
- Mark the output AppImage as executable and run it!

#### Note
The `config.json` is configured to bundle the `msa-daemon` and `msa-ui-qt` which are required for Xbox Live play. If you don't want these, you can remove the lines to download it from the `prerun` section. You then need to change

`"binarypath": "/usr/bin/mcpelauncher-ui-qt.startme"` to `"binarypath": "/usr/bin/mcpelauncher-ui-qt"`

in the `buildinfo` section and change

`"exec": "/usr/bin/mcpelauncher-ui-qt.startme.wrapper"` to `"exec": "/usr/bin/mcpelauncher-ui-qt.wrapper"`

in the `apprunconf` section.
