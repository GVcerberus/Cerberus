FROM opensuse:tumbleweed

MAINTAINER Gaurav Verma <burnitcerberus@gmail.com>

LABEL Author="Gaurav VERMA"
LABEL Project="Cerberus"
LABEL Version="1.0"
LABEL LastModified="Thu Jan 17 21:09:37 2019"

RUN zypper --non-interactive install which \
   && zypper --non-interactive install git \
   && zypper --non-interactive install vim \
   && zypper --non-interactive install curl \
   && zypper --non-interactive install python3 \
   && zypper --non-interactive install python \
   && zypper --non-interactive install gcc \
   && zypper --non-interactive install clang \
   && zypper --non-interactive install zsh

RUN zypper --non-interactive install tar
RUN zypper --non-interactive install gcc-c++

RUN zypper --non-interactive install java \
   && zypper --non-interactive install make \
   && zypper --non-interactive install ctags

ENV JAVA_HOME /usr/bin/java

# Set Up Vim Plugins
RUN curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

ADD bin ~/bin

COPY dotfiles/.* /root/

RUN source /root/.zshrc

RUN vim +PlugInstall +qall 

ENV HOST Cerberus-v1

# install docker client and ssh
