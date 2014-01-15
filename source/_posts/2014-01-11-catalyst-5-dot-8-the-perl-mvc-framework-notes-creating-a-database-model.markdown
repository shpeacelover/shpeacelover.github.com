---
layout: post
title: "Catalyst 5.8 The Perl MVC Framework Notes--Creating a database model"
date: 2014-01-11 16:24:03 +0800
comments: true
categories: Catalyst
---
1. The command for creating a database model is as the following:   
```
perl script/myapp_create.pl model TestDatabase DBIC::Schema MyApp::Schema::TestDatabase create=dynamic dbi:SQLite:tmp/database
```   

2. The first argument is the name of the Catalyst Model (TestDatabase). DBIC::Schema is what sort of model we're creating. MyApp::Schema::TestDatabase is where the schema definition will be stored (we won't use the Schema in this example, but real applications will). create=dynamic tells DBIC to read the database every time theapplication is started to determine the schema (layout of tables, foreign key relations, and so on.). The final argument is the DBI connect string for the database.   
