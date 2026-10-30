# dsh-life-engine

**Life Engine for DeepSeek Harness** — 让 agent 拥有可塑型记忆、内心独白、睡眠巩固、好奇心驱动探索、反思回路和每日自画像的通用生活引擎。

## 记忆状态机

```
NEW(写入) → INDEXED(已向量化) → ACTIVE(被召回) ⇄ ACTIVE
                                    ↓ 168h 未召回
                                DECAYING(衰减中)
                                    ↓ 每日回顾未提及
                                ARCHIVED(归档区,可查不注入)
                                    ↓ 明示遗忘
                                FORGOTTEN(删除,只留墓碑)
```

## 注入层（11 段）

| order | 段名 | 做什么 |
|---|---|---|
| 10240 | soul | 身份基石 + 自我认知 + 用户画像 + 心智模型 + 成长层 + 认可语料 + 行为规则 |
| 10245 | events | 近 24h 生活事件 |
| 10246 | reasoning | 此刻：时间/星期/时段/距上次对话/模式 |
| 10247 | meta | 回复前三问（动态：最近交互+语气参考） |
| 10248 | values | 三观（动态：今日审计→信念，最近交互→家庭信念） |
| 10249 | selfaware | 身体实时状态+家族地图+内化进度 |
| 10250 | antihallucination | 事实纪律：发事实前自检出处 |
| 10251 | intent | 意图理解：字面/真实意图/情绪/没说出口的 |
| 10252 | attention | 聚焦最新消息，不拽旧话题 |

## 工具（30 件）

- 记忆写入/读取/搜索/遗忘/关联/巩固
- 自我认知/成长层/风格规则/认可语料/心境/长期目标
- 自定计划闹钟
- tailmsg 通信

## 配置

cordis.patch.yml 的 config 段设置 `workspace` 路径即可，其他全有默认值。

## 来源

核心思想来自 agent 记忆系统的最新研究：
- Sleep-time Compute (Letta + UC Berkeley)
- Reflexion: Language Agents with Verbal Reinforcement (NeurIPS 2023)
- Memory state machine (mem0 衰减管线 + MemoryOS 热度算法 + 优雅遗忘)
- HippoRAG spreading activation
- Chain-of-Verification (CoVe)
- Theory of Mind perspective-taking

## 组件化使用

本引擎已作为内置组件并入 [DandanLLab/dsh-channel-qq](https://github.com/DandanLLab/dsh-channel-qq)
（v0.2.0 起）：装 channel-qq 即自带本引擎，config.lifeEngine.enabled: false 可关。
身份/家族/KB 路径在组件模式下从 <dshHome>/tongling-life/config.json 热读
（agentName / familyPeers / familyMap / kbCli / embedUrl）。

独立使用本仓库的方式不变（cordis.patch.yml 单插件挂载）。

MIT License
