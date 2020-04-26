## 简介

Quantumult X 是一款功能强大的网络工具，适用于 Web 开发人员和需要自定义代理的用户。

[官方示例](https://github.com/crossutility/Quantumult-X)

## 配置

欲往何方？

<details>
  <summary>盘古开天辟地天地共有，凭什么他玉皇大帝独掌乾坤</summary>
  https://cdn.jsdelivr.net/gh/DivineEngine/Profiles@master/Quantumult/Global.conf
</details>

<details>
  <summary>花果山水帘洞</summary>
  https://cdn.jsdelivr.net/gh/DivineEngine/Profiles@master/Quantumult/China.conf
</details>                           |

#### 一些特有的问题的注意

Quantumult 有一些奇怪设计，比如 Quantumult 中相同（行为）规则以最后出现的规则为准，以及 USER-AGENT 类型规则的低优先级设计。

到了 Quantumult X 后，Quantumult 的相同（行为）规则以最后出现的规则为准的设计废除，但是 USER-AGENT 类型规则的优先级被进一步降低导致无法单纯以 USER-AGENT 规则覆盖后续规则。

另外 HOST(DOAMIN) 类规则疑似优先级为 HOST > HOST-SUFFIX > HOST-KEYWORD。

优先级会导致一些不可用问题，在自定义规则时需自行注意。