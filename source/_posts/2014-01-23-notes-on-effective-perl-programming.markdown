---
layout: post
title: "Notes on effective Perl programming"
date: 2014-01-23 19:47:56 +0800
comments: true
categories: Perl
---
1. 如果担心原先的程序启用strict后运行不正常， 则可以在实际修改代码前， 先在命令行上试着启用strict看看：    
```
perl -Mstrict program.pl
```      

2. 所谓列表， 就是一组有序的标量集合。 所谓数组， 就是一个存储着列表的变量. 对于数组， 我们可以将它放在标量上下文中计算， 但对于列表， 则没有相应的概念。而列表永远只是列表， 它没有标量解释。    

3. 逗号操作符在标量上下文中会返回最右边的元素。  所以 my $scalar = ('aa', 'bb', 'cc') 会将cc赋给$scalar.     

4. 在标量上下文环境中的列表赋值操作， 会返回负值操作符右边的元素个数。   

5. my $elements = my @array = localtime; 使用这种方法可以计算下某个操作生成的列表中有几个元素。 由于这个规则是右结合的， 所以实际上中间被赋值的列表可以是空列表：   
my $elements = () = local time;  如果要统计全局匹配的个数， 或者split函数返回的结果有多少个元素， 可以利用这个特性。       

``` 
my $count = () = m/(...)/g;    
    
my $count = () = split /:/, $line;    
  
```     
    
 




