# Docker {#docker}

Docker

LXC=Linux Container

LXC:

NameSpace:实现容器间的隔离

Cgroups:限制容器资源使用

chroot:文件系统隔离

boot2docker=VirtualBox+LinuxKernel_docker

LinuxKernel:

Cotainer:

pid：独立进程和1号进程

net: network info

ipc:

mnt:mount 自己独立的目录

utc:独立的hostname和domain

Docker：

aufs:实现分层的文件系统管理

image：read-only，单链表系统，每一个image包含指向parent image的指针。没有parent image的image是base image.

container：read-write

bootfs

rootfs

libcontainer

libchan

libswarm