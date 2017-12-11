FROM f69m/ubuntu32:lts
MAINTAINER ruki <waruqi@gmail.com>

# install devel environment
RUN apt update 
RUN apt install -y -f ccache curl build-essential tree silversearcher-ag git sudo

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
