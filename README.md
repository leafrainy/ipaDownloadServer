# ipaDownloadServer
## 简单的自建ipa安装服务 

### 1.材料
#### 1.1.（必须）支持https的站点（要么用免费证书自建，要么使用coding.net的page服务）
####  1.2.（必须）打包好的ipa文件
####  1.3.（必须）ipa的包名
####  1.4.（你猜呢）好看的文案宣传，UI设计

### 2.操作步骤
#### 2.1.上传ipa文件到支持https的站点或者云存储中，记录好链接。
#### 2.2.建立一个plist文件，命名为down.plist。并写入下面的代码。
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>items</key>
    <array>
        <dict>
            <key>assets</key>
            <array>
                <dict>
                    <key>kind</key>
                    <string>software-package</string>
                    <key>url</key>
                    <string>步骤2.1的https下载地址</string>
                </dict>
            </array>
            <key>metadata</key>
            <dict>
                <key>bundle-identifier</key>
                <string>你的app包名</string>
                <key>bundle-version</key>
                <string>1.0</string>
                <key>kind</key>
                <string>software</string>
                <key>title</key>
                <string>你的app名称，下载安装时会弹窗展示</string>
            </dict>
        </dict>
    </array>
</dict>
</plist>
```

#### 2.3.上传2.2的down.plist文件到https站点中，记录好链接。
#### 2.4.建立一个html文件，命名为down.html。并写入下面的代码。

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>网页标题</title>
    </head>
    <body>
        <h1>如果点击无法下载安装，请复制超链接到Safari浏览器中打开<h1/>
        <h2>
            <a title="iPhone" href="itms-services://?action=download-manifest&url=2.3中的down.plist访问链接">iPhone Download</a>
        <h2/>
    </body>
</html>
```

#### 2.5.上传2.4的down.html文件到https站点中，直接使用https访问该地址即可。

### 参考资料（表示感谢）
Github项目   https://github.com/QueeGuo/ipa-download

### TODO
建立一个完整的下载服务。包含增删改等。
