RUBY e RAILS NO UBUNTU (10.10)
===

Step by step guide to install Rails (last version) and Ruby (1.9.2) on Ubuntu. We also cover some GEdit setting with GMate plugin.

**1º Update apt-get**

Open the terminal and run:

    $ sudo apt-get update

**2º Install GIT and Curl**
    
    $ sudo apt-get install curl git-core libxslt-dev libxml2-dev
    
**3º Install RVM (Ruby Version Manager)**

RVM let you install and manage more than one Ruby version. But here we'll use only one:

    bash < <(curl -s https://rvm.beginrescueend.com/install/rvm)

**4º Loading RVM**

Open the .bashrc file:

    $ sudo gedit ~/.bashrc

Put the code below in the first line, save and close:

    [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"

Search for:

    [ -z "$PS1" ] && return

And replace for:

    if [[ -n "$PS1" ]] ; then

Entities the end of the file add an "fi"as under:

    fi
    [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"
    
Reload the file (in Terminal):

    $ . ~/.bashrc

**5º Installing the other essential packages**

    $ rvm notes
    
The above command will display the missing packages to install. Just copy and paste the line like below:

    $ sudo apt-get install build-essential bison openssl libreadline5 libreadline-dev zlib1g zlib1g-dev libssl-dev vim libsqlite3-0 libsqlite3-dev sqlite3 libreadline-dev autoconf clang

**6º Checking the RVM**

Enter the next command in terminal

    $ type rvm | head -n1

He should give some message like this:

    rvm is a function
    
**7º Installing Ruby**

Run (this command will take a couple of minutes)

    $ rvm install 1.9.2
    
Set ruby 1.9.2 as the default to your user:

    $ rvm --default 1.9.2
    
Now this should work:

    $ ruby -v
    ruby 1.9.2p136 (2010-12-25 revision 30365) [x86_64-linux]
    $ gem -v
    1.6.2
    
**8º Installing Rails**

    $ gem install rails
    
If you want Rails expecificar which you want to install, just pass as a parameter, example:

    $ gem install rails -v=3.0.3


**8ºMySQL and PostgreSQL (OPTIONAL)**

In development mode most of the time sqlite is enough. If you want to use MySQL the right Gem is mysql2 but before you should do:

    $ sudo apt-get install libmysqlclient16-dev 

And after:

    $ gem install mysql2
    
For PostgreSQL:

    $ sudo apt-get install libpq-dev 

And after:

    $ gem install pg
    
    
Setup GEdit
===

For GEdit we'll use GMate plugin. In Terminal:

    $ sudo apt-add-repository ppa:ubuntu-on-rails/ppa
    $ sudo apt-get update
    $ sudo apt-get install gedit-gmate
    
Now open GEdit got Edit/Preferences menu and in Plug-ins check all. Now everything is ready.
