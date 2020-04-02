# RocketMQ 自动化安装与部署

本项目是由 [Websoft9](http://www.websoft9.com) 研发的 [RocketMQ](http://rocketmq.apache.org/) 自动化安装程序，开发语言是 Ansible。使用本项目，只需要用户在 Linux 上运行一条命令，即可自动化安装 RocketMQ，让原本复杂的安装过程变得没有任何技术门槛。  

本项目是开源项目，采用 LGPL3.0 开源协议。

## 配置要求

安装本项目，确保符合如下的条件：

| 条件       | 详情       | 备注  |
| ------------ | ------------ | ----- |
| 操作系统       | Ubuntu16.04以上       |   |
| 公有云| AWS, Azure, 阿里云, 华为云, 腾讯云 | 可选 |
| 私有云|  KVM, VMware, VirtualBox, OpenStack | 可选 |
| 服务器配置 | 最低1核1G，安装时所需的带宽不低于10M |  建议采用按量100M带宽 |

更多要求请参考[官方安装文档](http://rocketmq.apache.org/docs/quick-start/)

## 组件

包含的核心组件为：RocketMQ, Erlang

更多请见[参数表](/docs/zh/stack-components.md)

## 本项目安装的是 RocketMQ 最新版吗？

本项目通过下载 RocketMQ 源码进行安装，下载链接存储在：[role/rocketmq/default/main.yml](/roles/rocketmq/defaults/main.yml)。我们会定期检查并测试官方版本的可用性，尽可能保证用户可以顺利安装最新版。

```
rocketmq_download_url: "https://archive.apache.org/dist/rocketmq/4.6.1/rocketmq-all-4.6.1-source-release.zip"
```

如果你发现不是最新版本，请到 [RocketMQ Releases页面](https://github.com/apache/rocketmq/releases)获取最新版源码下载链接，再修改 [main.yml](/roles/rocketmq/defaults/main.yml) 中的 ```rocketmq_download_url``` 变量值即可安装最新版 RocketMQ。  

## 安装指南

以 root 用户登录 Linux，运行下面的**一键自动化安装命令**即可启动自动化部署。若没有 root 用户，请以其他用户登录 Linux 后运行 `sudo su -` 命令提升为 root 权限，然后再运行下面的脚本。

```
wget -N https://raw.githubusercontent.com/Websoft9/ansible-linux/master/scripts/install.sh; bash install.sh -r racketmq
```

脚本后启动，就开始了自动化安装，必要时需要用户做出交互式选择，然后耐心等待直至安装成功。

**安装中的注意事项：**  

1. 操作不慎或网络发生变化，可能会导致SSH连接被中断，安装就会失败，此时请重新安装
2. 安装缓慢、停滞不前或无故中断，主要是网络不通（或网速太慢）导致的下载问题，此时请重新安装

多种原因导致无法顺利安装，请使用我们在公有云上发布的 [RacketMQ镜像](https://apps.websoft9.com/racketmq) 的部署方式


## 文档

文档链接：https://support.websoft9.com/docs/rocketmq/zh

## FAQ

- 命令脚本部署与镜像部署有什么区别？请参考[镜像部署-vs-脚本部署](https://support.websoft9.com/docs/faq/zh/bz-product.html#镜像部署-vs-脚本部署)
- 本项目支持在 Ansible Tower 上运行吗？支持
