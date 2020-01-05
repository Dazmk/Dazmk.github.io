---
title: BMI 计算器(BMI Calculator)
date: 2017-12-21 22:37:48
tags: Rails
---

这两天看高見龍老师的为你自己学ruby on rails 教程，其中有一个比较简单的Demo，就是这个BMI [Calculator](http://railsbook.tw/chapters/12-controllers.html#bmi-calculator)，自己动手跟着实现了一下，顺便写一篇博客记录一下，加深印象。

最终效果如下，输入身高体重点击开始计算后会得出BMI值，UI比较简陋，重要的是理解rails的整个流程。
![image](http://p16vszsby.bkt.clouddn.com/image/bmi_calculator_1.png?attname=&e=1513831002&token=NYX5b6QaVFGMB5vzHSgy0lp2jGcBlHXbg7YIca07:l3Y4HWpFHBt6bGhG6GaSNcoJnOU)

![image](http://p16vszsby.bkt.clouddn.com/image/bmi_calculator_2.png?attname=&e=1513831002&token=NYX5b6QaVFGMB5vzHSgy0lp2jGcBlHXbg7YIca07:coxWBD3UH2mypunrMJHsM5irGVc)

0. 新建一个rails项目：
```
  rails new bmi
```
1. 创建控制器(controller)

首先切换到项目
```
cd bmi
```
之后输入如下指令用来创建控制器
```
rails generate controller bmi index
或者
rails g controller bmi index
```
上面的指令会自动帮助我们做三件事
* 加上route,打开config/route.rb文件
```
Rails.application.routes.draw do
  get 'bmi/index'

  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
end
```
将其中的
```
get 'bmi/index'
```
改写成
```
get 'bmi', to: 'bmi#index'
```
并且添加
```
post "bmi/result", to: "bmi#result"
```

* controller中加上名为 index 的 Action
打开app/controllers/bmi_controller.rb,其中内容如下
```
class BmiController < ApplicationController
  def index
  end
end

```
* 创建app/views/bmi/index.html.erb文件
打开app/views/bmi/index.html.erb,其中内容如下
```
<h1>Bmi#index</h1>
<p>Find me in app/views/bmi/index.html.erb</p>
```

2. 建立输入表单
编辑index.html.erb，将其改为如下内容
```
<h1>BMI 计算器</h1>
<%= form_tag 'bmi/result' do %> 
  身高: <%= text_field_tag 'body_height' %> 公分<br/>
  体重: <%= text_field_tag 'body_weight' %> 公斤<br/>
  <%= submit_tag '开始计算' %>
<% end %>
```
form_tag,text_field_tag 和 submit_tag 是 rails 的 [TagHelper](http://api.rubyonrails.org/classes/ActionView/Helpers/FormTagHelper.html),可以点进去详细的看一下。

看一下index页面的源码，这些都是刚刚的TagHelper的功劳。
![image](http://p16vszsby.bkt.clouddn.com/image/form_tag.png?attname=&e=1513835331&token=NYX5b6QaVFGMB5vzHSgy0lp2jGcBlHXbg7YIca07:0Rg6pMzVRppl4XgWcM2KzySN9tc)

3. 现在输入的表单有了，需要去实现计算BMI的功能，上一步的表单会把数据提交到result的action计算。编辑app/controller/bmi_controller.rb,添加名为result的action
```
class BmiController < ApplicationController
  def index
  end

  def result
    height = params[:body_height].to_f / 100
    weight = params[:body_weight].to_f

    @bmi = (weight/ (height * height)).round(2)
  end
end
```
4. 计算出的结果需要显示出来，所以我们需要新建一个app/views/bmi/result.html.erb文件
```
<h1>您的BMI值为: <%= @bmi %> <h1>
```

现在项目部署一下应该就可以成功运行了~