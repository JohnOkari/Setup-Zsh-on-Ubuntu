# **Setup Zsh on Ubuntu — One Page Guide**

This guide walks you through installing **Zsh**, setting it as your default shell, adding **Oh My Zsh**, themes, and useful plugins — start to finish.

---

## **1. Install Zsh**

```bash
sudo apt update && sudo apt install -y zsh
zsh --version
```

---

## **2. Make Zsh Default**

```bash
chsh -s $(which zsh)
```

> Log out and back in, or restart your terminal.

---

## **3. Install Oh My Zsh**

```bash
sudo apt install -y curl git
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

## **4. Install Plugins**

```bash
# Autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# Syntax Highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

---

## **5. (Optional) Install Powerlevel10k Theme**

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Set in `~/.zshrc`:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

---

## **6. Edit `~/.zshrc`**

Open with:

```bash
nano ~/.zshrc
```

Example plugin list:

```bash
plugins=(git z zsh-autosuggestions)
```

Add syntax highlighting **last**:

```bash
source ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

---

## **7. Reload Config**

```bash
source ~/.zshrc
```

---

## **8. Test**

* Open new terminal → Zsh prompt appears.
* Type part of a command → **autosuggestions** appear.
* Typo in command → **syntax highlighting** alerts you.

---

## **Troubleshooting**

* `chsh: shell not changed` → Ensure `which zsh` is in `/etc/shells`:

```bash
echo $(which zsh) | sudo tee -a /etc/shells
```

* Weird Powerlevel10k symbols → Use a Nerd Font in terminal settings.
* Return to bash:

```bash
chsh -s $(which bash)
```

---

✅ **Done!** You now have a customized, faster, and more powerful terminal.

---
