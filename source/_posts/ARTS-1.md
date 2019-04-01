---
title: ARTS 第 1 周
date: 2019-04-01 11:40:00
tags:
---

## algorithm

---

### 问题描述

[Two Sum](https://leetcode.com/problems/two-sum/)：Given an array of integers, return indices of the two numbers such that they add up to a specific target.You may assume that each input would have exactly one solution, and you may not use the same element twice.  
**Example**:  

```bash
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

### 我的解法

```JavaScript
/**
* @param {number[]} nums
* @param {number} target
* @return {number[]}
*/
const twoSum = function function_name(nums, target) {
     if (nums.length === 2) {
          return [0, 1]
     }

     let map = new Map()
     for (let [i, num] of nums.entries()) {
          let diff = target - num

          if (map.has(diff)) {
               return [map.get(diff), i]
          }
          else {
               map.set(num, i)
          }
     }
}
```

## Review - [How Computers Work](https://www.khanacademy.org/computing/computer-science/how-computers-work2) 1~3 课笔记

---

*How Computers Work* 是 code.org 为儿童制作的解释计算机工作原理的系列课。

- 同人类以前发明的那些帮助自己干体力劳动的机器不一样，计算机处理的对象不是物理世界里的实物，而是虚拟的信息。
- 无论是最古老的巨型计算机，还是如今那些功能繁杂的计算机，它们的基本功能只有四项：
  - Input：**接收**信息；向计算机输入方式多种多样：键盘、鼠标、摄像机、体感设备……
  - Store：把接收的信息作为数据**储存**
  - Process：使用算法（一系列指令）**处理**内存中的数据，处理的结果继续储存或输出
  - Output：**输出**信息；计算机输出信息的样式也同样很多：文字，音视频，游戏，虚拟现实等，电脑联网后，一台电脑输出的信息还可以成为另一台电脑输入的信息
- 同人类使用语言来表征（represent）一切认识的事物一样，计算也拥有一套自己语言，用于表征一切接受的一切信息（数字，文本，图像和声音）。
- 计算机这套语言的最小单位的载体（文字）是一条电线（电子电路），这条电线有通电和不通电两个状态，可以用于分别标示“是/否”，“对/错”，“0/1”这样的概念。我们知道，借助二进制计数系统，仅用“0”和“1”两个符号就可以表示所有数字，也就是说，8 条计算机电路，就可以表示 0~250 之间的数字，电路数量也多，能表示的数字就越多。
- 而后基于数字，人们又建立其他的文字系统，让计算机可以把它接受的其他类型的信息都“翻译”成二进制数字
  - 表示文字：建立一个把自然语言中的每个字符（字母、象形文字、标点符号等）与一个二进制数字一一对应的系统（字符编码）
  - 表示图像：建立像素颜色和二进制数值的对应关系
  - 表示声音：建立声音模拟信号和二进制数值的对应关系

## Tips - 利用 vlmcsd 搭建 KMS 服务器

---
起因：半年之前在笔记本的售后处修电脑顺便买了 Windows 10 专业版，前几天显示激活码已失效。网上搜索了一下发现之前的是用 KMS 激活的，有效期只有 180 天，于是自己用开源的激活工具 [vlmcsd](https://github.com/Wind4/vlmcsd) 在 VPS 上搭 KMS 服务器重新激活。

### 1. 搭建服务器

下载并解压 vlmcsd，根据自己 VPS 的操作系统选择服务器程序

    cd ./vlmcsd-1108-2017-01-19-Hotbird64/binaries/Linux/intel/static && cp vlmcsd-x64-musl-static kms && mv kms /usr/bin
修改权限

    chmod +x /usr/bin/kms

启动服务

    kms

这个服务侦听的端口是1688，可以输入以下命令查看运行状态

    netstat -ap | grep 1688

加程序加入开机启动列表（在下列的文件中加入 `/usr/bin/kms`）

    vim /etc/rc.local

### 2. Windows 本地激活

以管理员身份打开命令提示符，然执行下列命令激活

    cd /d "%SystemRoot%\system32"
    slmgr /skms 你的VPS的IP或者绑定的域名
    slmgr /ato
    slmgr /xpr
输入 slmgr.vbs -dlv 可查询激活状态

### 参考：

[在VPS中利用vlmcsd搭建KMS激活服务器](https://imeiji.github.io/2018/02/08/利用vlmcsd搭建KMS激活服务器/)

[Linux上利用vlmcsd搭建KMS服务器](wwww.lvmoo.com/517.love)

## Share

---
这周没写文章