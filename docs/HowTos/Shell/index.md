---
layout: single
title: Shell
toc: ture
---

# Linux
[from Oh My Posh Web Side - manuel installation](https://ohmyposh.dev/docs/installation/linux)

```bash
sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
sudo chmod +x /usr/local/bin/oh-my-posh
```

## Download Theams
[from Oh My Posh Web Side - manuel installation](https://ohmyposh.dev/docs/installation/linux)
```bash
mkdir ~/.poshthemes
wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/themes.zip -O ~/.poshthemes/themes.zip
unzip ~/.poshthemes/themes.zip -d ~/.poshthemes
chmod u+rw ~/.poshthemes/*.omp.*
rm ~/.poshthemes/themes.zip
```

## Add Bash
[from Oh My Posh Web Side](https://ohmyposh.dev/docs/installation/prompt)
```bash
vi ~/.bashrc 
```
add this statement for the std theme
> eval "$(oh-my-posh init bash)"
or this statement with a specifi thema
> eval "$(oh-my-posh init bash  --config ~/.poshthemes/blue-owl.omp.json)"

# Windows
```cmd
notepad $PROFILE
```