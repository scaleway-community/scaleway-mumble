## -*- docker-image-name: "scaleway/mumble:latest" -*-
ARG SCW_ARCH

FROM scaleway/ubuntu:${SCW_ARCH}-xenial

MAINTAINER Scaleway <opensource@scaleway.com> (@scaleway)

# Prepare rootfs for image-builder
RUN /usr/local/sbin/builder-enter

# Install mumble
RUN apt-get update \
    && apt-get install -y \
       expect \
       mumble-server

# Copy files
COPY overlay ./

# Create server specific doc in /root/ for first login
RUN systemctl enable create-doc init-mumble

# Symlink doc readme to /root/
RUN ln -s /usr/share/doc/scaleway/mumble/README /root/README

# Clean rootfs from image-builder
RUN /usr/local/sbin/builder-leave
