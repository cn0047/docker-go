FROM cn007b/go:1.13

MAINTAINER V. Kovpak <cn007b@gmail.com>

# 20.04 - not available yet, so $(lsb_release -rs) will not work
ARG seabolt_lsb_release=18.04

RUN apt-get update --fix-missing

# seabolt for neo4j
RUN apt-get install -y libssl1.1
RUN wget https://github.com/neo4j-drivers/seabolt/releases/download/v1.7.4/seabolt-1.7.4-Linux-ubuntu-$seabolt_lsb_release.deb \
  && dpkg -i seabolt-1.7.4-Linux-ubuntu-$seabolt_lsb_release.deb \
  && rm seabolt-1.7.4-Linux-ubuntu-$seabolt_lsb_release.deb
