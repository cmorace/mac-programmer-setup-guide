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
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

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

## Install rbenv

``` bash
brew install rbenv
```

Check which ruby versions are available to install

``` bash
rbenv install -l 
```

Install ruby e.g.,

``` bash
rbenv install 3.0.3
rbenv global 3.0.3
echo 'eval "$(rbenv init - zsh)"' >> ~/.zshrc
```

start a new shell and check you have the right ruby version in your path

``` bash
ruby -v
```

---

## Install jekyll

``` bash
gem install --user-install bundler jekyll
```

if you get a path error, export the path e.g.,

``` bash
echo 'export PATH="/Users/ccm/.local/share/gem/ruby/3.0.0/bin:$PATH"' >> ~/.zshrc
```

create a new jekyll project to test everything is working

``` bash
gem install bundler jekyll
jekyll new my-awesome-site
cd my-awesome-site
bundle exec jekyll serve
# => Now browse to http://localhost:4000
```

If there is an error about `webrick`

``` bash
bundle add webrick
```

## Install Visual Studio Code

download the release version [here](https://code.visualstudio.com/)

or get the insiders version [here](https://code.visualstudio.com/insiders/)
