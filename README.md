# Mac Programmer's Setup Notes

## 1. Install the Latest Command Line Tools

``` bash
xcode-select --install
softwareupdate --all --install --force
```

---

## 2. Install Homebrew

First,

``` bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After downloading, add homebrew to your path

``` bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/ccm/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Then open a new terminal, and check the installation with:

``` bash
brew doctor
```

---

## Install the latest version of Git

``` bash
brew update
brew install git
```

## Install Github Command Line Tools (if you use Github)

First,

``` bash
brew update
brew install gh
gh auth login
```

then follow the instructions to login to Gihub.com and authenticate your computer.

---

## Config your git user.name and user.email

``` bash
git config --global user.name "Mona Lisa"
git config --global user.email mona.lisa@gmail.com
```

---

## Install Oh My Zsh

``` bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Some plugins I like:

1. [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#oh-my-zsh)

    ``` bash
    git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
    ```

2. [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md)

    ``` bash
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    ```

---

## Install Pyenv and Python

First,

``` bash
brew update
brew install pyenv
```

 Then update your zsh config files

``` bash
echo "alias brew='env PATH="${PATH//$(pyenv root)\/shims:/}" brew'" >> ~/.zshrc
echo 'eval "$(pyenv init --path)"' >> ~/.zprofile
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

Install libraries required to install python

``` bash
brew install openssl readline sqlite3 xz zlib
```

To see the versions of Python that can be installed,

``` bash
pyenv install -l
```

Choose the version you want, for example 3.9.9, and install it

``` bash
pyenv install 3.9.9
```

Create a new terminal window, and check your installation

``` bash
python --version
```

---

## Setup a Python Virtual Environment

``` bash
pip install -U pip
pip install virtualenv
mkdir .virtualenvs
virtualenv env_name
```

I like to add an alias to .zshrc to activate my virtual environment e.g.,

```bash
alias activate='source /home/.virtualenvs/env_name/bin/activate'
```

---

## Install Visual Studio Code

download the release version [here](https://code.visualstudio.com/)

or get the insiders version [here](https://code.visualstudio.com/insiders/)
