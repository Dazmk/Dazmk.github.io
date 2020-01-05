title: rails 提示没有匹配的路由(no route matches)
author: Dashy
tags:
  - Rails
categories:
  - Rails
date: 2017-12-27 22:55:00
---
# No route matches

![image](http://p16vszsby.bkt.clouddn.com/no_route_matches.png?attname=&e=1514442700&token=NYX5b6QaVFGMB5vzHSgy0lp2jGcBlHXbg7YIca07:ZqqhszZqoE67WXLDgRgK12iS8MM)

今天在跟着做 Ruby on Rails 教程第五章的例子时，遇到了一个问题 No route maches

代码如下

![image](http://p16vszsby.bkt.clouddn.com/no_route_maches_code.png?attname=&e=1514442795&token=NYX5b6QaVFGMB5vzHSgy0lp2jGcBlHXbg7YIca07:wX1LfWieeycOo_hyS5VuzqLwlI0)

最后发现是在path那里多加了单引号导致的，删掉之后完美运行。

![image](http://p16vszsby.bkt.clouddn.com/no_route_maches_right.png?attname=&e=1514443115&token=NYX5b6QaVFGMB5vzHSgy0lp2jGcBlHXbg7YIca07:gfnTqUBePUl5Rt75RasB0MOzqbQ)


