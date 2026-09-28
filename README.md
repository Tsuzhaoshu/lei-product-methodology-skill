# 雷氏产品方法论 · Skill

> 借鉴雷军的产品工程方法论（专注、极致、口碑、快），为产品定义、极致打磨与用户参与设计提供结构化工作流。

![version](https://img.shields.io/badge/version-1.0.0-blue)
![license](https://img.shields.io/badge/license-MIT-green)
![status](https://img.shields.io/badge/status-stable-brightgreen)

---

## 这是什么

一个可即装即用的 **Agent Skill**，把"雷军产品方法论"压缩成三阶段工作流（产品定义 → 死磕细节 → 用户参与），帮助你在资源有限的场景下做出有口碑的产品决策。

适用人群：
- 初创团队定义第一款产品
- 成熟产品做体验攻坚
- 任何想用"专注 + 极致 + 口碑 + 快"思路推进项目的人

不适用：
- 需要铺量覆盖全价格段的防御性产品策略
- 明确要求"快速铺量"或"覆盖尽可能多用户"的场景

---

## 核心原则（4 条）

| 原则 | 一句话 | 检查问题 |
|------|--------|----------|
| 单点切入，克制贪婪 | 切口越小，压强越大 | 是否在试图解决多个问题？ |
| 对"不完美"零容忍 | 极致是可打磨的习惯 | 哪些熟视无睹的丑陋细节？ |
| 口碑源于"超出预期" | 体验必须超出心理预期 | 哪个点能让用户"哇"一声？ |
| 快节奏迭代 | 参考周更节奏逼近最优 | 反馈响应有多快？ |

---

## 安装方式（按渠道选择）

本 Skill 同时兼容 **Claude Code**、**GitHub Copilot**、**TRAE** 以及任何支持 Agent Skills 开放标准的工具。选择你使用的渠道：

### 渠道一：Claude Code（最成熟）

**项目级（团队共享）**
```bash
# 克隆本仓库到项目根目录的 .claude/skills/ 下
git clone <repo-url> /tmp/lei-skill
cp -r /tmp/lei-skill/.claude/skills/lei-product-methodology  your-project/.claude/skills/
```
任何 clone 该项目的人都能自动获得此 Skill。

**个人级（跨项目）**
- macOS/Linux：复制到 `~/.claude/skills/lei-product-methodology/`
- Windows：复制到 `C:\Users\<你的用户名>\.claude\skills\lei-product-methodology\`

**Plugin Marketplace（公开发布）**
在 `.claude-plugin/marketplace.json` 中注册：
```json
{
  "name": "lei-product-methodology-marketplace",
  "plugins": [
    {
      "name": "lei-product-methodology",
      "source": "./lei-product-methodology",
      "description": "雷军产品工程方法论 Skill"
    }
  ]
}
```
用户通过 Claude Code 的 `/plugin` 命令添加本仓库地址即可安装。

### 渠道二：GitHub Copilot

GitHub Copilot 原生支持 `SKILL.md` 格式，自动从 `.claude/skills/` 目录发现。

**项目级**：将本仓库的 `.claude/skills/lei-product-methodology/SKILL.md` 提交到你的 GitHub 仓库即可。

**个人级**：复制到 `~/.copilot/skills/lei-product-methodology/`。

### 渠道三：TRAE（当前环境原生）

将 `.trae/skills/lei-product-methodology/` 目录置于工作区根目录，TRAE 会自动扫描并发现。技能会出现在可用 Skill 列表中，按触发词或 `/lei-product-methodology` 调用。

### 渠道四：企业私有 Skill 平台（SkillHub）

适合团队/企业内部分发，支持私有化部署、版本管理、RBAC 权限治理和审计日志。

```bash
skillhub publish ./lei-product-methodology --namespace product-team
```

### 渠道五：通用分发（兼容性最广）

直接使用本仓库根目录的 `.claude/skills/lei-product-methodology/SKILL.md` 文件，按上述任一平台的路径规范放置即可。任何支持 Agent Skills 开放标准的工具均可识别。

---

## 使用方式

### 自动触发
在对话中提到这些关键词时，Agent 会自动加载本 Skill：
- "雷军方法论" / "专注极致口碑快"
- "产品定义" / "砍功能" / "用户体验打磨"
- "定义新产品" / "评估产品方案" / "设计用户反馈闭环"

**示例 prompt**：
> 我要做一个面向大学生的记账 App，但功能列表已经列了 20 个，不知道怎么砍。

### 手动调用
```
/lei-product-methodology
```

---

## 工作流（三阶段）

### 阶段一：产品定义（专注）
1. 列出所有想做的功能
2. 问：哪一个是用户**现在最痛**的刚需？
3. 砍掉其余，只保留这一个
4. **输出**：一句话产品定义 + 一个核心功能

### 阶段二：死磕细节（极致）
1. 找到该功能中最粗糙的环节
2. 问：这个细节的**理论最优解**是什么？
3. 持续改进直到"再努一把也没法更好"
4. **输出**：最粗糙环节 + 改进方案 + 预期效果

### 阶段三：用户参与（口碑与快）
1. 让用户参与开发过程（论坛、反馈群、内测）
2. 建立快速迭代机制（参考周更节奏）
3. 发布时，确保有一个点**明显超出**用户预期
4. **输出**：用户参与方案 + 迭代节奏 + 超出预期的设计点

---

## 目录结构

```
.
├── .claude/
│   └── skills/
│       └── lei-product-methodology/
│           └── SKILL.md              ← Claude Code / GitHub Copilot 兼容
├── .trae/
│   └── skills/
│       └── lei-product-methodology/
│           └── SKILL.md              ← TRAE 原生路径
├── .gitignore
├── README.md                         ← 本文件
└── LICENSE                           ← MIT
```

两份 `SKILL.md` 内容完全一致，仅路径不同以适配不同平台的扫描规范。

---

## 版本

当前版本 `1.0.0`。版本号维护在 `SKILL.md` frontmatter 的 `version` 字段。

变更日志：

| 版本 | 说明 |
|------|------|
| 1.0.0 | 首次发布：核心原则 4 条 + 三阶段工作流 + 边界条件 |

---

## License

MIT License - 详见 [LICENSE](./LICENSE) 文件。可自由复制、修改、分发。

---

## 贡献

欢迎提交 Issue 和 PR 改进工作流、补充案例、优化触发关键词。
