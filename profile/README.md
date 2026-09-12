# Arlo Skill

**把项目经验整理成 AI 可以复用的技能。**

Arlo Skill 集中维护和分享面向实际项目的 Agent Skills：将工作方法、开发规范、内容模板和验证流程整理成独立技能，让 AI 在理解项目上下文后，按明确的方法完成工作。

这里的技能会随着实际使用持续完善，也会根据新的项目需求逐步扩充。

[浏览全部仓库](https://github.com/orgs/arlo-skill/repositories) · [GEO 网站与内容发布](https://github.com/arlo-skill/geo-web-publishing) · [AI 虚拟币事件监控](https://github.com/arlo-skill/ai-crypto-event-monitor) · [提出建议](https://github.com/arlo-skill/.github/issues)

## 技能目录

| 技能 | 解决什么问题 | 说明 |
|---|---|---|
| [geo-web-publishing](https://github.com/arlo-skill/geo-web-publishing) | 设计便于搜索引擎与联网 AI 发现的公开网站，并根据项目事实持续发布文章 | 落地页、HTML、分类标签、关联内链、robots.txt、Sitemap、内容核验与后台发布 |
| [ai-crypto-event-monitor](https://github.com/arlo-skill/ai-crypto-event-monitor) | 本地脚本持续监听虚拟币行情，仅在条件命中后触发 Codex 研究 | Go 监控模板、只读网页、多币行情与触发、对话维护持仓/挂单、持久化防重、市场/链上/资金流/新闻热度核验；部署后交付运行网址，默认 dry-run，无交易执行 |

每个技能独立维护，具体能力、使用条件和安装方法以对应仓库的 README 与 `SKILL.md` 为准。

## 一行安装

按需选择技能，安装到 Codex，供不同项目使用。

**GEO 网站与内容发布：**

```bash
npx --yes skills@latest add arlo-skill/geo-web-publishing --skill geo-web-publishing --agent codex --global --yes
```

**AI 虚拟币事件监控：**

```bash
npx --yes skills@latest add arlo-skill/ai-crypto-event-monitor --skill ai-crypto-event-monitor --agent codex --global --yes
```

需要 Node.js 22.20 或更高版本（含 npm/npx）和 Git。安装使用 [skills CLI](https://github.com/vercel-labs/skills)，包含技能入口及配套参考文件、模板；安装不会启动服务、定时任务或监控。Go 监控模板的运行还需要 Go 1.24+、macOS/Linux、可用的 Codex CLI 和真实目标任务 UUID。

- **仅用于当前项目**：在项目根目录运行，去掉 `--global`。
- **用于其他 AI 工具**：将 `--agent codex` 改成相应目标，例如 `claude-code` 或 `cursor`；支持情况见安装工具文档。
- **已有同名技能**：重新安装前，保留需要继续使用的本地定制。

安装后，在支持技能调用的环境中使用 `$geo-web-publishing` 或 `$ai-crypto-event-monitor`，并提供项目上下文与具体任务。完整步骤见对应仓库的 [GEO 安装说明](https://github.com/arlo-skill/geo-web-publishing#一行安装)或[监控技能安装说明](https://github.com/arlo-skill/ai-crypto-event-monitor#一行安装)。

查看 Codex 全局技能列表：

```bash
npx --yes skills@latest list --global --agent codex
```

## 在项目中使用

1. **选择技能**：阅读适用场景，选择与当前任务相关的技能。
2. **提供上下文**：说明项目、目标、现有约定和事实来源；涉及外部操作时明确接口与授权范围。
3. **执行并验证**：让 AI 按技能完成工作，核对实际结果，再根据使用反馈改进。

例如，可以用 GEO 技能设计官网文章结构，或按指定主题通过已授权接口发布内容；也可以用事件监控技能构建行情观察程序，在价格规则命中后调用 AI 核验市场和链上信息。

技能提供工作规范和模板，部分附带可运行的参考代码。项目配置、后台接口、账号权限及调度器由实际环境接入；敏感凭证通过环境变量、密钥管理器或连接器引用。虚拟币监控默认仅研究，不自动下单，技术验证通过不代表策略能够盈利。

## 我们重视什么

- **贴近真实项目**：从现有代码、文档和实际行为理解任务，避免凭空假设产品能力。
- **可以重复使用**：将通用方法与项目配置分开，按任务读取需要的参考资料。
- **遵循明确范围**：在已有授权内推进工作，涉及新增操作范围时说明所需条件。
- **结果能够核对**：说明完成了什么、如何验证，以及仍未确认的部分。

## 反馈与贡献

发现问题或有改进建议，可以在对应技能仓库提交 Issue 或 Pull Request。描述使用场景、预期结果和实际问题，会更有助于改进技能。

组织介绍、技能目录或新技能方向的建议，可以提交到 [.github 的 Issues](https://github.com/arlo-skill/.github/issues)。
