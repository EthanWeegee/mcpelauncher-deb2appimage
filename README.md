# mcpelauncher-deb2appimage
Config for deb2appimage to create an AppImage for the Linux Minecraft: Bedrock Edition launcher

This config file is to be used with [deb2appimage](https://github.com/simoniz0r/deb2appimage), to make a working AppImage of the [MCPE Linux launcher](https://github.com/minecraft-linux/mcpelauncher-manifest) from the prebuilt `.deb`s in the Ubuntu repository.

---

### Instructions to create AppImage
- Download the `config.json` you want to use. `config-xenial.json` uses the xenial packages to build the AppImages, while `config-bionic.json` uses the bionic packages to build the AppImage. You can *probably* use the bionic AppImage, but if that doesn't work, try xenial.
- Download `mcpelauncher-ui-qt.startme` and keep it in the same directory as the `config.json` file. If you don't want Xbox Live support with `msa-daemon` and `msa-ui-qt`, you can skip this step and see the [Note](#note) below.
- Visit [the Ubuntu repository](http://mcpelauncher.mrarm.io/apt/ubuntu/) and locate the `.deb`s in `pool/main/m` [(Link)](http://mcpelauncher.mrarm.io/apt/ubuntu/pool/main/m/)
- Under each of these four directories, make sure the filename is the same as in `config.json`. If not, copy the link of the `.deb` and paste it in `config.json` over the old one.
  - You can optionally change `"version": "20191030",` to the date the `.deb` lists in the file name. This makes it easier to keep track of what version of the launcher you have.
- Download [the latest release of deb2appimage](https://github.com/simoniz0r/deb2appimage/releases/latest). Mark it as executable if it isn't already.
- In a terminal, run `/path/to/deb2appimage.AppImage -j /path/to/config.json`. You can optionally specify an output directory with ` -o ./`. If you don't do this, the output AppImage will be in your $HOME directory.
- Mark the output AppImage as executable and run it!

#### Note
The build config is configured to bundle the `msa-daemon` and `msa-ui-qt` which are required for Xbox Live play. If you don't want these, you can remove the lines to download it from the `prerun` section. You then need to change

`"binarypath": "/usr/bin/mcpelauncher-ui-qt.startme"` to `"binarypath": "/usr/bin/mcpelauncher-ui-qt"`

in the `buildinfo` section and change

`"exec": "/usr/bin/mcpelauncher-ui-qt.startme.wrapper"` to `"exec": "/usr/bin/mcpelauncher-ui-qt.wrapper"`

in the `apprunconf` section.
