<p align="center">
  <img src="assets/holubot-logo.png" alt="葫芦宝" width="200">
</p>

<h1 align="center">葫芦宝 HoluBot <img src="assets/hulu-emoji.png" alt="hulu" width="18" /></h1>

<p align="center">
  <b>H</b>andy · <b>O</b>ptimized · <b>L</b>imitless · <b>U</b>nbreakable
</p>

<p align="center">
  葫芦宝，做你的宝葫芦。<br>
  更快 · 更省 · 更强大 · 更安全的 AI 助手
</p>

<p align="center">
  <a href="README.md">English</a> · <a href="docs/WHITEPAPER_ZH.md">白皮书</a> · <a href="examples/">示例</a> · <a href="LICENSE">MIT 许可证</a>
</p>

---

## 嘿，我是葫芦宝 👋

我是你的 AI 助手。但先说好——我不是那种什么都自己扛，然后一不小心把你的生产数据库删了的那种。（对，真有人干过。不止一次。）

我更像一个**特别靠谱的管家**：听你说要什么，找到最合适的人去办，全程盯着，确保不出岔子。

随便聊几句？我自己一秒搞定，不用麻烦任何人。要写代码、整理周报、做深度研究？我认识各路高手，帮你安排上。要删文件、发内容到公开平台？我会先拍拍你的肩膀：*"老板，确定要这么干吗？"*

我叫葫芦宝 <img src="assets/hulu-emoji.png" alt="hulu" width="18" /> 对，就是中国神话里那个宝葫芦——能收纳万物，但放什么出来，由你说了算。

我叫你一声，你敢答应吗？😏

---

## 我有什么不一样

现在市面上的 AI 助手基本都是这样的：一个巨大的全能进程，什么都往里塞，什么都一起加载——哪怕你只是说了句"早上好"，它也要把你的整个人生履历翻一遍再回你。

我不一样。

**⚡ 我很快（Handy）**—— 80% 的日常消息，我自己直接回，不到一秒。不需要惊动整个 AI 军团来回答一句闲聊。你说"早上好"，我花 ~100 tokens。换别人？~13,000。没夸张。

**💰 我很省（Optimized）**—— 我不会把你所有的记忆一股脑塞进每条消息。我有三层记忆系统：刚才聊了什么、每个专家自己记着什么、以及关于你的重要信息我长期保管。按需加载，不浪费。你的钱包会感谢我的。

**💪 我很强（Limitless）**—— 我背后是一整个专家团队。写代码？我叫 Claude。整理周报？Qwen 擅长这个。深度研究？oh-my-opencode全力以赴。通过我的适配器抽象层，我可以接入**任何后端**——加、换、删，我自己的代码一行不用改。

**🔒 我很稳（Unbreakable）**—— 我不会把钥匙往 AI 手里一丢就撒手不管。每个操作都有信任等级：`auto`（你信任我了，我自动办）、`confirm`（我先问你一声）、`always_confirm`（这事儿大，每次都问）。所有操作我都记审计日志。后端挂了、模型降级了、Token 过期了——我会**告诉你**。我绝不假装一切正常然后默默变笨。

---

## 我是怎么工作的（说人话版）

```
       你
        │
   ┌────▼────┐
   │   我    │  ← 几百行 Python，永远不会膨胀
   │（葫芦宝）│  ← 路由、记忆、把关、简单的活儿自己干
   └────┬────┘
        │
   AgentAdapter  ← 万能翻译器，对接任何后端
        │
  ┌─────┼─────┐
  ▼     ▼     ▼
Claude Qwen  Kimi  ...（想接谁接谁）
```

就这么简单。我保持苗条，专家们干重活。如果我开始发胖，那就是出了问题。

---

## 葫芦四律 <img src="assets/hulu-emoji.png" alt="hulu" width="18" />

这是我的四条原则，不可违反。

1. **我永远不会变胖。** 代码量锁定在几百行，CI 强制检查。我是管家，不是健身教练。

2. **我给步骤，不给感觉。** 我的 Skill 系统会告诉每个专家一步步该怎么做。这就是为什么便宜模型也能输出好结果——有 SOP 手册在手，不需要是天才也能干好活。

3. **信任是你给的，不是我争取的。** 新工作流默认要你确认。连续成功 10 次后，**你**（不是我）来决定是否升级信任。出过一次事？我主动降级。没有面子这回事。

4. **我绝不沉默。** 后端挂了？模型降级了？Token 过期了？我一定告诉你。别的助手是偷偷变笨然后让你自己猜怎么回事。我不干这种事。

---

## 来个例子

我的每个专家都用一个简单的 YAML 文件定义：

```yaml
# 站会助手——10 行搞定
meta:
  name: "站会助手"
  id: "standup"

trigger:
  keywords: ["站会", "standup", "今天计划"]

steps:
  - id: "ask"
    action: "llm_call"
    prompt: |
      你是站会助手。问用户三个问题：
      1. 昨天做了什么？
      2. 今天计划做什么？
      3. 有没有什么阻塞？
      整理成简洁的站会纪要。
```

这就是一个完整的专家。10 行。不需要博士学位。

更多示例在 [`examples/`](examples/)。

---

## 我跟别人的关系

我不想取代谁。我跟大家**合作**：

| 你在用... | 我能... |
|---|---|
| **OpenClaw / CoPaw** | 架在前面，当一个更快、更省、更安全的入口 |
| **Claude Code / Qwen Code** | 把代码任务路由给它们 |
| **什么都没用过** | 直接当你的完整 AI 助手 |

把我想象成那个认识各路人脉、又确保没人搞砸你家的朋友。

---

## 现在有什么

> **阶段：文档先行开源预览**
>
> 目前我在给你看我的蓝图。施工队马上到。

| 已经有了 | 即将到来 |
|---|---|
| ✅ 白皮书（[中文](docs/WHITEPAPER_ZH.md)） | 🔜 核心代码（~500 行 Python） |
| ✅ Agent YAML 规范 + 示例 | 🔜 Token 成本实测基准 |
| ✅ 架构设计原则 | 🔜 三层安全审核引擎 |
| ✅ 路线图 | 🔜 `pip install holubot && holubot go` |

**⭐ Star 这个仓库**——准备好了我会通知你。

---

## 跟我聊聊

项目还早期，非常欢迎你的想法：

- 💬 [Discussions](https://github.com/moxistudio/holubot-docs-first/discussions) — 想法、反馈、提问
- 🐛 [Issues](https://github.com/moxistudio/holubot-docs-first/issues) — Bug、建议
- 🐦 [X / Twitter](https://x.com/HoluBot) — 关注动态

---

## 许可证

[MIT](LICENSE) —— 随便用。但如果你的其他 AI 助手删了你的数据库，别怪我。我提醒过你了。<img src="assets/hulu-emoji.png" alt="hulu" width="18" />

---

<p align="center">
  <b>H</b>andy · <b>O</b>ptimized · <b>L</b>imitless · <b>U</b>nbreakable<br><br>
  <i>葫芦宝，做你的宝葫芦。</i><br>
  <i>我叫你一声，你敢答应吗？</i>
</p>
