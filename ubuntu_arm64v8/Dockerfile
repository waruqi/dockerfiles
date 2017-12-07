FROM arm64v8/ubuntu
MAINTAINER ruki <waruqi@gmail.com>

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

# install fpm
RUN sudo apt install -y ruby ruby-dev
RUN gem sources -r http://rubygems.org/
RUN gem sources -a https://ruby.taobao.org/
RUN gem sources -u
RUN sudo gem install --no-ri --no-rdoc fpm

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
WORKDIR /home/ruki/projects
