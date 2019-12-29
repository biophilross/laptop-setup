# Laptop setup

Instructions for setting up new or factory reset laptops

---

This assumes that you are using a Macbook running maxOS.

## Install XCode

	xcode-select --install

## Install XQuartz

http://www.xquartz.org/

## Install Homebrew

	http://brew.sh/
	/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
	sudo chown $USER /usr/local
	brew doctor && brew update

## Install Git

	brew install git
	# use keychain to remember username and password
	git config --global credential.helper osxkeychain
	git config --global user.name “pzross”
	git config --global user.email “philippzross@gmail.com"
	git config --global core.editor vim

## Terminal Setup

Dotfiles:

	git clone https://github.com/pzross/dotfiles $HOME/.dotfiles
	cd $HOME/.dotfiles
	bash setup.sh osx

Settings:

Profile: Basic
Cursor: Red, Blink cursor
Font: Source Code Pro 13 pt. character spacing 0.85 line spacing 0.9
Keyboard: uncheck Scroll alternate screen
Advanced: Uncheck paste newlines as carriage returns, audible bell, only whens sound is muted

## Brew Installs

See dotfiles github repo `start_brewing.sh` for more details

Setting up miniconda

	wget https://repo.continuum.io/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
	bash Miniconda3-latest-MacOSX-x86_64.sh -b -p $HOME/.miniconda3

	conda config --add channels conda-forge
	conda config --add channels defaults
	conda config --add channels r
	conda config --add channels bioconda

## Install Sketch

https://www.sketchapp.com/

## Setup R

Install Bioconductor packages:

Do this first so you can uncomment the loading of Biocinstaller in the .Rprofile

	source("https://bioconductor.org/biocLite.R")
	biocLite(ask=F)

Install CRAN packages:

	install.packages(c("readr", "tidyr", "dplyr", "magrittr", "ggplot2", "cowplot", "docopt", "devtools”))
	devtools::install_github("jalvesaq/colorout")

Install my packages

	devtools::install_github("thephilross/iver")

Restart your computer!

## Rename Google Drive Folder

1. Quit Google Drive app.
2. Rename “~/Google Drive/” to whatever you want.
3. Open Google Drive and wait for it to complain the folder is missing.
4. Click the menu item and click the warning item.
5. Click “Locate Folder..” button on the right in window that pops up.
6. Find your renamed folder and hit OK.

## Install MacTEX

http://www.tug.org/mactex/mactex-download.html

## Installing Docker

	brew install docker docker-machine
	brew cask install virtualbox
	-> need password
	-> possibly need to address System Preference setting
	docker-machine create --driver virtualbox default
	docker-machine env default
	eval "$(docker-machine env default)"
	docker run hello-world
	docker-machine stop default
