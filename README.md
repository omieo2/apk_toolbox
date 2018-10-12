# Apk_Toolbox
逆向分析应用时想快速浏览一批样本的信息，人工逐个统计太费时费力，遂想着写个python脚本进行处理。

功能：
批量获取apk信息
批量下载apk
批量修改apk文件名

实现思路：
1.用androguard库获取apk的基本信息（文件md5、签名md5、包名等），再用openpyxl库处理excel文件。
2.将待下载的apk链接放到一张excel表中，用openpyxl获取链接，再用request发起网络请求，获取response后判断文件大小，再以二进制写入文件。
3.通过hashlib对文件进行摘要，获取md5后用os.rename()重命名。
