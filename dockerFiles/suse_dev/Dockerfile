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

ADD bin ~/bin

COPY dotfiles/.* /root/

RUN chsh -s /usr/bin/zsh

RUN cd $HOME && git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
   && git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions

# Set Up Vim Plugins
RUN curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

RUN vim +PlugInstall +qall

ENV HOST cerberus-gv

