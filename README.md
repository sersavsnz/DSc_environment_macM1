# Setting up Data Science environment
Here I list steps for setting up working environment on my m1 macbook.

## Install devtools
Run in your terminal
```sh
python3
```
It will offer to install **devtools**.

## Xcode Command Line Tools
```sh
xcode-select --install
```

##  Homebrew
Homebrew is a system package manager. Follow the [installation instructions](https://brew.sh/). Now we can install software with Homebrew, so we start from the necessary dependencies
```sh
brew install openssl readline sqlite3 xz zlib tcl-tk
```

## Git
```sh
brew install git
```
```sh
# set the global credentials
it config --global user.name "xxx"
git config --global user.email xxx@gmail.com
```

## Zsh, Oh My Zsh and iterm2 terminal
Instal and customise **Zsh** shell (set by default on mac), [**Oh My Zsh**](https://github.com/ohmyzsh/ohmyzsh) and [**iterm2**](https://iterm2.com/features.html) terminal (click for advanced features such as autocompletion).
```sh
# install iterm2 as an macOS app 
brew install --cask iterm2
```
Open iterm2 and add it to your dock. One can customize some settings opening preferences. 

Install Oh My Zsh
``` sh
# install  Oh My Zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
``` 
We can [configure](https://medium.com/@slavadubrov/setting-up-a-macbook-as-data-science-specialist-8fee88c9c498) the terminal with a ~/.zshrc file. 
To add [plugins](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins) or change a theme correct the corresponding part in .zshrc file. 
The [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/) and [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) plugins need additional installation.
I'm using the [powerlevel10k](https://github.com/romkatv/powerlevel10k#homebrew) theme in Zsh. Check [here](https://gist.github.com/kevin-smets/8568070#powerlevel9k--powerlevel10k) and [here](https://github.com/romkatv/powerlevel10k/blob/master/font.md#manual-font-installation) to configure the VSCode terminal to work with the powerlevel10k theme.
```sh
# install powerlevel10k
brew install romkatv/powerlevel10k/powerlevel10k
echo "source $(brew --prefix)/opt/powerlevel10k/powerlevel10k.zsh-theme" >>~/.zshrc
```
Some useful features of iterm2:
- double tab let you select a folder
- looping over history with up arrow (when type some command like mkdir it will show only mkdir history)
- hot keys
    - Ctrl + U – delete from the cursor to the start of the line.
    - Ctrl + K – delete from the cursor to the end of the line.
    - Ctrl + W – delete from the cursor to the start of the preceding word.
    - Alt + D – delete from the cursor to the end of the next word.
    - Ctrl + L – clear the terminal.

## VS Code
For coding we use Visual Studio Code. Alternatively, PyCharm can be used. 
I switched to VS Code for a simple reason: it is lighter then PyCharm + can read Jupyter NB directly.
```sh
brew install --cask visual-studio-code
```

## Pyenv
For managing different versions of python I'm using [**pyenv**](https://github.com/pyenv/pyenv#homebrew-in-macos) -- see the documentation for installation and usage.
```sh
brew update
brew install pyenv  

echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
echo 'eval "$(pyenv init --path)"' >> ~/.zprofile

exec "$SHELL"
```

## PDM
To manage python dependencies I am using [PDM](https://pdm.fming.dev/latest/) - a modern Python package and dependency manager. It does not require installing a virtual environment as it follows PEP 582, it is simple and fast. Also watch the intro [video](https://www.youtube.com/watch?v=qOIWNSTYfcc) on how to use it in general and with vs code.
