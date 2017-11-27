FROM waruqi/arch
MAINTAINER ruki <waruqi@gmail.com>

# build xmake
RUN cd /tmp && git clone https://gitee.com/tboox/xmake.git --depth 1 
RUN cd /tmp/xmake && echo 'LDFLAGS_RELEASE += -static' >> core/plat/linux/prefix.mak && sed -i 's/\-lreadline//g' core/makefile
RUN cd /tmp/xmake && make build && make install prefix=/tmp/usr
RUN /tmp/usr/share/xmake/xmake --version

# prepare dockerfile for the running environment
COPY Dockerfile.run Dockerfile
CMD tar -cf - /tmp/usr Dockerfile
