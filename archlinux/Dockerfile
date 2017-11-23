FROM base/archlinux
MAINTAINER ruki <waruqi@gmail.com>

# add pacman mirrors
RUN echo $'[archlinuxfr] \n\
SigLevel = Never \n\
Server = http://repo.archlinux.fr/$arch' >> /etc/pacman.conf
RUN echo 'Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch' > /tmp/a && cat /etc/pacman.d/mirrorlist >> /tmp/a && cp /tmp/a /etc/pacman.d/mirrorlist
RUN pacman -Syy

# install devel environment
RUN pacman -S --noconfirm --needed git curl base-devel ccache sudo yaourt pkgbuild-introspection fakeroot tree ripgrep

# switch to ruki user
RUN groupadd -r ruki && useradd -r -g ruki ruki
RUN mkdir /home/ruki
RUN chown -R ruki:ruki /home 
RUN echo "root:0000" | chpasswd
RUN echo "ruki:0000" | chpasswd
RUN echo "ruki ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
USER ruki

# install vim
RUN sudo pacman -S --noconfirm --needed python2-neovim python-neovim ctags 
RUN sudo ln -s `which nvim` /usr/local/bin/vim
RUN cd /tmp && git clone https://gitee.com/tboox/vim.git --depth 1 && cd vim/linux && chmod 777 ./install && ./install
RUN rm -rf /tmp/vim 

# install xmake
RUN cd /tmp && git clone https://gitee.com/tboox/xmake.git --depth 1 && cd ./xmake && make build && sudo make install 
RUN rm -rf /tmp/xmake 
RUN xmake --version

# install directories
RUN mkdir /home/ruki/projects
WORKDIR /home/ruki/projects
