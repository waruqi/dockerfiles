FROM madworx/netbsd:8.0-x86_64
MAINTAINER ruki <waruqi@gmail.com>

# switch to ruki user
RUN ls -l
#RUN useradd -r -g ruki ruki
RUN mkdir /home/ruki
#RUN chown -R ruki:ruki /home 
RUN echo "root:0000" | chpasswd
#RUN echo "ruki:0000" | chpasswd
#RUN echo "ruki ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
USER root
RUN sh
