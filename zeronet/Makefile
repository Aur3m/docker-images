.DEFAULT_GOAL := all
MAKEFLAGS += --warn-undefined-variables --no-print-directory
SHELL := /bin/bash

HOOK := https://hooks.microbadger.com/images/supersandro2000/zeronet/B9vzdMxCP5RYwUuPtaP61aOsM8E=
IMAGE := zeronet
BUILD_ARGS := SHA=$(shell curl -s -u ":$(GITHUB_TOKEN)" -- https://api.github.com/repos/HelloZeroNet/ZeroNet/commits/py3 | jq -r '.sha')
Z_VER := $(shell curl -Ls https://github.com/HelloZeroNet/ZeroNet/raw/py3/src/Config.py | grep -oP "(?<= self.version = \")([0-9]+\.){2}[0-9]+")
Z_REV := $(shell curl -Ls https://github.com/HelloZeroNet/ZeroNet/raw/py3/src/Config.py | grep -oP "(?<= self.rev = )[0-9]+")
VERSION := $(Z_VER)-r$(Z_REV)

include ../buildx/Makefile
