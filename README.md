# Terminal Customization with ZSH and Oh-My-ZSH

Configuring a powerful, user-friendly terminal environment is essential for developer productivity. We can through setting up ZSH, installing Oh-My-ZSH, and enabling key plugins to improve our command-line workflow. This setup not only enhances command efficiency through features like autosuggestions and syntax highlighting, but also reduces the cognitive load required to recall complex commands. With customizable themes and plugin support, we can tailor the terminal to fit our personal workflow — even in a shared or remote computing environment like a cluster, making repetitive tasks faster and reducing friction during development. This guide walks through how to achieve this setup step-by-step in the cluster.

## Check ZSH Availability

On most clusters, ZSH may already be available. You can check with:

```bash
zsh --version
```

If this command returns a version number like `zsh 5.5.1 (x86_64-redhat-linux-gnu)`, ZSH is already installed and you can skip installation.

However, if ZSH is **not installed** and you have **sudo permissions**, you can install ZSH and common productivity plugins with:

```bash
sudo apt install zsh zsh-autosuggestions zsh-syntax-highlighting zsh-autocomplete
```

⚠️ On shared HPC clusters, you may not have sudo access. In that case, you can request installation from your system administrator. Alternatively, you can **compile and install Zsh into your own `$HOME` directory** without needing root access. For more detailed instructions, refer to the [official Zsh GitHub repository](https://github.com/zsh-users/zsh#installing-zsh).

## Change Your Default Shell (Bash) to ZSH

If your user has permissions, you just need to run:

```bash
chsh -s $(which zsh)
```

⚠️ On many shared clusters, you may not have `chsh` access. In that case, run manually after each login:

```bash
zsh
```

If you want to automatically enter Zsh every time you log in without changing the system’s default shell, you can add the following line to your `~/.bashrc`:

```bash
nano ~/.bashrc # open ~/.bashrc
exec zsh # add it at the end of the file, and do not modify anything inside the >>> conda initialize >>> block
# press `Ctrl+O` to save and `Ctrl+X` to exit
source ~/.bashrc # reload the terminal or run this command
```

## Install Oh-My-ZSH

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

This installs into `~/.oh-my-zsh/` and generates a `~/.zshrc`.

## Install Plugins

Clone the following plugins into ~/.oh-my-zsh/custom/plugins/:

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

## Enable Plugins in `.zshrc`

Open `.zshrc` and find:

```bash
plugins=(git)
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
source ~/.zshrc
```

## Enjoy the Experience

Once configured, you'll benefit from:

🚀 Command suggestions based on history

🖍️ Real-time syntax highlighting

⌨️ Tab completion and shortcuts

🧩 Easy theming and customization


