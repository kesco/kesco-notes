# Vagrant简易教程

## 打包Vagrant Box

当我们开发完后，因为要统一我们组内的开发环境，所以Vagrant Box要保持一致。为了减少工作量，Box一般都是要共享的，所以我们要自己打包好自己的开发环境。

下面，我们自己假设Vagrant内的虚拟环境为Ubuntu，主要步骤如下：

1. 清理虚拟机缓存
2. 清理虚拟机硬盘占用的空余空间
3. 用Vagrant命令打包

## 清理虚拟机缓存

Linux缓存主要是系统缓存和升级缓存为主：

```sh
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```
## 清理虚拟机硬盘占用的空余空间

虚拟机分区会占用些空闲空间，打包时候为了缩小box体积，我们要清理掉：

```sh
sudo dd if=/dev/zero of=/EMPTY bs=1M
sudo rm -f /EMPTY
```
## 用Vagrant命令打包

剩下的就是打包了：

```sh
vagrant package --output mynew.box
```
