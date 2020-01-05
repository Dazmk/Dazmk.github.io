title: ror教程(ruby on rails)2
tags:
  - Rails
categories:
  - Rails
author: Dashy
date: 2017-12-27 22:43:00
---
test controller 中可以通过使用setup来初始化一些变量

```
require 'test_helper'

class StaticPagesControllerTest < ActionDispatch::IntegrationTest

  def setup
    @base_title = "Ruby on Rails Tutorial Sample App"
  end

  test "should get home" do
    get static_pages_home_url
    assert_response :success
    assert_select "title", "Home | #{@base_title}" 
  end

  test "should get help" do
    get static_pages_help_url
    assert_response :success
    assert_select "title", "Help | #{@base_title}"
  end

  test "should get about" do
    get static_pages_about_url
    assert_response :success
    assert_select "title", "About | #{@base_title}"
  end
end
```

定义和使用变量时不要忘记加 @ 符号

provide 

```
<% provide(:title, "Home") %>
<!DOCTYPE html>
<html>
  <head>
    <title><%= yield(:title) %> | Ruby on Rails Tutorial Sample App</title>
  </head>
  <body>
    <h1>Sample App</h1>
    <p>
      This is the home page for the
      <a href="http://www.railstutorial.org/">Ruby on Rails Tutorial</a>
      sample application.
    </p>
  </body>
</html>
```

provide 与 content_for 区别

> The same as content_for but when used with streaming flushes straight back to the layout. In other words, if you want to concatenate several times to the same buffer when rendering a given template, you should use content_for, if not, use provide to tell the layout to stop looking for more contents.


not something we can merge

单引号字符串不能进行插值操作

```
>> string = 'dashy'
=> "dashy"
>> puts "The string '#{string}' is nonempty." if string.empty?
=> nil
>> puts "The string '#{string}' is nonempty." unless string.empty?
The string 'dashy' is nonempty.
=> nil
```

可以使用 !!（读作“bang bang”）对对象做两次取反操作，把对象转换成布尔值


```
>> a = %w[foo bar baz quux]
=> ["foo", "bar", "baz", "quux"]
>> a[0..2]
=> ["foo", "bar", "baz"]
```

值域的结束值使用 -1 时，不用知道数组的长度就能从起始值开始一直获取到最后一个元素。