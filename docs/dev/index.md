# Ansible 开发

## 官方开发文档

http://docs.ansible.com/ansible/dev_guide/index.html

> 非常推荐大家看看 **官方文档**

## 环境

本次所用的环境

- ansible `2.3.0.0`

- os `Centos 6.7 X64`

- python `2.6.6`

## 介绍

Ansible 开发分为两大模块，一是`modules`，而是`plugins`。

首先，要记住这两部分内容在哪个地方执行？

- `modules` 文件被传送到 **远端主机** 并执行。
- `plugins` 是在 **ansible控制节点** 上执行的。

再者是执行顺序？

`plugins` 先于 `modules` 执行。

然后大家明确这两部分内容是干啥用的？

- `modules` 是ansible的核心内容，它使playbook变得更加简单明了，一个task就是完成某一项功能。ansible模块是被传送到远程主机上运行的。所以它们可以用远程主机可以执行的任何语言编写modules。

- `plugins` 是在 **ansible控制节点** 上执行的，用来辅助modules做一些操作。比如连接远程主机，拷贝文件到远程主机之类的。
