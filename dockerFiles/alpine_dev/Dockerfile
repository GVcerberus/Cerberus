FROM alpine:latest
 
MAINTAINER Gaurav Verma <burnitcerberus@gmail.com>

RUN apk update && apk upgrade \ 
   && apk add --update bash zsh build-base git curl python python3 \
      python-dev cmake ctags clang libxt libx11 libstdc++ make libxpm-dev libx11-dev \ 
      libxt-dev ncurses-dev \
   && apk add -U curl \
   && cd /tmp \
   && git clone --depth=1 https://github.com/vim/vim \
   && cd /tmp/vim \
   && ./configure --with-features=big \
      --enable-multibyte \
      --enable-pythoninterp \
      --with-python-config-dir=/usr/lib/python2.7/config \
      --disable-gui \
      --disable-netbeans \
      --prefix /usr \
   && make install \
   && rm -rf /tmp/vim \
   && cd $HOME && git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
   && git clone https://github.com/zsh-users/zsh-autosuggestions /root/.zsh/zsh-autosuggestions \
   && curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
      https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim \
   && cd ~ && curl -O https://raw.githubusercontent.com/GVcerberus/dotFiles/master/.vimrc \
   && curl -O https://raw.githubusercontent.com/GVcerberus/dotFiles/master/.zshenv \
   && curl -O https://raw.githubusercontent.com/GVcerberus/dotFiles/master/.zshrc \
   && curl -O https://raw.githubusercontent.com/GVcerberus/dotFiles/master/.gitconfig \
   && curl -O https://raw.githubusercontent.com/GVcerberus/dotFiles/master/.ycm_global_extra_conf.py \
   && vim +PlugInstall! +qall \
   && cd ~/.vim/plugmanager/YouCompleteMe \
   && mkdir build \
   && cd build \
   && cmake ../third_party/ycmd/cpp/ -DEXTERNAL_LIBCLANG_PATH=/usr/lib/libclang.so.5.0 \
   && cmake --build . --target ycm_core \
   && cd ~/.vim/plugmanager/YouCompleteMe \
   && rm -rf build

ENV HOST cerberus-gv-root

ENTRYPOINT ["zsh"] 
