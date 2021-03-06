# Ubuntu 14.04 Configuration

## 1. Default Application Install

```
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install git wget curl ssh xclip

$ # register ssh key on Github
$ # install chrome dropbox
```

### 1.1 vim

####  Vim source build

see https://github.com/Valloric/YouCompleteMe/wiki/Building-Vim-from-source
<br/>
```
cp dotfiles/.vimrc ~/.vimrc
```

#### vundle
```
$ git clone https://github.com/gmarik/vundle.git ~/.vim/bundle/Vundle.vim
```

#### vim-powerline

see http://askubuntu.com/questions/283908/how-can-i-install-and-use-powerline-plugin

### 1.2 System Monitoring Tools

```
$ sudo apt-get htop ncdu
```

### 1.3 Productivity

```
# Autojump
$ sudo apt-get autojump # and edit .zshrc to add plugin

# Shutter
$ sudo apt-get install libnet-dbus-glib-perl libimage-exif-perl
$ sudo add-apt-repository ppa:shutter/ppa
$ sudo apt-get update
$ sudo apt-get install shutter
$ # add alias shutter as cap

# go
$ # download go bin
$ tar -C /usr/local -xzf go1.3.linux-amd64.tar.gz
$ mkdir ~/.go


# ghq
$ go get github.com/motemen/ghq 
# peco
$ go get github.com/peco/peco/cmd/peco
```

### 1.4 Git extensions

- git-flow
- git extras
- hub

### 1.5 Geeknote

