# bt
bt-backup  官方原版v7.7.0版本面板备份

**Centos/Ubuntu/Debian安装命令 独立运行环境（py3.7）**

```Bash
curl -sSO https://raw.githubusercontent.com/lidalao/bt/main/install/install_panel.sh && bash install_panel.sh
```


# 手动破解：

1，屏蔽手机号

```
sed -i "s|bind_user == 'True'|bind_user == 'XXXX'|" /www/server/panel/BTPanel/static/js/index.js
```

2，删除强制绑定手机js文件

```
rm -f /www/server/panel/data/bind.pl
```

3，手动解锁宝塔所有付费插件为永不过期
打开目录/www/server/panel/class找到并编辑panelplugin.py文件
使用Ctrl+F搜索并找到softList['list'] = tmpList这段代码，在其下方添加如下代码：
```
                softList['pro'] = 1
        for soft in softList['list']:
            soft['endtime'] = 0
````
3，手动解锁宝塔所有付费插件为永不过期

文件路径：`/www/server/panel/data/plugin.json`

搜索字符串：`"endtime": -1`全部替换为`"endtime": 999999999999`

4，给plugin.json文件上锁防止自动修复为免费版

```
chattr +i /www/server/panel/data/plugin.json
```

5，去除后门以及其他优化
```Bash
curl -sSO https://raw.githubusercontent.com/lidalao/bt/main/install/clean_panel.sh && bash clean_panel.sh
```
