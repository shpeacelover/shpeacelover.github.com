---
layout: post
title: "notes on 'practical programming'"
date: 2014-02-21 14:30:48 +0800
comments: true
categories: Python	
---
1. In Python, print will add a new line automatically.     
    
2. Python loads modules only the first time they are imported. Internally, Python keeps track of the modules it has already seen; when it is asked to load one that’s already in that list, it just skips over it. This saves time and will be particularly important when you start writing modules that import other modules, which in turn import other modules—if Python didn’t keep track of what was already in memory, it could wind up loading commonly used modules like math dozens of times.      
3. When Python imports a module, it sets that module’s __name__ variable to be the name of the module, rather than the special string "__main__". This means that a module can tell whether it is the main program:     
    ```
if __name__ == "__main__":	print "I am the main program"else:	print "Someone is importing me"    
```      
4. Lists are mutable;    
5. If we loop through a list, the variable is left holding its last value when the loop finishes.    
6. For Python's built in function open, the result of open is not the contents of the file. Instead, open returns a file object whose methods allow the program to access the contents ofthe file.    
7. Read reads the whole file, readline reads the next line of text from the file.    
8. string.strip, which returns a copy of a string that has leading and trailing whitespace characters (spaces, tabs, and newlines) stripped away.     
9. deadlines will read the lines of the file and store them in a list.    
