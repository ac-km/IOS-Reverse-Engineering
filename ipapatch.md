# [IPAPatch](https://github.com/Naituw/IPAPatch)

>  IPAPatch是一个比较神奇的东西，有点类似于二次打包，他会把你写的patch编译成framework，然后解压原始ipa中的文件替换xcode生成的app里面的内容，并且通过optool将你代码生成的framework和外部的framework注入到二进制文件中，最后对这些二进制文件进行签名然后安装到手机上。

## 配置使用

### 第一步，下载工程

使用git克隆工程`git clone https://github.com/Naituw/IPAPatch.git`

### 第二步，准备一个砸了壳的ipa文件

载pp助手里面去下载没有课的ipa或者手动去吧ios应用商店下载的ipa的壳给砸开

### 第三步，替换掉工程里面的app.ipa文件

将上一步砸开壳之后的ipa文件重名名为app.ipa，然后放到I`PAPatch/Assets/app.ipa`

### 第四步，放置三方framework（可选）

放置三方framework到`IPAPatch/Assets/Frameworks`这里面，放在这里面会被自动链接

### 第五步，配置

打开 IPAPatch，在 IPAPatch-DummyApp 这个 Target 里，配置好 BundleID 和代码签名。Display Name 会作为前缀添加到原来的 App 上

### 第六步，编写你的patch

编写的入口在`IPAPatchEntry.m`文件的load方法，你可以在这里改变应用的行为，比如去掉https证书校验什么的，总之可以做你任何想做的时

### 第七步，编译运行

点击run按钮就可以了

### 第一次搞需要注意的问题

1. xcode需要登录你的apple id账号
2. 需要使用砸过壳的app，或者直接在pp助手下载越狱之后的应用
3. 在signing里面的team要选自己，然后identity里面的bundle identifier也需要修改成别人没有占用的

