# 常用命令

### 安装Rails

```
$gem install
```


###### 创建文件夹 cd 进入后 创建应用
```
$rails new first_app

```

让Rails不生成默认使用的Test：：Unit测试框架对应的test文件夹。
```
$rails new first_app --skip-test-unit
```


    create  README.md
      create  Rakefile
      create  config.ru
      create  .gitignore
      create  Gemfile
      create  app
      create  app/assets/config/manifest.js
      create  app/assets/javascripts/application.js
      create  app/assets/javascripts/cable.js
      create  app/assets/stylesheets/application.css
      create  app/channels/application_cable/channel.rb
      create  app/channels/application_cable/connection.rb
      create  app/controllers/application_controller.rb
      create  app/helpers/application_helper.rb
      create  app/jobs/application_job.rb
      create  app/mailers/application_mailer.rb
      create  app/models/application_record.rb
      create  app/views/layouts/application.html.erb
      create  app/views/layouts/mailer.html.erb
      create  app/views/layouts/mailer.text.erb
      create  app/assets/images/.keep
      create  app/assets/javascripts/channels
      create  app/assets/javascripts/channels/.keep
      create  app/controllers/concerns/.keep
      create  app/models/concerns/.keep
      create  bin
      
      Installing sass-rails 5.0.6
      Bundle complete! 15 Gemfile dependencies, 63 gems now installed.
      Use `bundle show [gemname]` to see where a bundled gem is installed.
      
      
若创建失败需要取得用户权限,并重新运行命令

```
$sudo -s
```


要心安装gem 运行
```
$bundle update 
```

```
 $bundle install
```
禁止安装生产环境所需的gem，这个选项会被记住，所以后续调用Bundler就不用再指定这个选项，直接运行bundle install就可以自动不安装生产环境所需的gem
```
 $bundle install --without production
```


文件夹 | 说明
---|---
qpp/ | 程序的核心文件，包含模型、视图、控制器和帮助方法                       
app/assets | 程序的资源文件，如CSS、JavaScript
bin／ | 可执行文件
config／ | 程序的设置
db／ | 数据库文件
doc／ | 程序的文档
lib／ | 代码库文件
log／ | 程序的日志文件
public／ | 公共可访问的数据，如出错页面
script/rails | 生成代码、打开终端会话或开启本地服务器的脚本
test/ | 程序的测试文件
tmp/ | 临时文件
vendor/ | 第三方代码，如插件和gem
vendor/assets | 第三方代码包含的资源文件，如CSS、Javascript和图片
README.rdoc | 程序简介
Rakefile | rake命令包含的任务
Gemfile | 程序所需要的gem
Gemfile.lock | gem列表，确保本程序的复制版使用相同版本的gem
config.ru | Rack中间件的配置文件
.gitignore | git忽略的文件类型







###### Rails自带命令行运行本地服务器


```
$rails server 或者 $rails s
```
        => Booting Puma
        => Rails 5.0.0 application starting in development on http://localhost:3000
        => Run `rails server -h` for more startup options
        Puma starting in single mode...
        * Version 3.6.0 (ruby 2.3.1-p112), codename: Sleepy Sunday Serenity
        * Min threads: 5, max threads: 5
        * Environment: development
        * Listening on tcp://localhost:3000
        Use Ctrl-C to stop

                    

浏览器访问localhost:3000，如有页面则说明服务器开启成功，在命令行工具中 按 Ctrl ＋C 关闭服务器

###### 部署工具
1. Phusion Passenger
1. Engine Yard   
1. Rails Machine                
1. Engine Yard Cloud   
1. Heroku       

搭建Heroku部署环境

在Gemfile中 加入

```
group :production do
  gem 'pg'
end

```
提交


```
 $git commit -a -m "Update Gemfile.lock for Heroku"
```

[注册](https://signup.heroku.com) Heroku 账户 

[安装](https://toolbelt.heroku.com) Heroku Toolbelt 所需软件

登录

```
$heroku login
```
创建
```
$heroku create

```
输入命令后如下，终端如下
```
Creating app... done, ⬢ murmuring-scrubland-20411
https://murmuring-scrubland-20411.herokuapp.com/ | https://git.heroku.com/murmuring-scrubland-20411.git
```
部署命令

```
 $git push heroku master
```
打开地址


```
$heroku open
```


---

### 实现用户数据模型

实现用户数据模型，还会为模型创建基于Web的页面。
没有必要置顶id，Rails会自动创建，并将其设为表主键。
脚手架后面的名字和模型一样，为单数形式，而资源和控制器为复数形势因此是**User**不是~~Users~~。


|users | |
---|---
id | integer
name | string
email | string




```
$rails generate scaffold User name: string email: string
```
新定义的User数据模型更新数据库

```
$bundle exec rake db:migrate
```





URL | 动作（Action）目的
---|---
／users | index 显示所有用户的页面
／users／1 | show 显示ID为1的用户的页面
／users／new | new 创建新用户的页面
／users／1／eidt| eidt 编辑ID为1的页面



Microposts资源


```
$rails generate scaffold Micropost content:string user_id:integer
```
新定义的User数据模型更新数据库
```
$bundle exec rake db:migrate
```


