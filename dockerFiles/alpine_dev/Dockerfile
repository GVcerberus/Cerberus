FROM alpine:latest

MAINTAINER Gaurav Verma <burnitcerberus@gmail.com>

LABEL Project="Cerberus-v1-Sat Jan 26 23:01:29 2019"

RUN apk update \
   && apk upgrade \
   && apk --no-cache add --update bash zsh

RUN apk add --update musl-dev git vim curl python python3 clang cmake ctags 

COPY dotfiles/.* /root/

RUN cd $HOME && git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
   && git clone https://github.com/zsh-users/zsh-autosuggestions /root/.zsh/zsh-autosuggestions

# Set Up Vim Plugins
RUN curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

RUN vim +PlugInstall +qall

ENV HOST alpine-gv

