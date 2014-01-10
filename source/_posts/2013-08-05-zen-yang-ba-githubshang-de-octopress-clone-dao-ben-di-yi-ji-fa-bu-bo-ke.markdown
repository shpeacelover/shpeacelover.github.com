---
layout: post
title: "怎样把 github上 的 octopress clone 到本地以及发布博客"
date: 2013-08-05 17:41
comments: true
categories:Blog
---
力求精简， 步骤如下：
1. git clone -b source https://github.com/shpeacelover/shpeacelover.github.com octopress
2. cd octopress
3. git clone https://github.com/shpeacelover/shpeacelover.github.com _deploy
4. sudo gem install bundler
5. bundle install
6. rake new_post["The Title of Your Article"]
7. bundle exec rake generate
8. bundle exec rake preview
9. bundle exec rake deploy
10. git add .
11. git commit -m 'your comment'
12. git push origin source
