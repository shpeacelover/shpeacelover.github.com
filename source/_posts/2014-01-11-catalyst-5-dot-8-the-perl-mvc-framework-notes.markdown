---
layout: post
title: "Catalyst 5.8 The Perl MVC Framework Notes "
date: 2014-01-11 12:33:25 +0800
comments: true
categories: Catalyst
---
1. catalyst.pl MyApp    (this command will create the app)   

2. Inside the lib directory, there is a file named MyApp.pm, This file defines the namespace and inheritance that are necessary to make this a Catalyst application. It also contains the list of plugins to load application-­specific configurations. These configurations can also be defined in the myapp.conf file in the MyApp directory. However, if the same configuration is mentioned in both the files, then the configuration mentioned here takes precedence.   
3. The file lib/MyApp/Controller/Root.pm will handle all root level (/)URLs. This is where the code that generates the welcome page is located.   
4. The root directory will hold your templates and other non-­code support files. A subdirectory called /root/static is for static content such as images and stylesheets. Catalyst is set up to serve static files from this directory automatically (under the /static path), thanks toCatalyst::Plugin::Static::Simple.   
5. The script directory contains the scripts needed to run, test, and modify your application. To note here, the script myapp_create.pl, which is a version of catalyst.pl that's customized for your application. It can create Models, Views, Controllers, tests, and many other things.   
6. The t directory is where your application's automatic tests are stored. By default, you'll have the following three tests:   
     * 01app.t, which is a test that passes if your application compiles.  
     * 02pod.t, which will pass if your Plain Old Documentation (POD)embedded API documentation, inside your application, is valid.   
     * 03podcoverage.t, which tests that every public function in your application has some documentation.  

7. When a user makes a request using the browser, Catalyst will look for the appropriate method that can handle the request within packages called Controllers.   

8. In a controller, there are some automatically created stuff. "BEGIN {extends 'Catalyst::Controller'; }" is to tell Moose/Perl that this module is a Catalyst Controller. "__PACKAGE__->meta->make_immutable" ells Moose that this module will not change at runtime. This statement is necessary for performance gains and is good practice to mention in every Moose module. Modules must return true when they're loaded,otherwise Perl will assume that the loading has failed and will die with an error message. 1 is always true, so it's conventional to use it for this purpose.  
9. To create a view, we can issue the following command, 'perl script/myapp_create.pl view TT TT'. The TT TT part of the previous command means to create a View called View/TT.pm (the first TT) based on the standard Catalyst::View::TT (the second TT).  For our example, The next step is to create a template in the root/hello directory.We will name it index.tt. The root directory is the default place where Catalyst::View::TT will look for templates. This can be changed by configuration if you really need to.
10. Variables that are passed between Controllers and Views are called stash.  
11. For the "sub index" part in a controller, if we change it to "sub index :Path :Args(1)", it will accept the argument after index. The :Path attribute after index tells Catalyst that this method will handle URL requests that do not mention the method name such as /hello. The Args(1) attribute declares that this action expects one argument.  
12. If we specified :Local instead of :Path, then Catalyst would map the index action to handle a URL that looks like /hello/index. So, the URL looks like the following http://localhost/hello/index/Bonjour!, where Bonjour! is the argument that is being passed to the Controller. If we omitted the attributes (:Local, :Path, and so on), Catalyst would ignore the action entirely and it would be a normal Perl subroutine in the package. If we want to handle any URL with this method, then we can use the :Global attribute.   
13. We also changed the first line of the hello subroutine to receive the parameter within the method. Initially, it looked like    
my ( $self, $c ) = @_;.    
This gets the first two arguments passed to the action by Catalyst, $self and $c. $self is a MyApp::Controller::Hello object and is not of much use right now. $c is the Catalyst context and contains all the information about our application and the current request (and therefore is very useful). Catalyst passes more than just $self and$c though, so we want to modify that line to read 
my ($self, $c, @args)=@_;. 
This will allow us to access the rest of the arguments via the @args array.     

14. The template that will be rendered is determined by the private name of your action.   

15. The stash is a data structure that exists throughout a single Catalyst request. Data you insert into the stash in an action will be available to the View (and other actions). Templates can only access variables that have been explicitly placed here, so it's important to remember to put your useful data in the stash (otherwise it will be gone at the end of the subroutine in the Controller, instead of at the end of the request).   

16. You can automatically restart the server when necessary by running the server like       
perl script/myapp_server.pl -r -d.    
The -r will cause the server to restart when appropriate, and the -d will show debugging information, even if you've turned it off inside your application. This is especially useful as you will want to deactivate the hardcoded -Debug option in your MyApp.pm, once you are ready to deploy your application.  

