FROM alpine:latest
MAINTAINER ruki <waruqi@gmail.com>

# install devel environment
RUN apk add bash git gcc g++ make readline-dev ncurses-dev libc-dev

# switch to ruki user
RUN addgroup -S ruki && adduser -S ruki -G ruki
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
