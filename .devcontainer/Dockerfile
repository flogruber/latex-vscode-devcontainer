FROM alpine:latest

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN apk add --no-cache \
    bash \
    git \
    sudo

RUN addgroup -S $USERNAME --gid $USER_GID \
    && adduser -S $USERNAME --uid $USER_UID -G $USERNAME

RUN echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME\
    && chmod 0440 /etc/sudoers.d/$USERNAME

# dependencies for texlive
RUN apk add -U --repository http://dl-3.alpinelinux.org/alpine/edge/main \
    poppler harfbuzz-icu

RUN apk add -U --repository http://dl-3.alpinelinux.org/alpine/edge/community \
    zziplib \
    texlive-full \
    biber