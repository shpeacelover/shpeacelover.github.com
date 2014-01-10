---
layout: post
title: "When Can We Omit the Ampersand While Calling a Subroutine "
date: 2014-01-07 16:39:30 +0800
comments: true
categories: Perl
---
If the compiler sees the subroutine definition before invocation, or if Perl can tell from the syntax that it’s a subroutine call, the subroutine can be called without an ampersand, just like a built-in function.
