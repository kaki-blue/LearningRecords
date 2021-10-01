## 在微软商店打不开的情况下安装WSL2

##### 更新：草，找到了`microsoft store`打不开的原因了，竟然是因为打开了 魔法猫猫 ，可恶的魔法，小丑，我是小丑吧



-----------------------------------------------------------------------------------------------------



##### `前言：感谢https://www.rainng.com/manually-install-ubuntu-wsl/`

因为高级java的课上需要显示RGB的动图

![](https://github.com/halipai/MYIMAGES/raw/main/github1/0.png?raw=true)

（详见https://github.com/jwork-2021/jw02-halipai），terminal上没有这么高级的技术，所以要安装wsl（我到底为什么不用虚拟机呢 可恶），然后发现microsoft store竟然无法打开，试了下搜到的所有方法也于事无补，所以只能在互联网上搜索手动安装wsl，话不多说，点击https://wiki.ubuntu.com/WSL#Installing_Ubuntu_on_WSL_via_rootfs，在`Installing Ubuntu on WSL via rootfs`下点击`[Ubuntu 20.04 LTS]`

![](https://github.com/halipai/MYIMAGES/raw/main/github1/1.png?raw=true)

下载wsl系统包

![](https://github.com/halipai/MYIMAGES/raw/main/github1/2.png?raw=true)

按照第一张图的说明输入

```
wsl --import <DistributionName> <InstallLocation> <FileName>
```

如我自己的输入：

```
wsl --import Ubuntu2 "F:\Program Files\Ubuntu2" "F:\Program Files\focal-server-cloudimg-amd64-wsl.rootfs.tar.gz"
```



#### 意外

在安装`wsl2`后打开了一次安卓模拟器

![](https://github.com/halipai/MYIMAGES/raw/main/github1/3.png?raw=true)

然后`wsl2`就不能用了

在`cmd`下输入

```
wsl
```

就会如下显示

```
请启用虚拟机平台 Windows 功能并确保在 BIOS 中启用虚拟化。
有关信息，请访问 https://aka.ms/wsl2-install
```

重装并不是有效的解决途径，因为安装时也会出现上述提示

经过多小时的搜索（因为我废物）和一些没有必要的操作（比如可能是windows家庭版的原因所以在windows功能中没有Hyper-V的选项也找不到组策略所以尝试去写了个.bat反正也没成功。。）后，我发现还是搜索到的第一个方法是可以解决这个问题的

感谢[WSL2启动报错——请启用虚拟机平台 Windows 功能并确保在 BIOS 中启用虚拟化 - 简书 (jianshu.com)](https://www.jianshu.com/p/be76a0f08dc7)

就是因为下了安卓虚拟器，在上面的图中点`立即修复`就会启动这个命令

```
 bcdedit /set hypervisorlaunchtype off
```

将Hyper-V设置为关

那么输入

```
bcdedit /set hypervisorlaunchtype auto
```

重启电脑，按理说就可以打开了

但在我刚发现这个问题的时候，就已经这么做n遍了，但是并没有起效，但后来在绝望的困境中无所事事，就输入了第一个命令，重启，输入第二个命令，重启，神奇的计算机就可以使用啦！

而且wsl没有安装java，为了统一所以在wsl下也安装jdk8

```
sudo apt-get update

sudo apt-get install openjdk-8-jdk
```



一个未解决的小问题：

![](https://github.com/halipai/MYIMAGES/raw/main/github1/4.png?raw=true)

网络上无法搜到，我也没解决









