# Arch package: `arkade-cli-bin`

Installs the official prebuilt **`ark`** CLI from [arkade-os/arkd releases](https://github.com/arkade-os/arkd/releases) as `/usr/bin/ark`.

This directory lives in the fork [theDavidCoen/arkade-cli](https://github.com/theDavidCoen/arkade-cli) of [arkade-os/cli](https://github.com/arkade-os/cli).

## Warning

Experimental wallet software. **You may lose funds.** Do not store meaningful funds. Use at your own risk.

## Build / install

```bash
cd packaging/arch
makepkg -si
```

Requires network to download the release binary. Supports `x86_64` and `aarch64`.

## Omarchy widget `requires`

```owl
requires { pacman: ["arkade-cli-bin"] }
```

Then call e.g. `cmd("ark receive")` / `cmd("ark balance")` (JSON stdout).

## Mutinynet quick start

```bash
ark --datadir ~/.ark-cli-mutiny init \
  --password 'choose-a-password' \
  --server-url https://mutinynet.arkade.sh \
  --explorer https://mutinynet.com/api

ark --datadir ~/.ark-cli-mutiny receive
ark --datadir ~/.ark-cli-mutiny balance
```

Spends need the password (`--password` or interactive prompt).

## Bump version

1. Set `pkgver` to the new [arkd](https://github.com/arkade-os/arkd/releases) tag (without `v`).
2. Refresh `sha256sums_*` for `ark-linux-amd64` / `ark-linux-arm64`.
3. Bump `pkgrel` to `1` (or increment if same upstream tag).
