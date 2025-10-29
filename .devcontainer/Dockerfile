# syntax=docker/dockerfile:1
FROM nvidia/cuda:12.3.2-base-ubuntu22.04

ENV DEBIAN_FRONTEND=noninteractive

# base packages
RUN apt-get update && apt-get install -y \
    git python3 python3-pip ffmpeg libsm6 libxext6 wget ca-certificates curl \
    zsh vim tmux git-lfs aria2 passwd \
    && rm -rf /var/lib/apt/lists/*

# python tooling
RUN python3 -m pip install --upgrade pip \
    && python3 -m pip install pre-commit "huggingface_hub[cli]" datasets hf_transfer

# project deps
COPY requirements.txt /tmp/requirements.txt
RUN python3 -m pip install -r /tmp/requirements.txt
