# 通用
- 上传到github仓库
~~~
cd /Users/zhangyuchen/STM32CubeIDE/workspace_1.9.0
git add -u
git status
git commit -m "0831"
git push origin YAUAY
~~~

- 下载某一个分支下的某一个文件\
http://blog.luckly-mjw.cn/tool-show/github-directory-downloader/index.html

- Chrome 插件下载
GitZip， 无敌好用


# Debug日志


## <span id = "1">1110</span>
杨泉：
```
各位老师好
5G 专网部署11.10 进展如下：
#完成事项：
  1: cpe+基站+核心网+DN（上位机出口） 整个端到端 业务打通，上下行ping 均正常
2: 商业终端，小米11/12s，红米K40手机，捷创5g智能网关，均接入正常
3: 核心网接入浙大实验室内网，实现网管界面/ssh 登录，并进行简单实践操作指导
4: 3张专网sim卡放在实验室，均入网正常。

#需继续跟踪事宜：
1: 上下行打流测试异常问题跟踪
       今日上下行：90-180mbps/     10-150mbps，下行异常。
        期望下行超300mbps
2: 核心网网管操作指南文档分享
3: ue 互通跟踪
      该功能是支持的，估计测试时候捷创cpe使用的是ims apn的地址，导致不同，@胡家翌 可以两个sim卡接入后在试试。

如有遗漏，还请老师补充。
```

我：
```
5GC server   10.15.196.207， root/xglab
OAM 网管： http:// 10.15.196.207   admin/admin
Speedtest: 10.0.0.1:8080

10.0.0.1 核心网网段
10.20.0.1 终端的网段  internet
10.20.1.1  ims
可以增加

以下分别对应的网段去10.15.196.207 去查看，每个终端都要配下面两个
ims
internet

主要就用三个日志 logs，一个是user plane function一个是流量管理，一个是session管理
upf
amfd
smfd

上位机只有在6号口 192.168.6.1
5号口是：基站
3、4号口不用，
1 OAM管理
2内网
只有1、2能ssh

问题：
1、上下行流量低，不稳定（改queue的buffer以后）
2、终端之间无法ping通
```

## <span id = "2">1115</span>
1、将5、6号业务口的socket模式，改成dptk透传模式 \
2、
