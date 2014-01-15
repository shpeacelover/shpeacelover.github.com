---
layout: post
title: "yaml exception reading errors"
date: 2014-01-15 20:50:41 +0800
comments: true
categories: Blog
---
When I use the "rake generate" command, sometimes I will get this error like, "YAML Exception reading". We can solve this problem by following the method below.    
```     
export LC_ALL=en_US.UTF-8    
export LANG=en_US.UTF-8

```