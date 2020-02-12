# 今日概览

- 今天是什么日子： 
>
- 起床时间：
>
- 就寝时间：
>
- 天气：
>
- 心情：
>
>#任务清单
- 昨日完成的最重要三件事：
>
- 今天最重要的三件事：
>
>

# 学习·信息·阅读

- 将你每天的学习到的知识在这里简要进行记录（只记录关键内容和心理感受）
>

# 健康·饮食·锻炼

- 有强健的体魄才能更好的学习和生活。
>

# 人际·家人·朋友

>

# 工作·思考

>

# 创意·未来

>

***
# 周复盘(每周日晚完成)

>

# 月计划(每月1号完成)

>

```python
##使用药智网，作为例子 ==>https://www.yaozh.com/login/
import urllib.request
#import urllib.parse
from urllib import parse
#使用这个包，自动保存cookies
from http import cookiejar
#1.用代码登录
#1.1登录网址【在登陆页面，右键检查，在network中找到login文件】
login_url="https://www.yaozh.com/login/"
#1.2登陆参数【在登录页打开网页调试，在network中勾选preserve log(保存上个页面的请求)，输入账号密码点击登录跳转页面，然后在login中找到form data参数】
   #注意两点：参数要经过转译  ；post请求的data要求是byte类型（二进制）
login_form_data={
        #账号密码
        "username":"heyingjie",
        "pwd":"heyingjie1996",
        #这两个参数，和登录页有关系，在网络调试器的elements中ctrl+f可以查找到两个参数
        "formhash":"18280DC67C",
        "backurl":"https%3A%2F%2Fwww.yaozh.com%2F"
        
        }
    #对参数进行转译，并转成byte类型
encode_login_form_data=parse.urlencode(login_form_data).encode("utf-8")
    #请求头
header={  
    #创建键值对要求键名必须首字母大写，其余位置字母小写
    #浏览器的版本
    "User-agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.130 Safari/537.36",
 
    }

#1.3发送登录请求POST【这个网站是用post登陆的】

cook_jar=cookiejar.CookieJar()
    #定义有cookie功能的handler,这个handler的参数是cookiejar
cookie_handler=urllib.request.HTTPCookieProcessor(cook_jar)
    #定义opener
cookie_opener=urllib.request.build_opener(cookie_handler)
    #如果要是使用代理，调用opener的open(url)方法访问url
    #或者使用调用opener的open(request)访问url,request中可以加入header，对浏览器参数进行设置


    #把header的信息和提交参数，都填入请求对象request之中
cookie_request=urllib.request.Request(login_url,headers=header,data=encode_login_form_data)
    #发请求,如果登陆成功自动保存cookie,之后用opener的open()访问其他，就会自动带上cookie
cookie_opener.open(cookie_request)
             
#2.带着cookies去访问,药智网个人中心==>显示网址是 https://www.yaozh.com/member/
center_url="https://www.yaozh.com/member/"
#创建请求头
center_request=urllib.request.Request(center_url,headers=header) 
#不使用urlopen(request)
#使用之前创建的opener来发起请求,因为opener里面有之前获取的cookie
response=cookie_opener.open(center_request)
#保存下来
data=response.read().decode("utf-8")
with open("center.html","w",encoding="utf-8")as f:
    f.write(data)




import requests
url="http://www.baidu.com"
response=requests.get(url)

print(response.content().decode("utf-8"))
```





![第一张图片](https://raw.githubusercontent.com/heyingjiee/markdown_image/master/1.png)





![RUNOOB 图标](http://static.runoob.com/images/runoob-logo.png "RUNOOB")



.

















