FROM mstorsjo/llvm-mingw:latest 
MAINTAINER ruki <waruqi@gmail.com>

# install devel environment
RUN apt update
RUN apt install -y git curl sudo vim 

# switch to ruki user
RUN groupadd -r ruki && useradd -r -g ruki ruki
RUN mkdir /home/ruki
RUN chown -R ruki:ruki /home 
RUN echo "root:0000" | chpasswd
RUN echo "ruki:0000" | chpasswd
RUN echo "ruki ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
USER ruki

# install directories
RUN mkdir /home/ruki/projects
WORKDIR /home/ruki/projects
