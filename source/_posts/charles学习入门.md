---
title: 软件测试基础（一）--charles学习入门
date: 2021-07-26 23:05:25
type: "_posts"
layout: "posts"
img: "https://raw.githubusercontent.com/longbig/hexo-blogs/master/source/img/01.jpeg"
---
# charles学习

## 学习目标

1、能够使用charles来分析前后端的问题

2、能够用charles模拟弱网测试环境

## charles简介

**1、charles是什么？**

```
charles是一款基于HTTP协议的代理服务器，通过成为电脑或浏览器的代理，然后截取请求和请求结果达到分析抓包的目的。
特点：跨平台、半免费
```

**2、charles工作原理**

```
PC机/手机（客户端）《---》代理服务器（charles）《---》web服务器
前置步骤：
1、需要运行charles并配置代理
2、在客户端上面需要配置代理

步骤：
1、由客户端发送请求
2、charles接收再发送给服务端
3、服务端返回请求结果给charles
4、由charles转发给客户端
```

**3、charles能做什么？**

```
支持HTTP及HTTPS代理

支持流量控制

支持接口并发请求

支持重发网络请求

支持断点调试
```

**4、charles的优点**

```
对比fiddler

charles能够支持linux、Macos
charles支持按域名和按接口查看报文，简洁明了
charles支持反向代理
charles网络限速可选择网络类型
charles可以解析AMF协议
```

## charles安装配置

**1、charles安装**

​	下载：https://www.charlesproxy.com/download/

​	安装：双击可执行文件（windows）

**2、charles组件介绍**

```
主导航栏
    1、清除请求数据
    2、开始/取消抓包
    3、开启/关闭SSL安全代理
    4、开启/关闭慢速网络
    5、开启/关闭断点设置
    6、修改请求数据
    7、重新发送请求
    8、校验返回的请求
    9、工具设置
请求栏
1、Structure  按域名显示接口请求数据
2、Sequence   按接口请求时间显示数据
3、Filter     通过域名进行请求过滤
请求数据和响应数据栏
```

**3、charles代理设置**

```
Proxy----》Proxy  Settings -----》port：8888（默认，若该端口被占用需要修改成未被占用的端口）-----》点击“OK”
```

**4、charles访问控制**

```
Proxy--->Access Control  Settings--->点击“add”--->在IP Range编辑框中输入ip地址---->勾选编辑栏下方的小方框（不在列表的ip通过charles访问网页，会有提示信息，不勾选时不会有提示）--->点击“OK”
```

**客户端-windows代理设置**

```
1、在chrome浏览器中输入Chrome：//setting
2、在搜索框中输入“代理”
3、点击“打开您计算机的代理设置”
输入代理服务器ip地址和端口
快捷设置代理方式：同一台电脑（安装charles和客户端是同一台电脑）：proxy---》Windows  Proxy
```

**客户端-Mac代理设置**

```
1、点击苹果图标，选择系统偏好设置
2、点击“网络”--》高级
3、选择“代理”选项卡
4、勾选“Web代理（HTTP）”
web代理服务器：输入代理服务器ip地址和端口
快捷设置代理：proxy--->Macos Proxy
```

**客户端-IOS手机代理设置**

```
1、在ios手机中选择“设置”-“无线局域网”
2、点击已连接的无线网络名称
3、在“HTTP代理”的“配置代理”中选择“手动”
4、输入服务器ip地址及端点，点击“存储”
```

**客户端-android手机代理设置**

```
1、在安卓手机中选择“设置”--》“WLAN”
2、长按已连接的无线网络名称，点击“修改网络”
3、勾选“显示高级选项”
4、在代理选择项中选择“手动”
5、输入代理服务器ip地址及端口，点击“保存”
```

## charles实战

**1、charles抓包分析问题**

抓包分析问题的步骤：

```
charles代理配置---》客户端代理配置---》操作客户端软件---》分析请求数据

问题分析：
修改用户名，用户名编辑很长，点击保存，提示：系统繁忙，且提示显示两次
分析：通过抓包，发现提示信息由后端接口返回，所以显示“系统繁忙”是后端代码问题，后端只调用了一次接口且只返回一次
显示两次提示信息是前端代码的问题
```

**2、https抓包**

```
1、需要安装SSL证书
```

**1、windows证书配置**

```
1、打开charles，选择“help”---》“SSL Proxying”--->“install  charles  root certificate”
2、在打开的证书框中，点击“安装证书”，选择“本地计算机”，点击“下一步”
3、选择“将所有证书都存放下列存储”，再点击“浏览”
4、选择“受信任的根证书颁发机构”，点击“确定”--》“下一步”--》“完成”
```

**2、charles HTTPS代理配置**

```
1、在charles窗口中点击菜单“proxy”--》“SSL proxying setting”
2、在打开的设置窗口中勾选“Enable SSL Proxying”
3、点击“OK”
```

**MacOS证书配置**

```
1、打开charles，选择“help”--》“SSL  Proxy”--》“install charles root certificate”
```

**IOS证书配置**

```
1、在电脑上运行charles，且手机设置好代理，在浏览器中地址栏输入：http://charlesproxy.com/getssl
2、设置--》点击“已下载描述文件”---》点击“安装”--》点击“安装”
3、返回到“通用”页面，选择“关于本机”
4、点击“证书信任设置”，启用charles  Proxy CA证书并确认。		启用--》继续
```

**charles流量配置**

```
1、在charles窗口中点击菜单“Proxy”--》“Throttle Setting”
2、在打开的设置窗口中勾选“Enable	Throttling”
3、在“Throttle	preset”下拉框中选择对应的网络类型
4、点击"OK"
```

**弱网测试实例**

```
将charles的网络流量配置成56k modem的网络，查看网页打开情况
结果分析：从时间分析（慢）
		页面展示状态（是否闪退，。。。）
```

**charles断点配置**

```
作用：用来构建异常的测试场景
1、右击接口链接，选择“Breakpotions”
2、在浏览器刷新对应接口的页面
3、此时会自动跳转至charles并显示出接口请求信息
4、点击“Edit  Request”，修改请求信息，点击“Execute”
5、点击“Edit Response”
6、在数据格式栏中选择合适的显示格式，如：json
7、修改对应的数据，点击“Execute”
8、回到浏览器查看数据应该为修改之后的Response的信息
```







