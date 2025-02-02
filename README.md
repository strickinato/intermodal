# intermodal: a 40' shipping container for the Internet

[![Crate](https://img.shields.io/crates/v/imdl.svg?logo=rust)](https://crates.io/crates/imdl)
[![Build](https://github.com/casey/intermodal/workflows/Build/badge.svg)](https://github.com/casey/intermodal/actions)
[![Book](https://img.shields.io/static/v1?logo=read-the-docs&label=book&message=imdl.io&color=informational)](https://imdl.io/book/)
[![Chat](https://img.shields.io/discord/679283456261226516.svg?logo=discord&color=7289da)](https://discord.gg/HaaT5Qz)

Intermodal is a user-friendly and featureful command-line BitTorrent metainfo utility. The binary is called `imdl` and runs on Linux, Windows, and macOS.

At the moment, creation, viewing, and verification of `.torrent` files is supported.

For more about the project and its goals, check out [this post](https://rodarmor.com/blog/intermodal).

![demonstration animation](https://raw.githubusercontent.com/casey/intermodal/master/www/demo.gif)

## Manual

- [General](#general)
  - [Installation](#installation)
    - [Supported Operating Systems](#supported-operating-systems)
    - [Packages](#packages)
    - [Pre-built binaries](#pre-built-binaries)
    - [Cargo](#cargo)
  - [Shell Completion Scripts](#shell-completion-scripts)
  - [Semantic Versioning](#semantic-versioning)
  - [Unstable Features](#unstable-features)
  - [Source Signatures](#source-signatures)
- [Acknowledgments](#acknowledgments)

## General

### Installation

#### Supported Operating Systems

`imdl` supports Linux, MacOS, and Windows, and should work on other unix OSes.
If it does not, please open an issue!

#### Packages

| Operating System                                                     | Package Manager                     | Package                                                                   | Command              |
|:--------------------------------------------------------------------:|:-----------------------------------:|:-------------------------------------------------------------------------:|---------------------:|
| [Various](https://forge.rust-lang.org/release/platform-support.html) | [Cargo](https://www.rust-lang.org)  | [imdl](https://crates.io/crates/imdl)                                     | `cargo install imdl` |
| [Arch Linux](https://www.archlinux.org)                              | [Yay](https://github.com/Jguer/yay) | [intermodal](https://aur.archlinux.org/packages/intermodal)<sup>AUR</sup> | `yay -S intermodal`  |

#### Pre-built binaries

Pre-built binaries for Linux, macOS, and Windows can be found on
[the releases page](https://github.com/casey/intermodal/releases).

You can use the following command to download the latest binary for Linux,
MacOS, or Windows, just replace `DEST` with the directory where you'd like to
install the `imdl` binary:

```sh
curl --proto '=https' --tlsv1.2 -sSf https://imdl.io/install.sh | bash -s -- --to DEST
```

A good place to install personal binaries is `~/bin`, which `install.sh` uses
when `--to` is not supplied. To create the `~/bin` directory and install `imdl`
there, do:

```sh
curl --proto '=https' --tlsv1.2 -sSf https://imdl.io/install.sh | bash
```

Additionally, you'll have to add `~/bin` to the `PATH` environment variable,
which the system uses to find executables. How to do this depends on the shell.

For `sh`, `bash`, and `zsh`, it should be done in `~/.profile`:

```sh
echo 'export PATH=$HOME/bin:$PATH' >> ~/.profile
```

For `fish`, it should be done in `~/.config/fish/config.fish`:

```fish
echo 'set -gx PATH ~/bin $PATH' >> ~/.config/fish/config.fish
```

#### Cargo

`imdl` is written in [Rust](https://www.rust-lang.org/) and can be built from
source and installed with `cargo install imdl`. To get Rust, use the
[rustup installer](https://rustup.rs/).

### Shell Completion Scripts

Shell completion scripts for Bash, Zsh, Fish, PowerShell, and Elvish are
available in the [completions](completions directory). Please refer to your
shell's documentation for how to install them.

The `imdl` binary can also generate the same completion scripts at runtime,
using the `completions` command:

```sh
$ imdl completions --shell bash > imdl.bash
```

### Semantic Versioning

Intermodal follows [semantic versioning](https://semver.org/).

In particular:

- v0.0.X: Breaking changes may be introduced at any time.
- v0.X.Y: Breaking changes may only be introduced with a minor version number
  bump.
- vX.Y.Z: Breaking changes may only be introduced with a major version number
  bump

### Unstable Features

To avoid premature stabilization and excessive version churn, unstable features
are unavailable unless the `--unstable` / `-u` flag is passed, for example
`imdl --unstable torrent create .`. Unstable features may be changed or removed
at any time.

### Source Signatures

All commits to the intermodal master branch signed with Casey Rodarmor's PGP
key with fingerprint `3259DAEDB29636B0E2025A70556186B153EC6FE0`, which can be
found
[on keybase](https://keybase.io/rodarmor/pgp_keys.asc?fingerprint=3259daedb29636b0e2025a70556186b153ec6fe0) and on
[his homepage](https://rodarmor.com/static/rodarmor.asc).

## Acknowledgments

The formatting of `imdl torrent show` is entirely copied from
[torf](https://github.com/rndusr/torf-cli), an excellent command-line torrent
creator, editor, and viewer.
