# DeepSeek Harness 生态周报·001

> 统计周期：2026-09-21—2026-09-27（UTC）  
> 数据截止：2026-09-27 10:20 UTC  
> 栏目框架：官方信息 + 生态规模 + 增长趋势 + 项目健康度 + 真实采用 + 编辑判断 + 栏目运营效果

## 一句话结论

DeepSeek Harness 还处在高速扩张的早期：`dsh-plugin` 候选仓库一周增长 632 个（+4.0%），头部 100 个仓库中 76% 在本周有推送；但 topic 只能表示「自我声明兼容」，尚不能等同于 16,303 个可安装、可维护、有真实用户的插件。

## 本期看板

| 维度 | 本期数值 | 解读 |
| --- | ---: | --- |
| `dsh-plugin` 候选仓库 | 16,303 | GitHub topic 搜索结果，不是经过审核的插件数 |
| 候选仓库周净增 | +632（+4.0%） | 上期基线为 15,671 |
| 官方主仓库 | 237,263 Stars / 28,511 Forks | 关注度高，但 Star/Fork 不代表活跃安装 |
| 官方本周发布 | 4 个预发布版本 | `0.1.7-alpha.1` 至 `0.1.7-rc.2` |
| 头部样本活跃度 | 76 / 100 | 本周有 push；包含官方主仓库 |
| 头部样本许可证覆盖 | 95 / 100 | GitHub API 能识别到 license |
| 头部非官方样本关注度 | 823,194 Stars / 77,731 Forks | 前 99 个非官方仓库合计，不去重用户 |
| 真实安装、活跃用户、留存 | 未公开 | 本期不用 Star 代替这些指标 |

---

## 1. 官方信息

### 1.1 版本节奏

官方主仓库 [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) 于本周发布了 4 个 `0.1.7` 预发布版本：

| 日期（UTC） | 版本 | 阶段 |
| --- | --- | --- |
| 09-22 | [`dsh-v0.1.7-alpha.1`](https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.1.7-alpha.1) | Alpha |
| 09-22 | [`dsh-v0.1.7-alpha.2`](https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.1.7-alpha.2) | Alpha |
| 09-23 | [`dsh-v0.1.7-rc.1`](https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.1.7-rc.1) | Release Candidate |
| 09-24 | [`dsh-v0.1.7-rc.2`](https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.1.7-rc.2) | Release Candidate |

### 1.2 值得关注的产品信号

1. **插件已从「可安装」走向「可管理」。** `0.1.7-rc.1` 支持安装、配置、启停和运行时卸载，并增加官方源、国内镜像与自定义源选择。
2. **Harness 的形态超过了对话客户端。** 新版覆盖 Headless JSON 事件流、SSH 远程工作区、MCP 资源、Browser/Computer Use 以及后台任务。
3. **官方开始处理「长时间运行」。** `rc.2` 引入持久化定时任务，桌面端关窗后任务可继续运行，这会扩大自动化类插件的使用空间。
4. **当前仍是预发布阶段。** 一周内从 Alpha 推进到 RC，节奏快；相应地，插件作者应预留兼容性测试成本，不应把 RC 当作稳定版承诺。

---

## 2. 生态规模

### 2.1 统一口径

