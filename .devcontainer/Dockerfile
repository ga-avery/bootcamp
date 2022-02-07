ARG version=21.04
FROM ubuntu:$version
ARG preinstalls="curl gnupg locales lsb-release software-properties-common sudo tzdata wget zsh"
ARG DEBIAN_FRONTEND="noninteractive"
ARG TZ="America/Los_Angeles"
ARG installs="git mongodb-mongosh nodejs postgresql-client python3.9-venv ruby-full sqlite3"

# initial update and installs
RUN apt update && apt install -y $preinstalls

# generate the UTF-8 locale
RUN rm -rf /var/lib/apt/lists/*
RUN localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8

# create student user
RUN useradd -m student -G sudo
RUN echo "student:sei" | chpasswd
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
RUN chsh student -s `which zsh`

# switch to student user
USER student
WORKDIR /home/student
RUN mkdir /home/student/.vscode-server && sudo chown -R student:student .vscode-server

# add in ppas and update software repos
RUN sudo add-apt-repository ppa:git-core/ppa -y
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
RUN echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list
RUN echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
RUN wget -qO - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
RUN wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -

# update apt repos again and install tools
RUN sudo apt update -y
RUN sudo apt install -y $installs

# update node/npm to latest versions
RUN sudo npm i -g n
RUN sudo n latest

# set up git with standard settings
RUN git config --global init.defaultBranch main

# install oh-my-zsh with default zshrc file
RUN sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended
COPY .zshrc .

# switch back to root to change the owner of the zshrc file
# and allow the user to edit it.
USER root
RUN chown student .zshrc
