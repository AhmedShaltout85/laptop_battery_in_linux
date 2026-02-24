# 🖥️ Modern Linux Terminal Tools

أفضل الأدوات الحديثة للطرفية في لينكس — تجعل تجربتك أسرع، أوضح، وأكثر احترافية!

---

## 📦 Update System

```bash
sudo apt update
sudo apt upgrade
```

---

## 🐱 bat – Modern `cat` with Syntax Highlighting

### Install
```bash
sudo apt install bat
```

### Setup
```bash
mkdir -p ~/.local/bin/
ln -s /usr/bin/batcat ~/.local/bin/bat
```

---

## 💾 duf – Disk Usage / `df` Replacement

### Install
```bash
sudo apt install duf
```

---

## 📂 eza – Modern `ls` Replacement

### Install
```bash
sudo apt install eza
```

> Or via official repository (recommended for latest version):

```bash
sudo mkdir -p /etc/apt/keyrings \
&& wget -qO- https://raw.githubusercontent.com/eza-community/eza/main/deb.asc | sudo gpg --dearmor -o /etc/apt/keyrings/gierens.gpg \
&& echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/gierens.gpg] http://deb.gierens.de stable main" | sudo tee /etc/apt/sources.list.d/gierens.list \
&& sudo chmod 644 /etc/apt/keyrings/gierens.gpg /etc/apt/sources.list.d/gierens.list \
&& sudo apt update \
&& sudo apt install -y eza
```

### Setup – Add aliases to `.bashrc`
```bash
grep -qxF "# eza alias" ~/.bashrc || {
  {
    echo ""
    echo "# eza alias"
    echo "alias ll='eza -lah --icons --group-directories-first'"
    echo "alias ls='eza --icons --group-directories-first'"
  } >> ~/.bashrc
}
```

> Additional useful aliases:
```bash
alias ls='eza --color=auto --icons=auto'
alias eza='eza --color=auto --icons=auto'
alias ll='eza -l'
alias la='eza -lah'
alias lt='eza -T'
```

---

## 📊 btop – Modern System Monitor (`htop` Replacement)

### Install
```bash
sudo apt install btop
```

---

## ⚡ fastfetch – System Info for Terminal (`neofetch` Replacement)

### Install
```bash
sudo apt install fastfetch
```

---

## 🗂️ dust – Human-Friendly Disk Usage (`du` Replacement)

### Install
```bash
sudo apt install du-dust
```

---

## 🚀 zoxide – Smart Directory Jumping

### Install
```bash
sudo apt install zoxide
```

### Setup – Initialize in shell
```bash
grep -qxF 'eval "$(zoxide init bash)"' ~/.bashrc >/dev/null || cat >> ~/.bashrc <<'EOF'

# zoxide setup
eval "$(zoxide init bash)"

EOF
```

---

## 🔍 fzf – Fuzzy Finder

### Install
```bash
sudo apt install git
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

### Setup – Add to shell config

**Bash:**
```bash
eval "$(fzf --bash)"
```

**Zsh:**
```bash
# Set up fzf key bindings and fuzzy completion
eval "$(fzf --zsh)"
```

---

## 🌟 starship – Modern, Fast Shell Prompt

### Install
```bash
sudo apt install starship
```

> Or via official install script:
```bash
curl -sS https://starship.rs/install.sh | sh
```

### Setup – Initialize in shell

**Bash:**
```bash
grep -qxF 'eval "$(starship init bash)"' ~/.bashrc >/dev/null || cat >> ~/.bashrc <<'EOF'

# starship setup
eval "$(starship init bash)"

EOF
```

**Zsh:**
```bash
echo 'eval "$(starship init zsh)"' >> ~/.zshrc
```

---

## 🎯 Bonus: fzf + zoxide → `zi`

Combines zoxide's smart ranking with fzf's interactive selection.

```bash
zi                  # interactive directory jump
z <partial-dir>     # jump instantly to most-used directory
```

---

## 🔤 Fonts – JetBrainsMono Nerd Font

```bash
mkdir -p ~/.local/share/fonts/JetBrainsMono
curl -sLO https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.tar.xz
tar -xvf JetBrainsMono.tar.xz -C ~/.local/share/fonts/JetBrainsMono
rm JetBrainsMono.tar.xz
fc-cache -fv ~/.local/share/fonts
fc-list | grep "JetBrains"
```

> Alternative one-liner:
```bash
mkdir -p ~/.local/share/fonts \
&& cd ~/.local/share/fonts \
&& curl -OL https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.tar.xz \
&& bash -c 'mkdir "${1%.tar.xz}" && tar -xf "$1" -C "${1%.tar.xz}"' _ JetBrainsMono.tar.xz \
&& rm JetBrainsMono.tar.xz \
&& fc-cache -fv
```

---

## 🛠️ Prerequisites

```bash
sudo apt update && sudo apt install gpg git curl
```

---

## 📚 References

- [NerdFonts](https://www.nerdfonts.com/)
- [Starship](https://starship.rs/)
- [fzf](https://github.com/junegunn/fzf)
- [eza](https://github.com/eza-community/eza)
- [bat](https://github.com/sharkdp/bat)
- [zoxide](https://github.com/ajeetdsouza/zoxide)
- [btop](https://github.com/aristocratos/btop)
- [dust](https://github.com/bootandy/dust)
- [fastfetch](https://github.com/fastfetch-cli/fastfetch)
- [duf](https://github.com/muesli/duf)
