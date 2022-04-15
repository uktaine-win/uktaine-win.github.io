---
title: work_note
date: 2022-04-12 22:04:07
tags:
---
### for  in & for   of
- use Object.keys()get keyArray of object，for in loop get the key,but only get 0,1,2...
- for in only get the Array index;use for of can get the value of Array, remember it.
### Logseq
- new tool for knowledge 

### uniapp
- future tool for work

### svg review
- in vue project use svg in global

### toFixed()
- basic rule: four drop six add five see condition
  ```
    2.34.toFixed(1) -> '2.3'
    2.36.toFixed(1) -> '2.4'
    2.35.toFixed(1) -> '2.4'
    2.335.toFixed(2) -> '2.33'
    2.3351.toFixed(2) -> '2.34' behind five have no-zero number will add
    2.345.toFixed(2) -> '2.35' before five is even number and smaller than five
    2.355.toFixed(2) -> '2.35' before five is odd number and smaller than five
    2.365.toFixed(2) -> '2.37' 
    2.375.toFixed(2) -> '2.38' before five is bigger than five will add
    -2.335.toFixed(2) -> -2.33 negative number turn to number of type
    (-2.335).toFixed(2) -> '-2.33' negative number turn to string of type
  ```

### use tampermonkey to add username and password
- when login at usually pages,can remember username and password to auto login
- simple auto-test

### window.onload() window.document.ready()
- when the html page is ready or loaded,can run script.
 ```
window.onload = function() { /*code*/}
window.document.ready(function(){/*code*/})
```
- need to certain
### window page lifecycle
- when open a page
- when DOM is ready,document event DOMContentLoaded can be trigger,on this time can run some script
- and <script>..code..</script> or <script src=""></script> will obstruct the DOMContentLoaded event
- at the same time the image can keep loading not clog
- when every source is loaded,the window.load event can be trigger
- when user left page 
- window.onbeforeunload 
- window.unload
- other tips: document.readyState have three state => loading -> interactive -> complete

### deploy serve on server
- https://juejin.cn/post/6844904032218120200  nginx pm2 
- https://juejin.cn/post/6844903811127967758  scp2 auto deploy to different environment
- https://juejin.cn/post/6897119761302454279 vuepress github pages
- https://juejin.cn/post/6844904025272352775 vue express nodejs; from front to end
- https://juejin.cn/post/7049692191110725645 buy server and deploy