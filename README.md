## 校友邦实习自动签到

> **更新日志：**
>
> 【2021/03/07】完善文档说明，更换通知方式为更稳定的钉钉机器人

### ⛏️运行环境

Python3以及相应的库

### ⛏️运行方式

1. 配置`user.json`信息
2. 运行`autoSign.py`测试是否可以正常执行
3. 设定定时任务

### ⛏️相关说明

#### 📃`user.json`配置

```json
{
  "token":{
    "openId":"填写你的openId",
    "unionId":"填写你的unionId"
  },
  "location":{
    "country":"中国",
    "province":"XX省",
    "city":"XX市",
    "adcode":"城市编码",
    "address":"XX街道XX路XX号"
  },
  "reason": "",
  "DingDingtoken":"钉钉机器人token",
  "DingDingsecret":"钉钉机器人secret"
}
```

##### ✔️获取`openId`和`unionId`的方法

> 签到默认提交的地址是在申请实习时的地址，如果需要修改请自行修改`getPosition()`中的`lat`、`lng`参数（即修改经纬度）

**工具：**`Fiddler`等抓包工具、`PC端wx`

**前提：**`校友邦`微信小程序已绑定校友邦账号

**抓包：**

1. 登录PC端wx
2. 开启`Fiddler`抓包（`Fiddler`安装方法请自行百度）
3. 打开`校友邦`微信小程序，登录（**使用微信快捷登录**）

<img src="https://img.xiehestudio.com/pic_go/20210307123713.png" style="zoom: 50%;" />

4. 这时就能看到`Fiddler`抓包结果，如下图

![](https://img.xiehestudio.com/pic_go/20210307124015.png)

##### ✔️关于`adcode`

> 查询地址：http://pxcity.net/sfz/zhejiang/  
>
> 以浙江省宁波市为例

<img src="https://img.xiehestudio.com/pic_go/20210307125001.png" style="zoom: 67%;" />

<img src="https://img.xiehestudio.com/pic_go/20210307125053.png" style="zoom:67%;" />

**实习地址**对应的县区级代码即为`adcode`

##### 🤖钉钉机器人通知

> 配置钉钉机器人的方法请参考文档[钉钉机器人文档](https://www.dingtalk.com/qidian/help-detail-20781541.html)

<img src="https://img.xiehestudio.com/pic_go/20210307124247.png" style="zoom:67%;" />

### ⏰定时任务

> 设置定时任务后就可以实现每天定时执行前到啦~
>
> 设置定时任务前请在相应的定时任务环境中手动执行一遍，检查参数是否填写正确。

1. 腾讯云函数：[文档](https://cloud.tencent.com/document/product/583/9210)
2. VPS部署：[文档](https://pwner.cn/posts/12d18c2f.html)

### 鸣谢

- [CncCbz/xybSign](https://github.com/CncCbz/xybSign)
- [xiaomingxingwu/xyb-sign](https://github.com/xiaomingxingwu/xyb-sign)

