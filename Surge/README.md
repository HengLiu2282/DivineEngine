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

除上述默认内置 list 外还有更多位于 [Ruleset](https://github.com/DivineEngine/Profiles/tree/master/Surge/Ruleset) 文件夹内，除非你知道你在干什么否则不要乱加 list，**规则不是越多越好**。

**Unbreak.list**：

不要单纯的理解为「广告白名单」，特别是如果你要引入其他「Ad.list」也一定要放在其之前！

**Advertising.list**：

Advertising.list 和 Rewrite 中的 reject 是专门针对 iOS 应用而写，虽然其中规则也能对移动网页甚至桌面网页起到效果，但并不建议在 macOS 及网关模式中使用。

**Streaming.list**:

国际流媒体服务，所有单独流媒体 list 除少数（TikTok、Himalaya 等）外均已内置于 Streaming.list 内，日常用法推荐为如在使用不同地区要求的服务如英国的 My5 或日本的 Hulu 时手动选择 Streaming 策略组下的服务器即可。

如果你觉得手动切换麻烦且拥有的服务器不少可以引入单独 list **直接**指定服务器策略，所以如果你的服务器很多**才需要**专门新增一个策略组如 Netflix 专门放置用于观看 Netflix 的服务器、引入 Netflix.list 并指定策略组策略。

⚠️ 注意：综上所述，**不需要**把单独流媒体 list 手动全部引入，基本全都内置于 Streaming.list 之中！另外，如果引入单独流媒体 list 需至少放置于 Streaming.list 前面。

**StreamingSE.list**：

流媒体服务特别版，主要支持为：

- 哔哩哔哩港澳台限定
- 爱奇艺台湾站
- 芒果TV国际版
- WeTV

以上的特殊性在于同一个域名/应用下同时用于大陆及限定区域（所以不能直接代理，影响大陆内容观看），所以使用方法为日常使用直连（DIRECT）当需要时手动切换到港澳台节点。

另外，以节省代理服务器流量出发，且（除了哔哩哔哩）视频内容均拥有大陆 CDN 节点，所以只有哔哩哔哩港澳台限定的部分视频内容才会走代理。

**[Apple](https://github.com/DivineEngine/Profiles/tree/master/Surge/Ruleset/Apple)**：

Apple 服务的 list 除了 Apple.list 均需至少放置于 Global.list 前面，而 Apple.list 需放在 Global.list 和 China.list 之间。

**Global.list 及 China.list**：

前者主要解决 DNS 污染问题，后者主要解决部分 CDN 带来的问题及节约 GeoIP 规则判断所耗费的时间问题。

#### 不需要去广告规则怎么办？

直接删除相关 Ruleset （及其策略组）和 Rewrite 即可。