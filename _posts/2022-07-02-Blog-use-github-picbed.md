---
published: true
layout: post
categories: 技术
---
## 使用github图床，利用picgo插件进行图片上传得到图片链接

![](https://raw.githubusercontent.com/kangtyou/Image/main/img/20220702155313.png)

下载这个软件过后就设置github图床如下：

![](https://raw.githubusercontent.com/kangtyou/Image/main/img/20220702155625.png)

![2022-04-25 123349.png]({{site.baseurl}}/_posts/2022-04-25 123349.png)


### 然后就可以使用复制粘贴的命令将自己想要的图片上传到自己的图库里面

使用`win + shift + s`键可以选择性截图，目前唯一的问题就是**博客搜索功能**和**markdown转pdf**的功能没有解决

- [x] 博客搜索功能
- [x] markdown转pdf功能


好像这个`proseio`本身也是可以上传图片的，而且是上传到本post目录下的。 Ok, seems that this is not useful!


### 博客搜索功能

新建`search.json`文件到根目录：








复制上面的项目里面的dest目录下面的simple-jekyll-search.min.js,复制到网站根目录的js文件夹里面.

### 修改页面文件search.html

```html
<!-- HTML elements for search-->
<div id="search-container" style="float:right;position: fixed;right:0px; bottom:10px; z-index:999999;background:#eeeeee;padding:10px 10px 0px 10px;">
  <input type="text" id="search-input" placeholder="search..." style="border:2px solid;border-radius:25px;padding-left:10px !important;" >
  <ul id="results-container" style="max-width:300px;"></ul>
</div>

<!-- script pointing to jekyll-search.js-->
<script src="/js/simple-jekyll-search.min.js"></script>

 <script>
      window.simpleJekyllSearch = new SimpleJekyllSearch({
        searchInput: document.getElementById('search-input'),
        resultsContainer: document.getElementById('results-container'),
        json: '/search.json',
        searchResultTemplate: '<li><a href="{url}" title="{desc}">{title}</a></li>',
        noResultsText: 'No results found',
        limit: 5,
        fuzzy: false,
        exclude: ['Welcome']
      })
    </script>
 ```
 
### 在default.html中修改，从而能在每一个页面都能够出现搜索
 
 
### More info about jekyll
1. [jekyll search](https://github.com/christian-fei/Simple-Jekyll-Search/blob/master/README.md)


2. [jekyll codeblock](https://rachelmad.github.io/entries/2016/11/06/code-in-jekyll#:~:text=Sometimes%2C%20you%20may%20have%20to%20explain%20something%20in,%25%7D%20%2F%2F%20your%20code%20here%20%7B%25%20endraw%20%25%7D)
 



### About markdown convert to pdf, I can simply convert it to html and then convert to pdf

**Over!!**
