# chenall V2.2

基于[Hexo]主题[chenall V2.2](https://github.com/chenall/hexo-theme-chenall)修改而成,未在主要功能上做相关改动,仅仅增加一些小内容以及美化主题.

- 用户配置文件也采用chenall的方案(自动加载`$SOURCE\_$THEME.yml`[默认就是**source\\_marklma.yml**]作为主题的配置文件,这样可以避免升级主题或其它原因导致的配置文件丢失).

### **具体效果:** [demo] 或我的搏客 [marklma.ga] gitcafe.com/marklma里面有这两个站点的完整源码

## 安装方法

通过以下命令下载主题到您的theme目录，然后修改blog的_config.yml中theme为marklma。

```
git clone git://github.com/marklma/hexo-theme-marklma.git themes/marklma
```
或
```
svn co -r HEAD https://github.com/marklma/hexo-theme-marklma/trunk themes/marklma
```

## 更新

```
cd themes/marklma
git pull 或 svn up
```

其它配置与[chenall的配置](https://github.com/chenall/hexo-theme-chenall/blob/master/README.md)基本一致。

## 主题配置说明

注: 配置中如果需要访问到本地路径,除非特别指定否则应该用`css/theme.css`不要写成`/css/theme.css`,前者是相对路径会自动添加config.root路径.后者是绝对路径.

本主题特色: **把这个配置文件复制到`source`目录下并改名为_marklma.yml则会优先使用该配置,这样可以避免由于升级主题或其它原因导致的配置丢失.更方便使用.**

默认的配置:

``` yaml
# Site default meta keywords
#keywords: site, wide, default, keywords

#已加载的模块,按顺序加载,所以需要自己调整加载的顺序,比如jquery一般要加载在最前面
loaded_modules:
- jquery
- bootstrap
- fontawesome
- prettify
- fancybox
#- mathjax

# 注: 模块是由css或js文件来实现的,部份需要附加js代码的模块在_modules目录下.
# 如: prettify 如果加载了prettify则会同时加载_modules\_modules.ejs
# 部份模块是自动按需加载的,在模板中添加如下代码加载多说的JS模块
# <% theme.add_module('duoshuo'); %>
#
#
modules:
  # respond 不要放到loaded_modules中,这个会自动加载
  # proxy 指定respond的proxy地址
  # 注: bootstrap的css文件和这个proxy需要在同一个域上
  respond: ## A fast & lightweight polyfill for min/max-width CSS3 Media Queries (for IE 6-8, and more).
    js: http://cdn.staticfile.org/respond.js/1.4.2/respond.min.js
    proxy: http://cdn.staticfile.org/respond.js/1.4.2/respond-proxy.html
  jquery:
    js: http://cdn.bootcss.com/jquery/1.10.2/jquery.min.js
  bootstrap: #强大的CSS框架，由Twitter的开发工程师推出
    css: http://cdn.staticfile.org/twitter-bootstrap/3.1.0/css/bootstrap.min.css
    js: http://cdn.staticfile.org/twitter-bootstrap/3.1.0/js/bootstrap.min.js
  prettify: # Google Code Prettify 代码的高亮显示
    css: http://cdn.bootcss.com/prettify/r298/prettify.min.css
    js: http://cdn.bootcss.com/prettify/r298/prettify.min.js
  highlightjs: # highlight.js 代码高亮显示插件
    css: http://cdn.bootcss.com/highlight.js/7.4/styles/github.min.css
    js:  http://cdn.bootcss.com/highlight.js/7.4/highlight.min.js
  fancybox: # 一款基于jQuery开发的类Lightbox插件
    css: http://cdn.bootcss.com/fancybox/2.1.5/jquery.fancybox.min.css
    js:  http://cdn.bootcss.com/fancybox/2.1.5/jquery.fancybox.min.js
  imagesloaded: #监测图片是否加载完毕的JavaScript库
    #js: js/jquery.imagesloaded.min.js
     js: http://cdn.bootcss.com/jquery.imagesloaded/3.0.4/jquery.imagesloaded.min.js
  Gallery:
    css: http://cdn.bootcss.com/blueimp-gallery/2.11.2/css/blueimp-gallery.min.css
    js: http://cdn.bootcss.com/blueimp-gallery/2.11.2/js/jquery.blueimp-gallery.min.js
  fontawesome:
    css: http://cdn.bootcss.com/font-awesome/4.0.3/css/font-awesome.min.css
  # MathJax is an open source JavaScript display engine for mathematics that works in all browsers.
  mathjax: # 生成数学公式插件
    css:
    js: http://cdn.bootcss.com/mathjax/2.3/MathJax.js?config=TeX-AMS-MML_HTMLorMML
    #js: http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML
  uyan: #有言评论系统
    uid: 1880458
  ujian: #友荐：为网站添加'猜你喜欢'功能
    uid: 1880458
  swiftype: #Swiftype配置，详情访问https://swiftype.com
    key: #对应的Engine Key 在https://swiftype.com/home可以看到。

##评论功能设置,目前支持disqus和duoshuo/uyan,需要在上面的modules中进行要应的设置
# show_count 是否显示文章的评论数量
# short_name 对应的short_name
# 需要的其它参数也可以加在下面,然后自己修改模板来使用.theme.comments.xxxxxx来调用
#
# 
comments:
    provider: duoshuo
    show_count: true
    short_name: MarkLMa

## 站点分析统计代码功能组件
# 加载在站点的footer位置
analytics:
  # provider 要加载的统计代码类型,可同时加载多少,使用","分隔. 如下就加载了51la和google的统计代码
  # provider: 51la,google 
  provider: 51la,google,cnzz,baidu
  # google-analytics UA
  google:
  # 我要啦」免费统计 ID
  51la:
  # cnzz 免费统计
  cnzz:
    siteid:   #站点ID,在获取统计代码的页面的地址栏上可以看到siteid=xxxx或从代码中提取(一般是一串数字)
    show: #显示样式  留空: 图片形式1; 1: 图片形式2; 2: 图片形式1; 其它值: 文字形式
  baidu: # 百度统计对应站点的hash信息，在百度统计中获取的代码中的32个字符串信息 %3F 后面的32个十六进制字符串。类似下面的
    siteid: 

# 站点顶部菜单,支持子菜单
menu:
  Home: ''
  About: about/
  Archives: archives/
  其它链接:
    marklma: //marklma.ga
    sourse: https://github.com/marklma/hexo-theme-marklma
    weibo: http://www.weibo.com/marklma

# ajax_widgets是否使用jquery.load动态加载widget的内容,
# 注: 部份小工具,像标签,分类,最近文章等,这些工具的内容在所有页面都是一样的,这时它就支持动态加载
# 所谓的动态加载,就是把这些内容从文章中分离出来独立存在,并采用ajax技术动态加载到指定位置.
# 使用动态加载,更新文章时,就不会因为分类或标签等内容的更改,导致所有页面都需要更新.
#
ajax_widgets: true

# 要加载的工具在这里添加
widgets:
  header: #顶部
  footer: #底部
  sidebar: #侧边栏
    - swiftype
    #- search
    - category
    - recent_posts
    - tagcloud
    - latest_update_posts
    #- random_posts
    - sina_weiboshow
    - recent_comments
  before_content: # 文章内容前
  after_content:  # 文章内容后
    #- wumiiRelatedItems
    - post_footer_info
    - ujian

  after_post:     # 文章框架之后
    - post_pageNav
    - related_posts

# For use with tagcloud or tag widgets
# - only tags >= to tag_minium are shown
tag_minium: 3

## Google 跟踪代码管理器 设置
## https://www.google.com/tagmanager/
## ID 就是对应容器的ID
## GoogleTagManagerID: GTM-ABCDEF
GTM_ID:

## 在文章中使用'[CDN_URL]:'字符串自动替换为下面的地址,主要是为了方便使用.
CDN_URL: http://your.cdn.url

## ICP备案编号
Beian:

## 使用反色的导航条(值为true时导航条的背景色是黑色)
bs_nav_inverse: true

twitter_id: marklma
facebook_id:
linkedin_id:
github_id: marklma

rss: atom.xml

```

[Hexo]: http://hexo.io/
[demo]: http://marklma.ga
[chenall.net]: http://chenall.net
