FROM nixos/nix
MAINTAINER ruki <waruqi@gmail.com>

RUN nix-channel --add https://nixos.org/channels/nixpkgs-unstable nixpkgs
RUN nix-channel --update

# install devel environment
RUN nix-build -A pythonFull '<nixpkgs>'
RUN nix-env -i git
RUN nix-env -i bash gcc
RUN nix-env -i gnumake

RUN mkdir /home/ruki

# install xmake
RUN nix-shell -p hello --command 'cd /tmp/ && git clone --depth=1 "https://gitee.com/tboox/xmake.git" --recursive xmake && cd xmake && ./scripts/get.sh __local__'
RUN rm -rf /tmp/xmake
ENV PATH=~/.local/bin:$PATH

# install directories
RUN mkdir /home/ruki/projects
WORKDIR /home/ruki/projects
