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
