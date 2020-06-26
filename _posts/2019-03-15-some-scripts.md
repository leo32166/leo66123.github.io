---
title: linux常用安装脚本
---
nvm:

    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
lnmp:

    wget http://soft.vpser.net/lnmp/lnmp1.5.tar.gz -cO lnmp1.5.tar.gz && tar zxf lnmp1.5.tar.gz && cd lnmp1.5 && ./install.sh lnmp

erlang&elixir:
    wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb && sudo dpkg -i erlang-solutions_2.0_all.deb
    sudo apt-get update
    sudo apt remove erlang-base-hipe erlang-crypto erlang-syntax-tools
    sudo apt-get install esl-erlang
    sudo apt-get install elixir


    sudo yum -y install epel-release
    sudo yum  -y  update
    wget http://packages.erlang-solutions.com/erlang-solutions-1.0-1.noarch.rpm
    sudo rpm -Uvh erlang-solutions-1.0-1.noarch.rpm
    sudo yum  -y install erlang
    cd /usr/local && wget https://github.com/elixir-lang/elixir/releases/download/v1.10.2/Precompiled.zip
    unzip Precompiled.zip
    

katoolin：

    git clone https://github.com/LionSec/katoolin.git
    sudo cp katoolin/katoolin.py /usr/bin/katoolin
    chmod +x /usr/bin/katoolin
    
    
rvm:

    apt install gnupg2
    gpg2 --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB

    \curl -sSL https://get.rvm.io | bash -s stable --rails
    source /usr/local/rvm/scripts/rvm

beef:

    sudo apt-add-repository -y ppa:brightbox/ruby-ng
    sudo apt-get install ruby ruby-dev
    wget https://github.com/beefproject/beef/archive/master.zip 
    unzip master.zip
    cd master


apt install sqlmap

python:

    git clone https://github.com/python/cpython
    sudo apt-get update
    sudo apt-get   -y upgrade
    sudo apt-get   -y dist-upgrade
    sudo apt-get  -y install build-essential python-dev python-setuptools python-pip python-smbus
    sudo apt-get install -y libncursesw5-dev libgdbm-dev libc6-dev
    sudo apt-get install -y zlib1g-dev libsqlite3-dev tk-dev
    sudo apt-get install -y libssl-dev openssl
    sudo apt-get install -y libffi-dev
    cd cpython
    ./configure
    make
    sudo make altinstall

vpn:

    wget https://git.io/vpnsetup -O vpnsetup.sh && sudo sh vpnsetup.sh

msf:

    curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall && \
    chmod 755 msfinstall && \
    ./msfinstall
