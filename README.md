# CVE-2022-24934


## 漏洞概述

WPS Office安装时，会以管理员权限安装服务程序wpscloudsvr，该服务程序配置为手动启动，但错误配置了该服务程序所在文件夹的访问控制列表（ACL）属性，普通Users组成员仍然对该文件夹有读写权限。

## 影响范围

WPS Office版本小于11.2.0.10258均存在该漏洞。

（WPS版本号看最后一组，最后一组数字大即为新版本，11.1表示个人版，11.2表示企业版，11.6和11.8表示政企定制版）

## 利用场景

普通Users组成员在服务程序wpscloudsvr所在文件夹放置被劫持的DLL文件，以普通用户权限启动该服务，最终DLL被服务程序加载执行，实现本地提权。
（wpscloudsvr服务程序自身并不存在DLL劫持漏洞，可使用系统DLL劫持漏洞，测试时win7 6.1.7601 sp1 32位系统存在可被利用的系统DLL劫持漏洞，win10 10.0.18363.592 64位不存在可被利用的DLL劫持漏洞）

## 复现环境

操作系统：Win7 sp1。

WPS Office版本：WPS Office 11.2.0.10200。

复现工具：Process Explorer，Process Monitor，CFF Explorer，vs2008。

分析工具：Detect It Easy，OD，IDA，Openssl，数字签名复制工具sigthief.py。

## 漏洞详情&技术咨询

![图片](http://raqgyz5ky.hn-bkt.clouddn.com/111111.jpeg)

## 免责声明:

本篇文章仅用于技术交流学习和研究的目的，严禁使用文章中的技术用于非法目的和破坏，否则造成一切后果与发表本文章的作者无关。

### 中文版本:

本免责声明旨在明确指出，本文仅为技术交流、学习和研究之用，不得将文章中的技术用于任何非法目的或破坏行为。发表本文章的作者对于任何非法使用技术或对他人或系统造成的损害概不负责。

阅读和参考本文章时，您必须明确并承诺，不会利用文章中提供的技术来实施非法活动、侵犯他人的权益或对系统进行攻击。任何使用本文中的技术所导致的任何意外、损失或损害，包括但不限于数据损失、财产损失、法律责任等问题，都与发表本文章的作者无关。

本文提供的技术信息仅供学习和参考之用，不构成任何形式的担保或保证。发表本文章的作者不对技术的准确性、有效性或适用性做任何声明或保证。

### 英文版本:

This disclaimer is intended to clearly state that this article is solely for the purpose of technical exchange, learning, and research, and the use of the techniques mentioned in the article for any illegal purposes or destructive actions is strictly prohibited. The author of this article shall not be held responsible for any consequences resulting from the misuse of the techniques mentioned.

By reading and referring to this article, you must acknowledge and commit that you will not exploit the techniques provided in the article for any illegal activities, infringement of rights of others, or attacks on systems. The author of this article bears no responsibility for any accidents, losses, or damages caused by the use of the techniques mentioned in this article, including but not limited to data loss, property damage, legal liabilities, etc.

The technical information provided in this article is for learning and reference purposes only and does not constitute any form of warranty or guarantee. The author of this article makes no representations or warranties regarding the accuracy, effectiveness, or applicability of the techniques mentioned.
