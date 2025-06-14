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

If you want to automatically enter Zsh every time without changing the system’s default shell, you can add the following line:

```bash
nano ~/.bashrc # open ~/.bashrc
exec zsh # add it at the end of the file, and do not modify anything inside the >>> conda initialize >>> block
# press `Ctrl+O` to save and `Ctrl+X` to exit
source ~/.bashrc # reload the terminal or run this command
```

## Install Oh-My-ZSH

To enhance ZSH experience, we can install Oh-My-ZSH — a popular open-source framework that makes ZSH more powerful and user-friendly. It can help us to customize the shell with themes and also add plugins for features like auto-suggestions and syntax highlighting.

Install it with:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Install Plugins

Then we can install plugins to supercharge ZSH experience, and it's highly recommended to install the following Oh-My-ZSH plugins. These plugins improve command-line productivity by adding intelligent suggestions, syntax highlighting, and autocomplete features.

- **zsh-autosuggesions plugin**: Shows command suggestions based on your command history as you type.

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions.git $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

- **zsh-syntax-highlighting plugin**: Adds color to your command line input, highlighting valid and invalid commands in real time.

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

- **zsh-fast-syntax-highlighting plugin**: A faster implementation of syntax highlighting for large command lines.

```bash
git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
```

- **zsh-autocomplete plugin**: Provides real-time autocompletion as you type, including fuzzy matching and suggestions.

```bash
git clone --depth 1 -- https://github.com/marlonrichert/zsh-autocomplete.git $ZSH_CUSTOM/plugins/zsh-autocomplete
```

## Enable Plugins in .zshrc

Once the desired plugins are successfully cloned, the next step is to enable them by editing `.zshrc` configuration file. This ensures that ZSH will load these plugins every time a new shell session starts.

```bash
# open `.zshrc`
nano ~/.zshrc

# find the line which says `plugins=(git)` and replace that line with:
plugins=(
 git
 zsh-autosuggestions
 zsh-syntax-highlighting
 fast-syntax-highlighting
 zsh-autocomplete
)

# press `Ctrl+O` to save and `Ctrl+X` to exit

# reload your environment to make changes work
source ~/.zshrc
```

## Customize ZSH Theme

After enabling useful plugins, we can also customize the appearance of the terminal by changing the theme. It provides many built-in themes and by default, the theme is set to `robbyrussell`, but we can switch to another one such as `alanpeabody`, `agnoster`, or `bureau`:

- `robbyrussell`: Default theme. Shows current directory and Git branch. Clean and classic.
- `alanpeabody`: Displays Git status icons with a minimalist style.
- `agnoster`: Visually enhanced. Requires Powerline fonts. Shows path, Git, and status.
- `bureau`: Rich in information. Displays username, path, Git branch, time, and more.

```bash
# open `.zshrc`
nano ~/.zshrc

# find the line `ZSH_THEME="robbyrussell"` and replace that line with:
ZSH_THEME="alanpeabody"

# press `Ctrl+O` to save and `Ctrl+X` to exit
```

## Enjoy the Experience

Once configured, you'll benefit from:

🚀 Command suggestions based on history

🖍️ Real-time syntax highlighting

⌨️ Tab completion and shortcuts

🧩 Easy theming and customization


