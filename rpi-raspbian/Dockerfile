FROM resin/rpi-raspbian
MAINTAINER ruki <waruqi@gmail.com>

# install devel environment
ADD sources.list /etc/apt/
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

# install directories
RUN mkdir /home/ruki/projects
WORKDIR /home/ruki/projects
