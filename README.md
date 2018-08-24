# README

这个项目算是初学django写的第二个项目了。~~第一个是个人博客~~

![](https://img.shields.io/badge/Python-3.x-green.svg)![](https://img.shields.io/badge/Django-2.x-green.svg)

### cms识别

采用云悉的API，自行申请。

###  漏洞利用

说通俗点，就是输入一个域名，然后轮插件 - -。

#### 插件编写

必须要有run方法来完成检测，必须有返回值，如果有漏洞返回值中必须要有`[+]`，没有漏洞则不要求。

样例：

```python
import requests


class sqltest:
    def __init__(self, url):
        self.url = url

    def run(self):
        url = self.url
        data = "'"
        try:
            req1 = requests.get(url,timeout=10).headers['Content-Length']
            req2 = requests.get(url + data,timeout=10).headers['Content-Length']
            if req1 != req2:
                return '[+] 存在注入'
            else:
                return '[-]不存在注入'
        except:
            return '[-]访问异常'
```

ps：你可以复制粘贴别人的漏洞过来

### 端口扫描

多线程，自定义常用端口。

### 旁站C段

webscan.cc的API，不需要申请。

### AWVS扫描

接入AWVS扫描器，支持添加、暂停、删除任务，查看漏洞及导出报告



## 注意

请先修改`cms/views.py`中的API

报告生成在项目下的`报告`目录
