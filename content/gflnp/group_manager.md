---
title: '群管理员手册'
publishDate: 2022-10-31
date: 2023-05-17
---

> 测试中, 内容可能会改动

# 用法

本文档用于描述群管理员相关信息，包含以下章节：

-   申请条件
-   要求
-   职责
-   奖励
-   指令

## 申请条件

必要条件:

-   需在此服务器中游玩时间 > 3000 分钟
-   需在此服务器中达到 1 月人形

二选一条件:
条件 1:

-   在此服务器游玩时间 > 5000 分钟

条件 2:

-   需在此游戏(steam 时长)游玩时间 > 600 小时

## 要求

-   审核搁置时间不能超过 48 小时
-   每次执行时需要向服务器管理员报告

## 职责

-   负责处理举报相关审核

## 奖励

-   举报审核处理后根据举报文档将获得彩票 \* 1

## 指令

群管理员除了可用普通玩家已有指令外, 还可有额外的可用指令

针对这些指令, 标记为 颜色 的指令在执行时 需** 向管理员汇报**

额外指令分为 2 种:

-   封禁指令
-   普通游戏指令

### 封禁指令

#### tempban

临时封禁玩家, 需要一个参数

> tempban KREEDZT

#### clearban

解除临时封禁玩家的封禁, 需要一个参数

> clearban KREEDZT

#### tbdebug

显示临时封禁玩家列表

#### refresh_ban

刷新封禁玩家列表

> 注意: 该命令不会存在反馈, 仅会通知到服务端执行, 需要配合服务器管理员修改封禁列表后操作

### 普通游戏指令

#### buy

> 8 月 13 日更新: 购买价格为默认的 3 倍, 但 不限制 使用次数

购买物品

-   6: 军械车
-   7: 仓库车
-   101: MAA 坦克
-   102: 豹二主战坦克
-   103: T-14 主战坦克
-   201: M2A2 战车
-   202: GT-C 步战车
-   203: BMP-3 步战车
-   301: 运兵车
-   302: 运兵车(另一个阵营)
-   502: 悍马车

#### cgc

改变玩家颜色

> cgc #FF00FF

#### whereami

显示当前位置

#### sidinfo

查询玩家 sid，需要一个参数

> sidinfo KREEDZT

#### kick_id

#### kick

> 踢出玩家, 例: kick KREEDZT

#### 0_win

> 本局游戏获胜

#### 1_win

> 本局游戏失败(可当做重开指令)

#### 1_lose

#### 1_own

#### 0_own
