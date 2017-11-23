FROM ubuntu:14.04
MAINTAINER ruki <waruqi@gmail.com>

# add apt-get mirror
ADD sources.list /etc/apt/sources.list

# install devel environment
RUN apt update
RUN apt install -y git curl build-essential ccache tree silversearcher-ag

# switch to ruki user
RUN groupadd -r ruki && useradd -r -g ruki ruki
RUN mkdir /home/ruki
RUN chown -R ruki:ruki /home 
RUN echo "root:0000" | chpasswd
RUN echo "ruki:0000" | chpasswd
RUN echo "ruki ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
USER ruki

# install vim
RUN sudo apt install -y vim ctags 
RUN cd /tmp && git clone https://gitee.com/tboox/vim.git --depth 1 && cd vim/linux && chmod 777 ./install && ./install 
RUN rm -rf /tmp/vim

# install xmake
RUN cd /tmp && git clone https://gitee.com/tboox/xmake.git --depth 1 && cd ./xmake && make build && sudo make install
RUN rm -rf /tmp/xmake 
RUN xmake --version

# install directories
RUN mkdir /home/ruki/projects