## 一.项目简介
逆向分析应用时想快速浏览一批样本的信息，人工逐个统计太费时费力，遂想着写个python脚本进行处理。

## 二.功能
- 批量获取apk信息
- 批量下载apk
- 批量以md5重命名apk

## 三.实现思路
- 1.用androguard库获取apk的基本信息（文件md5、签名md5、包名等），再用openpyxl库处理excel文件。

- 2.将待下载的apk链接放到一张excel表中，用openpyxl获取链接，再用request发起网络请求，获取response后判断文件大小，再以二进制写入文件。

- 3.通过hashlib对文件进行摘要，获取md5后用os.rename()重命名。

## 四.使用说明
选用了python3，需要导入androguard、openpyxl、request等库才能起飞。

4.1 查看help
`python3 apk_toolbox.py -h`

```
———————— 使用说明 ————————
  -h, --help:         帮助信息
  -v, --version:      版本号
  -d, --download:     批量爬虫apk
  -r, --rename:       将文件以md5重命名
  -i, --info:         获取apk信息
```

4.2 批量获取apk信息
```python
python3 apk_toolbox -i 目标文件夹
会在`./日期文件夹`中生成`apk_info_日期.xlsx`，该表会记录目标文件夹apk的信息。
```

4.3 批量下载apk
```python
需将下载链接放在一张excel表格中，再运行`python3 apk_toolbox.py -d Excel表格`，下载文件存放在`./日期文件夹/`下
```

4.4 批量以md5重命名apk
```python
python3 apk_toolbox.py -r 目标文件夹
```