本报告将 GitHub [`dsh-plugin` topic](https://github.com/topics/dsh-plugin) 视为「候选生态池」。截止统计时间，GitHub Search API 返回 16,303 个仓库。

这个数字需要三点限定：

- topic 由仓库维护者自行添加，不代表官方审核或收录；
- 一个通用项目只要声明兼容 DSH 便可进入样本，不一定是 DSH 专用插件；
- GitHub Search API 的 `total_count` 适合观察方向，不宜当作财务级精确计数。

### 2.2 头部样本的技术与品类信号

下列数据来自 Star 前 100 仓库的 topic，为**多标签口径**，因此各类之和不等于 100：

| 信号 | 样本数 | 编辑解读 |
| --- | ---: | --- |
| AI Agent | 27 | Agent 与编排仍是最大主线 |
| Agent Skills | 18 | Skill 正成为跨 Harness 的分发单元 |
| MCP | 13 | 工具和资源互操作是关键基础设施 |
| 记忆 / RAG | 10 | `memory` 与 `rag` 相关 topic 去重后的项目数 |
| 本地优先 | 8 | 隐私、本地工作区与桌面端是明显分支 |
| Claude Code 兼容 | 29 | 不少项目选择多 Harness 分发 |
| Codex 兼容 | 24 | 生态竞争也是互操作竞争 |
| OpenCode 兼容 | 15 | DSH 并非这些项目的唯一入口 |

头部 100 个仓库的主要语言为 TypeScript（44）、Python（23）、JavaScript（18）、Go（5）和 Rust（5）。Web/Node 生态占优势，但 Python 仍是 Agent、RAG 和自动化插件的重要载体。

---

## 3. 增长趋势

### 3.1 仓库规模

| 日期 | 候选仓库 | 净增 | 增幅 |
| --- | ---: | ---: | ---: |
| 2026-09-21 | 15,671 | — | — |
| 2026-09-27 | 16,303 | +632 | +4.0% |

这一增长表明「声明兼容 DSH」正在快速普及，但不能推导出安装量也增长了 4.0%。下期应继续使用同一查询条件，避免口径变更被误认为生态增长。

### 3.2 本期总榜（排除官方主仓库）

| # | 项目 | Stars | Forks | 主要方向 |
| ---: | --- | ---: | ---: | --- |
| 1 | [nexu-io/open-design](https://github.com/nexu-io/open-design) | 98,247 | 11,393 | 设计与多模态内容生成 |
| 2 | [ruvnet/ruflo](https://github.com/ruvnet/ruflo) | 73,353 | 8,710 | Agent 编排与工作流 |
| 3 | [tt-a1i/archify](https://github.com/tt-a1i/archify) | 72,461 | 4,897 | 架构可视化与 Architecture as Code |
| 4 | [reactive-resume/reactive-resume](https://github.com/reactive-resume/reactive-resume) | 43,462 | 4,790 | 简历生产力 |
| 5 | [volcengine/OpenViking](https://github.com/volcengine/OpenViking) | 38,765 | 3,025 | Agent 记忆与上下文数据库 |
| 6 | [esengine/DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix) | 35,713 | 2,420 | 编码 Agent |
| 7 | [freestylefly/awesome-gpt-image-2](https://github.com/freestylefly/awesome-gpt-image-2) | 33,577 | 3,231 | 图像生成资源 |
| 8 | [Tencent/WeKnora](https://github.com/Tencent/WeKnora) | 30,449 | 4,074 | RAG 与知识库 |
| 9 | [anywhere-labs/dsh-desktop](https://github.com/anywhere-labs/dsh-desktop) | 29,137 | 1,388 | DSH 桌面端 |
| 10 | [Molunerfinn/PicGo](https://github.com/Molunerfinn/PicGo) | 27,258 | 2,328 | 图片上传与内容工具 |

### 3.3 趋势榜状态

**本期不发布伪精确的 Star 周增榜。** 上期只保存了候选总数，没有保存单仓库 Star 快照；现在用累计 Star 倒推「周趋势」会让老项目天然占优。本期已给出总榜，本次数据应作为下期趋势榜的比较基线。

---

## 4. 项目健康度

### 4.1 头部 100 样本

| 指标 | 结果 | 说明 |
| --- | ---: | --- |
| 过去 7 天有 push | 76% | 仅表示代码活动，不代表发布了可用版本 |
| 可识别许可证 | 95% | 5 个样本未由 GitHub API 识别出 license |
| 已归档 | 0 | 头部样本中未发现 archived 仓库 |
| 未解决 Issue | 8,089 | 只适合作为工作量线索，不同项目的 Issue 口径不可直接比较 |

### 4.2 官方仓库

- 开源协议：MIT。
- 最后推送：2026-09-24，距截止时间 3 天。
- GitHub Contributors API 返回 54 名贡献者。
- API 显示 0 个 open issue；这不能直接解读为「没有缺陷」，也可能与官方的问题收集流程有关。

### 4.3 风险提示

1. **Topic 污染风险：** 通用项目、列表型仓库和教程也会进入「插件」样本。
2. **版本兼容风险：** 主产品仍在 `0.1.x` 预发布阶段，稳定 API 不应被视为已承诺。
3. **单一平台偏差：** 本期健康度仅观测 GitHub，没有覆盖 npm/PyPI 发布、插件市场安装和私有部署。

---

## 5. 真实采用

### 5.1 目前能确认的代理信号

- 官方主仓库有 28,511 Forks 和 1,029 Watchers，表明存在持续关注与二次开发意愿。
- 前 99 个非官方仓库累计 823,194 Stars、77,731 Forks，Star 中位数为 2,223。这反映头部项目本身的社区基础，不能全部归因于 DSH。
- 前 100 中出现 Claude Code、Codex 和 OpenCode 等兼容标签，说明「一次开发、多 Harness 分发」已是显著策略。

### 5.2 不能由公开数据证明的事

本期未找到统一、可复核的插件安装量、活跃用户、7/30 日留存、任务成功率或卸载率。因此：

- 不把 Star 写成「用户数」；
- 不把 topic 仓库数写成「可安装插件数」；
- 不用 GitHub push 代替插件的成功运行率。

### 5.3 建议与官方/市场方共建的数据集

| 指标 | 最小分组 | 隐私要求 |
| --- | --- | --- |
| 安装量 / 成功安装率 | 插件、版本、OS | 只公布聚合值，设最小样本门槛 |
| 周活跃安装 | 插件、版本 | 不上报任务内容和工作区信息 |
| 7/30 日留存 | 安装 cohort | 使用随机、可重置标识符 |
| 启动成功率 / 错误率 | 插件版本、Harness 版本 | 错误签名去敏，不上传原始日志 |
| 卸载率 | 插件、安装 cohort | 报告区间值，避免识别小样本作者 |

---

## 6. 编辑判断

### 6.1 本周三个重要判断

**判断一：生态的关键变化不是「又多了 632 个仓库」，而是官方正在补齐插件分发和运行的底层能力。** 插件管理、多源安装、Headless、MCP 资源和后台任务会比单纯的仓库数增长更长期地决定生态上限。

**判断二：DSH 生态当前更像「兼容层」，而不是完全独立的应用市场。** 头部项目大量同时标注 Claude Code、Codex、OpenCode、MCP 和 Skills，开发者追求的是跨 Harness 分发。对 DSH 来说，兼容性和分发体验可能比独占插件更重要。

**判断三：当前的最大数据缺口是「使用」。** 工程活跃度很高，但我们仍无法回答「哪个插件被最多人稳定使用」。在安装与留存数据出现前，所有榜单都应标注它衡量的是「GitHub 关注度」而不是「用户采用」。

### 6.2 编辑精选

- **生态入口：** [awesome-dsh-plugin/awesome-dsh-plugin](https://github.com/awesome-dsh-plugin/awesome-dsh-plugin)。适合观察社区收录标准和新项目，但列表收录仍不等于可用性审计。
- **原生体验观察：** [anywhere-labs/dsh-desktop](https://github.com/anywhere-labs/dsh-desktop)。它直接围绕 DSH 插件生态构建桌面体验，比「增加一个兼容 topic」更能反映原生生态投入。
- **底层能力观察：** [volcengine/OpenViking](https://github.com/volcengine/OpenViking)。记忆和上下文层会直接影响长时间运行 Agent 的实用性，也与官方本周强化后台任务的方向呼应。

---

## 7. 栏目运营效果

### 7.1 首期状态

这是按新框架制作的首期报告，发布前没有阅读、完读、收藏、转发、订阅转化或外链点击数据。因此本期只定义基线，不填写虚构数值。

### 7.2 发布后 7 天复盘表

| 目标 | 指标 | 计算口径 | 首期数值 |
| --- | --- | --- | --- |
| 触达 | 有效阅读 | 停留 ≥ 10 秒或滚动 ≥ 25% 的去重访客 | 待发布后回填 |
| 内容质量 | 完读率 | 到达文末的有效阅读 / 有效阅读 | 待回填 |
| 长期价值 | 收藏率 | 收藏 / 有效阅读 | 待回填 |
| 传播 | 转发率 | 可识别转发 / 有效阅读 | 待回填 |
| 留存 | 订阅转化率 | 本期带来的新订阅 / 有效阅读 | 待回填 |
| 导流 | 项目点击率 | 项目外链去重点击 / 有效阅读 | 待回填 |
| 社区供给 | 有效自荐数 | 符合最低收录标准的项目自荐 | 待回填 |

发布时所有项目外链应附加统一 UTM 参数，且不同模块使用不同 `utm_content`，以区分总榜、编辑精选和正文提及带来的点击。

### 7.3 下期内容实验

1. 保持固定标题和发布时间，建立可比基线。
2. 为「纯榜单」和「编辑精选」分配独立点击标记，验证读者更需要数据还是判断。
3. 在文末只设一个主 CTA：订阅下期周报；项目自荐作为次级 CTA。
4. 发布 24 小时和 7 天各回填一次，不以单日流量判断长文效果。

---

## 8. 下周观察清单

- `0.1.7` 是否进入稳定版，以及预发布期的插件兼容问题。
- 持久化定时任务是否催生新的自动化插件。
- 前 100 仓库的 Star/Fork 周增，首次发布可复核的趋势榜。
- 头部项目的 DSH 集成是原生实现，还是仅增加 topic/文档声明。
- 是否出现可公开复核的安装量、企业案例或留存数据。

## 9. 方法与数据字典

### 9.1 数据源

- GitHub Search API：`topic:dsh-plugin`，分别获取 `total_count` 与按 Star 降序的前 100 仓库。
- GitHub Repositories / Releases / Contributors API：官方仓库元数据、发布日志与贡献者数。
- 上期快照：2026-09-21 记录的 15,671 个候选仓库。

### 9.2 关键定义

- **候选仓库：** 统计时点被 GitHub Search API 命中 `topic:dsh-plugin` 的仓库。
- **活跃样本：** `pushed_at` 不早于 2026-09-20 00:00 UTC 的前 100 仓库。
- **总榜：** 累计 Star 排序，排除官方主仓库。
- **趋势榜：** 同一仓库两期快照间的 Star 增量排序；首期没有单仓库基线，故不发布。
- **真实采用：** 安装、活跃使用、留存或可验证的生产案例；Star、Fork 和 topic 均只是代理信号。

### 9.3 可复核查询

```text
GET https://api.github.com/search/repositories?q=topic%3Adsh-plugin&sort=stars&order=desc&per_page=100
GET https://api.github.com/repos/deepseek-ai/deepseek-harness
GET https://api.github.com/repos/deepseek-ai/deepseek-harness/releases
GET https://api.github.com/repos/deepseek-ai/deepseek-harness/contributors?per_page=100&anon=1
```

GitHub 数据会持续变化，重跑上述查询时不应期待与本报告的截止时点完全相同。
