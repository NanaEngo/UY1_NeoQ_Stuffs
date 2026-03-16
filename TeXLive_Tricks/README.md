# 📄 TeXLive Tricks

TeXLive installation and configuration guides for Linux.

---

## Contents

| File | Description |
|------|-------------|
| [UY1_NeoQ_Install_TeXLive_Iso_Linux.md](UY1_NeoQ_Install_TeXLive_Iso_Linux.md) | Install TeXLive from ISO on Linux |
| [MyTL2022Linux.profile](MyTL2022Linux.profile) | Profile for command-line installation |
| [MYLinuxTeXstudio220910.txsprofile](MYLinuxTeXstudio220910.txsprofile) | TeXStudio configuration example |

---

## Quick Install

### 1. Mount ISO

```bash
sudo mount -o loop texlive2022.iso /mnt
```

### 2. Install (GUI)

```bash
cd /mnt
./install-tl -gui
```

### 3. Install (Command Line)

```bash
./install-tl --profile MyTL2022Linux.profile
```

### 4. Configure PATH

Add to `~/.bashrc`:
```bash
PATH=/usr/local/texlive/2022/bin/x86_64-linux:$PATH
export PATH
```

---

## TeXStudio Setup

1. Install: `sudo apt install texstudio`
2. Configure PATH in TeXStudio options
3. Verify: Help > Check LaTeX installation

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| `tlmgr: command not found` | Use `sudo env PATH="$PATH" tlmgr` |
| Missing packages | `tlmgr install <package>` |
| LanguageTool not working | Install Java: `sudo apt install openjdk-18-jre` |

---

## Resources

- [TeXLive Official](https://www.tug.org/texlive/)
- [TeXStudio](https://www.texstudio.org/)
- [LanguageTool](https://languagetool.org/)

---

*UY1 Néo Quanticiens – TeXLive Resources*
