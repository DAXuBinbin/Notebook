# Docker 使用

## 一、概要

Docker 是一个[开源](https://baike.baidu.com/item/开源/20720669)的应用容器引擎，让开发者可以打包他们的应用以及依赖包到一个可移植的[镜像](https://baike.baidu.com/item/镜像/1574)中，然后发布到任何流行的 [Linux](https://baike.baidu.com/item/Linux)或[Windows](https://baike.baidu.com/item/Windows/165458)操作系统的机器上，也可以实现[虚拟化](https://baike.baidu.com/item/虚拟化/547949)。容器是完全使用[沙箱](https://baike.baidu.com/item/沙箱/393318)机制，相互之间不会有任何接口。

## 二、操作

### 1.从tar压缩包加载离线镜像

```shell
docker load -i  demo.tar
```



