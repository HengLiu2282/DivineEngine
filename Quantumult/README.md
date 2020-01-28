## 简介

Quantumult X 是一款功能强大的网络工具，适用于 Web 开发人员和需要自定义代理的用户。

## 规则

| 版本 | 下载                                                         | 描述 |
| ---- | ------------------------------------------------------------ | ---- |
| Pro  | https://raw.githubusercontent.com/DivineEngine/Profiles/master/Quantumult/Pro.conf |      |

## 帮助

**官方示例**

- [Github](https://github.com/crossutility/Quantumult-X)

### 说明

#### 关于 Filter Remote

要求排序如下：

1. [必须] Unbreak.list - 用于修正后续规则行为
2. [可选] Advertising.list - 广告
3. [可选] Privacy.list - 隐私（行为分析、隐私追踪）
4. [可选] Hijacking.list - 劫持（运营商、恶意网址）
5. [必须] Streaming.list - 流媒体服务
6. [可选] StreamingSE.list - 流媒体服务限定版(大陆面向港澳台)
7. [必须] Global.list - 国际网络分流
8. [必须] China.list - 国内网络分流

除上述默认内置 list 外还有更多位于 [Filter](https://github.com/DivineEngine/Profiles/tree/master/Quantumult/Filter) 文件夹内，使用时需注意：

1. 除非你知道你在干什么否则不要乱加 list，**规则不是越多越好**。

2. 所有单独流媒体 list 除少数（TikTok、Himalaya 等）外均已内置于 Streaming.list 内，日常推荐用法为如在使用不同地区要求的服务如英国的 My5 或日本的 Hulu 时手动选择 Streaming 策略组下的服务器即可。
   如果你觉得手动切换麻烦且服务器不多可以引入单独 list **直接**指定服务器策略，所以如果你的服务器很多，**才需要**专门新增一个策略组如 Netflix 专门放置用于观看 Netflix 的服务器、引入 Netflix.list 并指定策略组策略。

   ⚠️ 注意：单独流媒体 list 需至少放置于 Streaming.list 前面。
综上所述，不需要把每一个流媒体 list 全部引入。
   
3. Apple 服务的 list 需至少放置于 Global.list 前面。

#### 不需要去广告规则怎么办？

直接删除相关 Filter 和 Rewrite 即可。

#### 关于 Quantumult X 一些特有的问题

因为 Quantumult 的一些奇怪设计，比如 Quantumult 中相同（行为）规则已最后出现的为准，以及 USER-AGENT 类型规则的低优先级设计导致 Unbreak 中对于一些广告游戏只能关闭 Quantumult 后才能正常游戏。

到了 Quantumult X 后，Quantumult 的相同（行为）规则以最后出现为准的设计废除，但是 USER-AGENT 类型规则的优先级被进一步降低导致无法单纯以 USER-AGENT 规则覆盖后续规则。

且 HOST(DOAMIN) 类规则疑似优先级为 HOST > HOST-SUFFIX > HOST-KEYWORD 会导致更多的「补丁」规则和不可用行为，在自定义规则时需特别注意。