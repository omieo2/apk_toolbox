### 一.项目简介
逆向分析应用时想快速浏览一批样本的信息，手动查询太费时费力，所以写个想写个脚本批量处理应用。

### 二.功能点
- 批量获取apk信息
- 批量下载apk
- 批量以md5重命名apk

### 三.实现思路
- 1.用androguard库获取apk信息（文件md5、签名md5、包名等），再将信息写入一张excel表。

- 2.将下载链接放在excel表的第一列，获取所有链接后进行迭代，通过requests请求获取response，然后判断文件大小(只下载小于100M的应用)，再写入文件。

- 3.通过hashlib对文件进行摘要，以文件MD5进行重命名。

### 四.使用说明
配置好python3，通过命令`pip install -r requirements.txt`安装所需的库。

4.1 查看help
`python3 apk_toolbox_v1.1.py -h`

```
———————— 使用说明 ————————
  -h, --help:         帮助信息
  -v, --version:      版本号
  -d, --download:     批量爬虫apk
  -r, --rename:       将文件以md5重命名
  -i, --info:         获取apk信息
```

4.2 批量获取apk信息
```
-将apk放在同一个文件夹下
-执行命令：python3 apk_toolbox_v1.1 -i 文件夹
-运行完后查看：当前目录\当天日期\apk_info_日期.xlsx
```

4.3 批量下载apk
```
-将下载链接放在一张excel表格的第一列
-执行命令：python3 apk_toolbox_v1.1.py -d 文件名.xlsx
-下载完后查看：当前目录\当天日期\，存放着应用及应用信息表。
```

4.4 批量以文件md5重命名apk
```
python3 apk_toolbox_v1.1.py -r 目标文件夹
```
