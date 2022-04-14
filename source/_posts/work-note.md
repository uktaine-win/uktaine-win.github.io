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

### on server install nginx
```
<!-- # wget  http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm -->
2

建立nginx的yum仓库

<!-- # rpm -ivh nginx-release-centos-7-0.el7.ngx.noarch.rpm -->
1

下载并安装nginx

# yum install nginx
2
Enable Nginx to start at boot time
# systemctl enable nginx
3 启动nginx服务
# systemctl start nginx
4 Check the current Nginx runtime status:
# systemctl status nginx


Enable all Nginx ports:
Using Firewalld (CentOS, RockyLinux)
# firewall-cmd --zone=public --add-service=http –permanent
# firewall-cmd --zone=public --add-service=https --permanent


```