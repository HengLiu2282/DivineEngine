## 简介

Surge 是一个面向高级用户的网络工具箱，也是一个高性能的 HTTP/SOCKS5 代理服务器。它能够拦截和记录网络流量的汇总，同时根据灵活的规则体系将流量传输到其他代理服务器。

[官方网站](https://nssurge.com/)

## 规则

| 版本    | 下载                                                         | 描述               |
| ------- | ------------------------------------------------------------ | ------------------ |
| Legacy  | https://raw.githubusercontent.com/DivineEngine/Profiles/master/Surge/Legacy.conf | Surge 2            |
| NextGen | https://raw.githubusercontent.com/DivineEngine/Profiles/master/Surge/NextGen.conf | Surge 3 及后续版本 |

## 帮助

**官方文档**

- [Manual](http://manual.nssurge.com/)

**导入教程**

- [Surge 配置导入](https://www.notion.so/Surge-c5dd1d4577a14912948ec024aa1e0b21)

### 说明

#### 关于 Ruleset

要求排序如下：

1. [必须] Unbreak.list - 用于修正后续规则行为
2. [可选] Advertising.list - 广告（建议仅 iOS 端开启）
3. [可选] Privacy.list - 隐私（行为分析、隐私追踪）
4. [可选] Hijacking.list - 劫持（运营商、恶意网址）
5. [必须] Streaming.list - 流媒体服务
6. [可选] StreamingSE.list - 流媒体服务特别版（大陆面向港澳台）
7. [必须] Global.list - 国际网络分流
8. [必须] China.list - 国内网络分流

除上述默认内置 list 外还有更多位于 [Ruleset](https://github.com/DivineEngine/Profiles/tree/master/Surge/Ruleset) 文件夹内，使用时需注意：

1. 除非你知道你在干什么否则不要乱加 list，**规则不是越多越好**。

2. 所有单独流媒体 list 除少数（TikTok、Himalaya 等）外均已内置于 Streaming.list 内，日常推荐用法为如在使用不同地区要求的服务如英国的 My5 或日本的 Hulu 时手动选择 Streaming 策略组下的服务器即可。
   如果你觉得手动切换麻烦且服务器不多可以引入单独 list **直接**指定服务器策略，所以如果你的服务器很多，**才需要**专门新增一个策略组如 Netflix 专门放置用于观看 Netflix 的服务器、引入 Netflix.list 并指定策略组策略。

   ⚠️ 注意：单独流媒体 list 需至少放置于 Streaming.list 前面。
综上所述，不需要把每一个流媒体 list 全部引入。
   
3. Apple 服务的 list 需至少放置于 Global.list 前面。

最后**强调**：Advertising.list 和 Rewrite 中的 reject 是专门针对 iOS 应用而写，虽然其中规则也能对移动网页甚至桌面网页起到效果，但并不建议在 macOS 及网关模式中使用。

#### 不需要去广告规则怎么办？

直接删除相关 Rulteset （及其策略组）和 Rewrite 即可。