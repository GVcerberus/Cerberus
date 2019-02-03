FROM ubuntu:latest
 
MAINTAINER Gaurav Verma <burnitcerberus@gmail.com>

RUN apt-get update \ 
   && apt-get upgrade \ 
   && apt-get -yq install build-essential bash zsh git vim curl python python3 \
      cmake make ctags clang ncurses-dev \
   && cd $HOME && git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
   && git clone https://github.com/zsh-users/zsh-autosuggestions /root/.zsh/zsh-autosuggestions \
   && curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
      https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim \
   && cd ~ && curl -O https://raw.githubusercontent.com/GVcerberus/dotFiles/master/.vimrc \
   && curl -O https://raw.githubusercontent.com/GVcerberus/dotFiles/master/.zshenv \
   && curl -O https://raw.githubusercontent.com/GVcerberus/dotFiles/master/.zshrc \
   && curl -O https://raw.githubusercontent.com/GVcerberus/dotFiles/master/.gitconfig \
   && curl -O https://raw.githubusercontent.com/GVcerberus/dotFiles/master/.ycm_global_extra_conf.py \
   && vim +PlugInstall! +qall

ENV HOST cerberus-gv-root

ENTRYPOINT ["bash"] 