[Geeknote](http://www.webupd8.org/2014/09/geeknote-command-line-evernote-client.html)

<br>
## 2. Appearance Setting

### 2.1 Font
```
sudo apt-get install unity-tweek-tool
```

### 2.2 Appearance
```
enable workspace
autoi hide launcher on
launcher icon size : 40
```

### 2.3 Brightness & Lock
```
Turn screen off when inactive for : 10 minutes
```

### 2.4 Shell : ZSH
```
$ sudo apt-get install zsh
$ curl -L http://install.ohmyz.sh | sh
```
<br>
Ref : [Here](http://www.unixmen.com/install-oh-zsh-ubuntu-arch-linux-fedora/)

#### zsh plugin : compleat

Background : https://github.com/mbrubeck/compleat

```
$ sudo apt-get install haskell-platform
$ git clone git://github.com/mbrubeck/compleat.git

$ ./Setup.lhs configure
$ ./Setup.lhs build
$ sudo ./Setup.lhs install
$ udo mkdir /etc/compleat.d
$ sudo cp examples/* /etc/compleat.d
```

#### zsh plugin : git-extras

See : https://github.com/visionmedia/git-extras

```
$ (cd /tmp && git clone --depth 1 https://github.com/visionmedia/git-extras.git && cd git-extras && sudo make install)
```

#### zsh plugin : grunt

See : https://github.com/yonchu/grunt-zsh-completion

```
$ cd ~/.oh-my-zsh/custom/plugins
$ git clone https://github.com/yonchu/grunt-zsh-completion.git grunt
```

### 2.5 Solarzied Terminal
```
$ wget --no-check-certificate https://raw.github.com/seebi/dircolors-solarized/master/dircolors.ansi-dark
$ mv dircolors.ansi-dark .dircolors

$ git clone https://github.com/sigurdga/gnome-terminal-colors-solarized.git
$ cd gnome-terminal-colors-solarized
$ ./set_dark.sh

$ cp dotfiles/.zshrc ~/
```
<br>
Ref : [Here](http://www.webupd8.org/2011/04/solarized-must-have-color-paletter-for.html)

### 2.6 tmux
```
$ sudo apt-get install tmux
```

#### tmux-powerline

```
$ install tmux powerline see https://powerline.readthedocs.org/en/latest/installation/linux.html#installation-linux
$ cp dotfiles/.tmux.conf ~/
```

#### tmuxinator

```
$ gem install tmuxinator
$ tmuxinator doctor 
$ ln -s ~/Dropbox/dotfiles/.tmuxinator ~/
```

<br>
## 3. Key

### 3.1 Default Key Configuration
```
super + del -> gnome-system-monitor (Custom)
super + e -> Home Folder (in Launchers)
shift + alt + d -> hud (in Launchers)
right alt -> compose key (in Typing)
Use compose key as input source switcher (in Typing)
```

### 3.2 Capslock as ESC
```
$ sudo apt-get install gnome-tweak-tool
gnome-tweak-tool > Typing > Make Caps Lock an additional ESC
```

<br>
## 4. Korean
```
Language Supoort -> install Korean
Text Entry -> add Korean(Hangul) in Input source 
```
<br>
### 4.1 한글 짤림 문제 (Optional)
```
sudo add-apt-repository -y ppa:jincreator/freetype && sudo apt update && sudo apt install -y libfreetype6

```

<br>
## 5. Development Environment

### Node.js

- nvm

### 5.2 MongoDB
```
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
$ echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list
$ sudo apt-get update
$ sudo apt-get install mongodb-org
$ sudo service mongod start

$ # add admin user 
$ sudo vi /etc/mongodb.conf auth config
$ sudo service mongod restart
```

### 5.3 C++
```
$ sudo apt-get install gcc g++ make cmake autoconf libtool
```

### 5.4 Java 8, Scala

Java 8

```
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install oracle-java8-installer
$ sudo apt-get install oracle-java8-set-default

$ # export NODE_PATH=/usr/local/lib/jsctags/:$NODE_PATH
$ # export JAVA_HOME=/usr/lib/jvm/java-8-oracle
$
```

Scala

```
$ wget www.scala-lang.org/files/archive/scala-2.11.2.deb
$ sudo dpkg -i scala-2.11.2.deb

$ wget http://dl.bintray.com/sbt/debian/sbt-0.13.5.deb
$ sudo dpkg -i sbt-0.13.5.deb
```

### 5.5 Mysql 5.5
```
$ sudo apt-get install mysql
$ # install mysql workbench
```

### 5.6 Spring
```
$ # get STS 
$ tar -zxvf sts
$ sudo mv sts-bundle /opt
$ cd /opt/sts-bundle/sts-3.5.1.RELEASE
$ sudo ln -s /opt/sts-bundle/sts-3.5.1.RELEASE/STS /usr/local/bin/sts

$ sudo vi /usr/share/applications/sts.desktop

[Desktop Entry]
Name=sts
Exec=/usr/local/bin/sts
Terminal=false
StartupNotify=true
Icon=/opt/eclipse/icon.xpm
Type=Application

$ # add extentions vrapper, color-theme, gradle support
$ # set emacs key binding as default key
```

gvm, springboot

```
$ curl -s get.gvmtool.net | bash
$ $ gvm install springboot
$ spring --version
Spring Boot v1.2.0.BUILD-SNAPSHOT
```

### 5.8 Emacs

(1) install

[Emacs 24.4 installation](http://askubuntu.com/questions/437255/how-to-install-emacs-24-4-on-ubuntu)

(2) configure

See : https://github.com/ansterd/emacs-linux/

### 5.9 Git

```
$ dotfiles/.gitconfig ~/
```

Ref1 : http://durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/  
Ref2 : http://oli.jp/2012/git-powerup/

### 5.10  vim

VIM Configuration using **vundle** as package management tool

#### Packages

- surround.vim
- matchit

### 5.11 Python

- [pyenv](https://github.com/yyuu/pyenv)
- [pyenv-virtualenv](https://github.com/yyuu/pyenv-virtualenv)
- [autoenv](https://github.com/kennethreitz/autoenv)

#### Ipython

See http://blog.safaribooksonline.com/2013/12/12/start-ipython-notebook/

```
sudo pip install jinja2 tornado pyzmq
sudo pip install ipython[all] # in bash
sudo apt-get install liblapack-dev libatlas-dev python-dev gfortran
sudo pip install numpy sympy matplotlib scipy pandas
```

#### Python3

```
sudo apt-get install python3-pip
sudo pip3 install matplotlib
```

### 5.12 Ruby

See https://gorails.com/setup/ubuntu/14.04

### 5.13 SML

```
$ sudo apt-get install gcc-multilib g++-multilib
$ ;; Installation Guide: http://www.smlnj.org/
```

### 5.14 Haskell

1. install Haskell Platform. See [here](http://www.haskell.org/platform/linux.html)  

2. install cabal See [here](http://www.haskell.org/haskellwiki/Cabal/How_to_install_a_Cabal_package) 

### 5.15 R

[References](http://www.korecky.org/?p=1254)

1. Install R

`$sudo vi /etc/apt/sources.list.d/r-base.list`

paste these lines into thefile

```
# R-Base repository
deb http://mirrors.nic.cz/R/bin/linux/ubuntu trusty/
```

import repository signature

`$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9`

update and install

```
$ sudo apt-get update
$ sudo apt-get install r-base r-base-dev r-cran-rjava r-cran-xml libxml2-dev
```

2. Install R studio

Download and install R studio from [here](http://www.rstudio.com/products/rstudio/download/)

## 6. Ghost

Install `buster`

```
# ref : http://seoh.github.io/ghost-to-gh-pages/index.html

git clone https://github.com/seoh/buster.git && cd buster  
sudo python setup.py install  
```

Get `gen-sitemap.sh' to generate Ghost sitemap from [Here](https://gist.github.com/vbtechsupport/7094343)

Set `.zshrc`

```
alias busg='buster generate --domain=http://127.0.0.1:2368 --dir=~/Dropbox/Blog/1ambda.github.io' --base='http://1ambda.github.io'
alias busm='/home/anster/Dropbox/Blog/ghost-tools/gen-sitemap.sh'
alias busd='buster deploy --dir=~/Dropbox/Blog/1ambda.github.io'  
```

Install Ghost see [Velox](https://github.com/1ambda/velox)


