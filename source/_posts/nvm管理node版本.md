---
title: nvm 管理 node 版本

categories: 
 - 教程


tags:
 - nvm

index_img: /img/nvm/nvm_index.png
---
简述 nvvm 管理 node 版本的教程

## nvm 的安装与配置

### 下载

前往 github 下载 [nvm](https://github.com/coreybutler/nvm-windows/releases)，推荐下载 nvm-setup.zip

![nvm 推荐下载版本](/img/nvm/001.png)

解压 nvm-setup.zip 之后得到一个 exe 安装文件

![zip 包解压后的内容](/img/nvm/002.png)

### 安装

安装过程中，首先选择 nvm 的安装路径，尽量不要选择有中文路径的地址。

![自主选择 nvm 的安装路径](/img/nvm/003.png)

下面要选择 node 的安装地址。

![选择 nodejs 的路径](/img/nvm/004.png)

如果不知道 node 安装在哪里，在 cmd 输入 where node 即可查询。

``` cmd
where node
```

![查看 node 安装地址](/img/nvm/008.png)

### 配置

在 nvm 安装根路径找到 setting.txt 加入下载源的设置。

``` txt
node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
```


![设置 nvm 的下载源](/img/nvm/007.png)

配置nvm的环境变量。

计算机-属性-高级系统设置-环境变量-系统变量

![环境变量](/img/nvm/009.png)

### 查看是否安装成功

在 cmd 中输入 nvm 查询是否安装成功，如果如下图显示，说明安装成功了。

``` cmd
nvm
```

![nvm 安装成功](/img/nvm/005.png)

如果没有出现上图的情况，可以重启试一下。

## nvm 的常用指令

 - 查看本机安装的 node 所有的版本

``` cmd
 nvm list
```

![查看 node 版本](/img/nvm/006.png)

 - 安装最新版本

``` cmd
nvm install node
```

 - 安装指定版本

``` cmd
nvm install v10.15.3
```

 - 使用指定版本

``` cmd
nvm use v10.15.3
```

 - 卸载指定版本

``` cmd
nvm uninstall v10.15.3
```



## 可能遇到的问题及解决方法

 - 安装 nvm 之后，cmd 中输入 node -v 或者 npm -v 提醒不是内部命令或外部命令...

检查 node 安装地址的 nodejs 是否可用，如果显示不可用，在 nvm 的地址下，新建一个空的 nodejs 文件夹，之后在环境变量的配置中，重新配置 nodejs 的地址。

![重新配置 nodejs 的环境变量](/img/nvm/010.png)

配置完环境变量后，重启 cmd 终端，手动卸载现存的 node 版本。

``` cmd
 nvm uninstall v10.15.3
```

之后再用 nvm 重新安装所需要的node版本包。

``` cmd
 nvm install v10.15.3
```
修改测试内容