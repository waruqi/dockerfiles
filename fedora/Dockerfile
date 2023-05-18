FROM fedora:latest
MAINTAINER ruki <waruqi@gmail.com>

# install devel environment
RUN dnf -y install @development-tools @rpm-development-tools
RUN dnf -y install copr-cli make gcc-c++ unzip vim ripgrep
RUN dnf -y upgrade git

# switch to ruki user
RUN groupadd -r ruki && useradd -r -g ruki ruki
RUN mkdir /home/ruki
RUN chown -R ruki:ruki /home
RUN echo "root:0000" | chpasswd
RUN echo "ruki:0000" | chpasswd
RUN echo "ruki ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
USER ruki

# install xmake
RUN cd /tmp/ && git clone --depth=1 "https://gitee.com/tboox/xmake.git" --recursive xmake && cd xmake && ./scripts/get.sh __local__
RUN rm -rf /tmp/xmake
ENV PATH=~/.local/bin:$PATH

# install directories
RUN mkdir /home/ruki/projects
WORKDIR /home/ruki/projects
