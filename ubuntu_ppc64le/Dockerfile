FROM ppc64le/ubuntu:22.04
MAINTAINER ruki <waruqi@gmail.com>

# install devel environment
RUN apt update
RUN apt install -y git curl build-essential ccache tree silversearcher-ag
RUN apt install -y sudo

# switch to ruki user
RUN groupadd -r ruki && useradd -r -g ruki ruki
RUN mkdir /home/ruki
RUN chown -R ruki:ruki /home
RUN echo "root:0000" | chpasswd
RUN echo "ruki:0000" | chpasswd
RUN echo "ruki ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
USER ruki

# install xmake
RUN cd /tmp/ && git clone --depth=1 "https://gitee.com/tboox/xmake.git" -b dev --recursive xmake && cd xmake && ./scripts/get.sh __local__
RUN rm -rf /tmp/xmake
ENV PATH=~/.local/bin:$PATH

# install directories
RUN mkdir /home/ruki/projects
WORKDIR /home/ruki/projects
