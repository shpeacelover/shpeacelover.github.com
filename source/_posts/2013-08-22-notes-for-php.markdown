---
layout: post
title: "notes for PHP"
date: 2013-08-22 14:38
comments: true
categories:
---
1. flock() does not work with NFS or other networked file systems. It also does not work with older file systems that do not support locking, such as FAT. On some operating systems, it is implemented at the process level and does not work correctly if you are using a multithreaded server API.

2.
