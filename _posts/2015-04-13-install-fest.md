---
layout: post
title: "Install Fest!!!"
tags:
- installation
- mac os x
- set up
- workflow
permalink: install-fest
comments: true
---

I'm in the middle of a super long post about Rails models. It is quite involved and is taking a long time to write. So in the meantime, I present you with this relatively shorter blog post composed of mostly links.

I recently got a new MacBook Pro! So I spent a day installing and setting up my system for the perfect workflow. I experimented with different set ups, and ended up installing and un-installing several things. Also sometimes I'd install something, and realize I had to install something else first, etc. So here I will try to just show you how I would do it if I had to do it again, without all the mistakes.

### The Terminal and the Shell
* install [iTerm](http://iterm.sourceforge.net/index.shtml)
* install [Oh My ZSH](http://ohmyz.sh/) because it's really cool looking!
  * move existing .bashrc content to .zshrc
  * move existing .bash_profile content to .zprofile
  * selectively add some of these [shell aliases](http://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html)

### Get ALL OF THE PACKAGE MANAGERZZZ!
* haha j/k, there are so many that it's confusing. I'll try to explain...
  * apt-get is a package manager for linux (don't need for my Mac--use homebrew instead)
  * [homebrew](http://brew.sh/) is a package manager for osx (the command is just `brew`)
  * [rubygems](https://github.com/rubygems/rubygems) is a package manager for ruby (the command is `gem`)
  * [npm](https://www.npmjs.com/package/npm) is a package manager for JavaScript, you'll need to install [node.js](https://nodejs.org/download/) first
  * [bower](http://bower.io/) is a package manager for web packages (bootstrap, jquery, etc.)
* decidedly NOT package managers, but useful in some of the same ways:
  * [wget](https://www.gnu.org/software/wget/) can be used to download contents from FTP, HTTP and HTTPS (`brew install wget`)
  * [curl](http://curl.haxx.se/docs/manpage.html) is similar to wget, with [some differences](http://daniel.haxx.se/docs/curl-vs-wget.html). (comes with Mac, I think)

### tmux it up!
  * install tmux: [simple instructions](https://robots.thoughtbot.com/love-hate-tmux)
  * optionally [configure tmux based on this gist](https://gist.github.com/snuggs/800936)
  * set up shell so that it [starts tmux by default](https://wiki.archlinux.org/index.php/Tmux#Start_tmux_on_every_shell_login)
  * [learn more](https://robots.thoughtbot.com/a-tmux-crash-course) about tmux

### Git, GitHub, etc.
* set up XCode and git (I just typed `git` and it asked me if I wanted to install XCode etc., so easy)
* generate [ssh key for github](https://help.github.com/articles/generating-ssh-keys/)
* added alias for [git hist](http://gitimmersion.com/lab_11.html) 
* optionally install [GitX](http://gitx.frim.nl/) or [Source Tree](http://www.sourcetreeapp.com/) for GUI visualization

### Set up localhost
* set up [localhost with userdir](https://discussions.apple.com/docs/DOC-3083)
  * user pages at ~/Sites (accessible at localhost/~jimmy/...)
  * localhost at /Library/WebServer/Documents (or ~www/Documents) and accessible at localhost
    * had to do "chmod -R o+w ~www/Documents" in order to get write access to this folder
    * [linked](https://kb.iu.edu/d/abbe) /wwwd to ~www/Documents so I can just do 'cd /wwwd' or '/wwwd' in zsh

### Edit Them Texts!
* no need to install vim (comes with Mac), but it's nice to configure vim:
  * install [pathogen](https://github.com/tpope/vim-pathogen) which allows us to...
  * install [Vim Sensible](https://github.com/tpope/vim-sensible) (universal set of defaults)
  * and [Solarized](https://github.com/altercation/vim-colors-solarized) (pretty colors!)
  * note: if your colors don't look right, add `let g:solarized_termcolors = 256` to your ~/.vimrc file as [detailed here](http://fideloper.com/mac-vim-tmux) (scroll down to "Add Solarized")
  * added some [tab settings into .vimrc](https://gist.github.com/jimmylorunning/196d21cca3e6233be90b)
* install [Sublime Text](http://www.sublimetext.com/) and [linked subl](https://www.sublimetext.com/docs/2/osx_command_line.html) so it can be used on the command line

### Set up Rails
* install [rbenv, ruby, rails, mysql, and postgresql](https://gorails.com/setup/osx/10.10-yosemite)
* install [heroku toolbelt](https://toolbelt.heroku.com/osx)

### PHP, if you absolutely must
* PHP came with my Mac! (type `php -v` to see if you have it first) but I still had to [configure it](http://coolestguidesontheplanet.com/get-apache-mysql-php-phpmyadmin-working-osx-10-10-yosemite/) (scroll down to PHP).
* if you already installed Rails via instructions above, then you'll have MySQL... now all you'll need is [phpmyadmin](http://www.phpmyadmin.net/home_page/index.php). Use [these instructions](http://coolestguidesontheplanet.com/get-apache-mysql-php-phpmyadmin-working-osx-10-10-yosemite/) (search for phpmyadmin)
* install PHPUnit (testing framework) with [these instructions](https://phpunit.de/getting-started.html)

### Jekyll or this blog didn't happen!
* instructions here [Jekyll](http://jekyllrb.com/docs/installation/)

### Other Super Useful Tools!
* install [Pixel Winch](http://www.ricciadams.com/projects/pixel-winch) SUPER easily measure anything in pixels
* install [Dash](https://kapeli.com/dash) read docs on Ruby, JavaScript, etc. even if you're offline
* install [Divvy](http://mizage.com/divvy/) manage your windows
* install [colordiff](http://www.colordiff.org/) `brew install colordiff` and alias diff="colordiff" in ~./zshrc
* install [1Password](https://agilebits.com/onepassword) for password management
* install [todo.txt](http://todotxt.com/) command line todo list tool!

Phew! Did I miss anything? Do you have any suggestions? Let me know!
