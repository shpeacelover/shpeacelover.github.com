---
layout: post
title: "Catalyst manual tutorial notes"
date: 2014-01-14 17:01:10 +0800
comments: true
categories: Catalyst
---
1. Make sure when adding new plugins you also include them as a new dependency within the Makefile.PL file.   
   
2. When specifying plugins, you can omit Catalyst::Plugin:: from the name.   

3. You should refer to "Action-types" in Catalyst::Manual::Intro for additional information and for coverage of some lesser-used action types not discussed here (Regex and LocalRegex).     

4. Although DBIx::Class has included support for a create=dynamic mode to automatically read the database structure every time the application starts, its use is no longer recommended.     

5. lib/MyApp contains a Schema subdirectory, which then has a subdirectory called "Result". This "Result" subdirectory then has files named according to each of the tables in our simple database (Author.pm, BookAuthor.pm, and Book.pm). These three files are called "Result Classes" (or "ResultSource Classes") in DBIx::Class nomenclature. Although the Result Class files are named after tables in our database, the classes correspond to the row-level data that is returned by DBIC.    
   
6. Also note the "flow" of the model information across the various files and directories. Catalyst will initially load the model from lib/MyApp/Model/DB.pm. This file contains a reference to lib/MyApp/Schema.pm, so that file is loaded next. Finally, the call to load_namespaces in Schema.pm will load each of the "Result Class" files from the lib/MyApp/Schema/Result subdirectory. The final outcome is that Catalyst will dynamically create three table-specific Catalyst models every time the application starts (you can see these three model files listed in the debug output generated when you launch the application).      

7. The Catalyst stash only lasts for a single HTTP request. If you need to retain information across requests you can use Catalyst::Plugin::Session.  

8. You cannot define a many_to_many relationship bridge without also having the has_many relationship in place.   

9. At the end of a given user request, Catalyst will call the most specific end method that's appropriate. For example, if the controller for a request has an end method defined, it will be called. However, if the controller does not define a controller-specific end method, the "global" end method in Root.pm will be called.   

10. Catalyst takes "extra slash-separated information" from the URL and passes it as arguments in @_ (as long as the number of arguments is not "fixed" using an attribute like :Args(0)).    

11. Chaining lets you have a single URL automatically dispatch to several controller methods, each of which can have precise control over the number of arguments that it will receive.  A chain can essentially be thought of having three parts -- a beginning, a middle, and an end.   

12. In practice you should never use a GET request to delete a record -- always use POST for actions that will modify data.   

13. There are several ways to pass information across a redirect. One option is to use the flash technique.    

14. It is generally recommended (partly for historical reasons, and partly for code clarity) only to use default in MyApp::Controller::Root, and then mainly to generate the 404 not found page for the application.   

15. Flash allows you to set variables in a way that is very similar to stash, but it will remain set across multiple requests. Once the value is read, it is cleared (unless reset).    

16. If you want to keep your existing method, you can create a new copy and comment out the original by making it look like a Pod comment. For example, put something like =begin before sub add : Local { and =end after the closing }.   

17. For debugging techniques in Catalyst, please visit the page "https://metacpan.org/pod/Catalyst::Manual::Tutorial::07_Debugging". We can also find information about how to "Check the version of an installed module" and how to "Check if a modules contains a given method".

18. If you want to use MySQL or postgresql in catalyst, please refer to the following url, "https://metacpan.org/pod/Catalyst::Manual::Tutorial::10_Appendices". 