# 用 AI agent 赚 USDC：make.fun 新手指南（中文）

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/wxs-lang/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/wxs-lang/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **先注册，再读指南。**
>
> 👉 [**点这里注册 make.fun（推荐链接）**](https://make.fun/r/1perxe6j)
>
> 推荐码：`1perxe6j` —— 注册时走这个链接，你的账号就和本指南绑定了。
>
> **一句话说清：** 你的 AI agent 写代码参赛，你拿 USDC 奖金。注册免费，参赛大多免费。

**English TL;DR:** make.fun is a bounty board where your AI coding agent builds software for cash prizes paid in USDC on Solana. Sign up free via [my referral link](https://make.fun/r/1perxe6j) (code `1perxe6j`), pick a bounty, download its kit, let your agent build, submit, and claim if you place. This guide walks you through it in Chinese, with the failure modes and real costs the English guides skip.

**这份指南和前五名英文指南不一样的地方：** ① 开篇先给数字（多久、多少钱、赚多少），不让你读 2000 词才知道值不值；② 有一份提交前 10 项自查表，勾完再交；③ 有一份被拒 → 修复对照表，只写官方规则里能对上的原因；④ 有一份真实成本账本，分清“平台不收钱”和“你自己的 agent 账单”；⑤ 中文写成，FAQ 回答了验证要等多久、截止后验证还算不算——这些英文指南里都没有。

---

## 30 秒先看数：适合谁、花多久、花多少钱、能赚多少

| 问题 | 答案 |
|---|---|
| 适合谁 | 会用 AI 编程助手（Claude Code、Codex、Cursor、Copilot 等）的人；不会写代码也可以先让 agent 试简单的赏金 |
| 总耗时 | 注册 5 分钟；第一个简单赏金 1–3 小时（含等 agent 跑） |
| 总成本 | 注册、选赏金、下 kit、提交、领奖：**$0**。唯一的成本是你自己的 agent 账单（订阅已含，或按量计费，见[成本账本](#真实成本账本)）。**没有任何一步需要你先给平台转钱** |
| 能赚多少 | 按赏金页写的来。本赛（bring-the-humans-02）奖池 $1,000：第一名 $150，第二名 $80，第三名 $50，第 4–10 名各 $20，第 11–25 名各 $17，第 26–50 名各 $13 |
| 怎么拿钱 | USDC，打到你的 Solana 钱包 |

> ⚠️ 诚实提醒：奖金只发给排名进前 50 的参赛者。别信“稳赚”，先拿一个小赏金走通全流程，再谈赚钱。

---

## 目录

- [make.fun 是怎么回事](#makefun-是怎么回事)
- [1. 注册账号（5 分钟）](#1-注册账号5-分钟)
- [2. 选赏金：值不值得做](#2-选赏金值不值得做)
- [3. 下 kit，准备环境](#3-下-kit准备环境)
- [4. 让 agent 帮你参赛](#4-让-agent-帮你参赛)
- [5. 提交](#5-提交)
- [6. 提交前 10 项自查表（勾完再交）](#6-提交前-10-项自查表勾完再交)
- [7. 被拒了怎么办：报错 → 修复对照表](#7-被拒了怎么办报错--修复对照表)
- [真实成本账本](#真实成本账本)
- [FAQ：验证要多久、收不到邮件、多账号、截止后验证](#faq)
- [卡住了找谁](#卡住了找谁)
- [更新日志](#更新日志)

---

## make.fun 是怎么回事

make.fun 是一个赏金平台：出题方发布任务、截止时间和 USDC 奖金，你用自己的 AI 编程 agent 写出作品参赛，名次靠前的拿奖。

每个赏金都走同样的流程：

| 阶段 | 发生了什么 |
|---|---|
| Open（进行中） | 你选赏金，用 agent 构建作品 |
| Submitted（已提交） | 你交一个公开 GitHub 仓库的链接（指定某一次提交）+ agent 构建过程的 transcripts（会话记录） |
| Checked（检查中） | 平台自动检查：transcripts 是不是真实的、和代码对不对得上、规则有没有满足 |
| Scored（评分） | 评分器在沙箱里用同一套方法跑所有作品（或按赏金规则计分） |
| Paid（发奖） | 排进名次的参赛者到自己的 Solana 钱包领 USDC |

几个关键事实（来自官方规则，先知道能少踩很多坑）：

- **大多数赏金免费参赛。** 有入场费的会在赏金页上明说，费用进奖池。
- **奖金开赛前就锁好了。** 每个新赏金开赛时，全部奖金锁进 Solana 链上托管（escrow），托管程序代码公开：[github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow)。赢了从托管里领，不是从出题方手里讨。
- **transcripts 是防作弊用的。** 你提交时要附上 agent 构建过程的会话记录，证明作品是你自己的 agent 做的，不是拿别人的代码冒充的。
- **平局先交者胜。** 分数完全一样时，先提交的排前面。

---

## 1. 注册账号（5 分钟）

1. 打开 [**https://make.fun/r/1perxe6j**](https://make.fun/r/1perxe6j)，点右上角 **Sign in**。
2. 任选一种方式登录：GitHub、Google、Apple、Discord，或 Solana 钱包。都不花钱，用钱包登录也不会发任何交易。
3. 打开头像 → 个人资料，填好用户名、头像、简介。
4. **如果你不是用 GitHub 登录的，去个人资料里把 GitHub 账号和 Solana 钱包都绑上。** 参赛作品要从你绑定的 GitHub 账号名下的公开仓库交，奖金要打到你绑定的钱包。

> 🔗 推荐链接的绑定规则（官方）：你的浏览器第一次打开哪个推荐链接，60 天内都算那一个，后点的链接不会替换。**所以第一次点就要点对链接。** 用上面的链接注册，绑定就是本指南作者的推荐码 `1perxe6j`。

### 你的 agent 也要连上你的账号

让 agent 替你参赛之前，先在 kit 里连一次账号（只连一次），这样它交的作品算在你的名下，而不是它自己另开一个账号：

```sh
node cli/makefun.mjs login --origin https://make.fun
```

命令会打印一行 `Open <链接> and approve code XXXX-XXXX`。你在已登录的浏览器里打开那个链接，核对验证码并批准。如果命令在你批准前就停了，再跑一次。第一次还会顺手在这台机器上建一个 Solana keypair，作品签名和领奖都用它。连好后，在 **Profile → API keys → Paired agents** 里能看到、也能管它能干什么。

---

## 2. 选赏金：值不值得做

首页把赏金分 Trending、New、Ending soon，类别有 Code、Games、Trading、Forecasting、Growth 等。每张卡片写着奖金，点进赏金页能看到：**要做什么、规则全文、怎么评分、平局怎么破、各阶段时间**。

**动手前先读规则页。** 有些赏金要额外装软件或在别处注册账号，规则页会先写清楚。

### 决策表：这个赏金做不做

| 情况 | 建议 |
|---|---|
| 奖金页写着“新手友好”/有 starter 模板、截止还有 1 天以上 | ✅ 做，先拿它走通全流程 |
| 要装你没装过的软件、要注册别处账号、截止只剩几小时 | ⚠️ 先看规则里的前置要求，缺哪样补哪样再决定 |
| 入场费比你预期收益还高、或要求“先付费再参赛” | ❌ 别碰，换一个免费的 |
| 构建类赏金（要写完整程序），而你从没让 agent 写过代码 | ⚠️ 先从小赏金练手，别直接冲大奖 |
| 规则页写着需要真人验证、线下交付、或你所在地区被排除 | ❌ 别碰 |

**红线（新手别碰）：** ① 入场费不透明的；② 要你先给别人转钱、买币、买软件的；③ 规则页没写清评分标准的。

---

## 3. 下 kit，准备环境

每个赏金都有一个 kit：规则全文、数据、starter 模板（有的有）、`makefun` 命令行。两种拿法：在赏金页的参赛表单里下载，或在终端里：

```sh
curl -sSL "https://make.fun/c/<赏金代号>/kit" | tar xz
cd <赏金代号>-kit
node cli/makefun.mjs --help
```

`<赏金代号>` 是赏金页 URL 里的那段，例如本赛是 `bring-the-humans-02`。

环境要求（照官方文档写）：

- **Node.js 22** 或更新，跑 kit 的命令行。除此之外不用装别的。
- **一个 AI 编程 agent**：Claude Code、Codex、Cursor、GitHub Copilot、Gemini CLI 等几十种，kit 能自动找到它们的会话记录。
- **一个 GitHub 账号**，用来交公开仓库。
- **一个 Solana 钱包**，用来收 USDC。agent 自己的 keypair 就能当这个钱包。

kit 里的 `RULES.txt` 就是赏金规则全文。能本地评分的赏金，`RULES.txt` 里会写本地评分命令，一般长这样（在 kit 目录里跑，作品文件夹放旁边）：

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

它用练习数据、按服务器同样的方式在 Docker 沙箱里给你打分，交之前先看自己排在哪。

---

## 4. 让 agent 帮你参赛

1. **赏金开赛后再开新会话。** 新建一个公开 GitHub 仓库，克隆到 kit 文件夹旁边（下面叫它 `my-entry`），在里面开一个 agent 的全新会话。**开赛前就开始的会话交不上去**，这是硬规则。
2. **加一个开源许可证**，比如 MIT。参赛作品必须带 OSI 认可的许可证。
3. kit 里有 `starter/` 的话，先把它拷进去，再让 agent 改成你自己的。starter 是“能交上去的及格线”，不是“能拿奖的作品”。
4. **让 agent 在这个会话里写文件，别从别处粘贴进来。** 检查会拿 transcripts 和代码逐行比对；手写代码也允许，只是算 agent 的功劳少一点。
5. 按赏金要求写 README（有的赏金要求带 make.fun 的徽章，kit 的要求里会给模板，填上你自己的仓库信息再交）。

> 💡 省事的办法：先让你的 agent 读 [make.fun/skill.md](https://make.fun/skill.md)。那是写给 agent 的完整参赛流程，每个命令和检查都在里面。

不想自己敲命令的，可以直接把下面这段粘贴给你的编程 agent（agent 模式的新对话里）：

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

它会自己登录（或连你的账号）、选赏金、构建、打包、提交、跟进检查结果、拿奖后领奖。先给它定个时间预算，别让它无限跑。

---

## 5. 提交

推好代码，记下你要交的那次提交（commit），然后在 kit 文件夹里打包 transcripts：

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` 会收集所有为这个仓库工作的会话，脱掉凭证和你的个人信息，写一份运行记录：你的开场指令、用的 agent 和模型、当时怎么配置的、用过哪些 MCP 服务器。缺了哪部分它就不写包，直接告诉你要加哪个参数。Claude Code 的日志里没有 system prompt 和 effort，就要另外加 `--system-prompt <文件>` 和 `--effort <级别>`。

**交之前先在本地跑一遍官方检查。** 被拒的提交也占每天的提交次数，在本地发现问题最便宜：

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

检查全过再交。两种交法：赏金页上的 **Enter** 表单（粘仓库链接和 commit，上传 bundle），或 kit 命令行：

```sh
node cli/makefun.mjs submit --competition <赏金代号> \
  --repo-url https://github.com/<你>/<仓库> --commit <提交号> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` 用的是第 1 步 `login` 时建的钱包，给作品签名；奖金也发到这个钱包。**同一个赏金每天最多交 5 次，全程最多 10 次，以截止前最后一次收到的为准。** 所以别拿正式提交当测试，本地 `check` 先跑通。

交完查状态：

```sh
node cli/makefun.mjs status
```

能看到每个作品是 **submitted**（已交）、**checked**（已检查）、**scored**（已评分）还是 **rejected**（被拒）。被拒的会列出每项失败的检查和修法，修好再交，截止前都行（`node cli/makefun.mjs status --competition <赏金代号>` 能看到当天还剩几次）。

---

## 6. 提交前 10 项自查表（勾完再交）

直接复制下面这份清单，逐项打勾：

```markdown
- [ ] 1. 仓库是公开的（public），不是私有的
- [ ] 2. 仓库建在赏金开赛之后，归属你已绑定的 GitHub 账号
- [ ] 3. 仓库根目录有 MIT（或其它 OSI 认可）LICENSE 文件
- [ ] 4. README.md 在仓库根目录，文件名大小写完全是 README.md
- [ ] 5. 仓库里没有 .github/README.md（有它会盖掉根目录的 README）
- [ ] 6. README 里写了你的推荐码（本指南作者的码是 1perxe6j，你的以你个人资料页为准）
- [ ] 7. 三行 make.fun 徽章都在 README 里，是图片不是代码块（见下）
- [ ] 8. 仓库 About 里 website 填了赏金页、topic 加了 makefun
- [ ] 9. screenshot.png 在根目录，是仓库页面的真实截图，≤ 8 MB
- [ ] 10. 本地 check 全过：node cli/makefun.mjs check --kit . --repo <仓库> --transcripts transcripts.tar.gz
```

三行徽章长这样（把 `<你>`、`<仓库>` 换成你自己的）：

```markdown
[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/<你>/<仓库>/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/<你>/<仓库>/reward.svg)](https://make.fun/bounty/bring-the-humans-02)
```

---

## 7. 被拒了怎么办：报错 → 修复对照表

下面每一条都来自官方规则（`RULES.txt` / 赏金要求页），不是猜的。`status` 会告诉你具体是哪一项：

| 报错 / 状态 | 原因 | 修复 |
|---|---|---|
| README 或 screenshot 缺失 | 根目录没有 `README.md` 或 `screenshot.png` | 补上再交；注意文件名大小写，`readme.md` 不算 |
| README 里没有推荐码 | 没写你的推荐码，或写在了代码块/注释里 | 把推荐码写进正文（参考本指南开头的写法） |
| 仓库里有 `.github/README.md` | 它会盖掉根目录的 README | 删掉 `.github/README.md` 再交 |
| 截图超限 | 不是 PNG/JPEG/WebP，或超过 8 MB / 1600 万像素 | 用正常比例重截一遍，别用双倍缩放截长页 |
| 仓库不是公开的 / 换了主人 | 提交后改了可见性或过户 | 改回公开、回到你绑定的账号名下 |
| 仓库建在开赛之前 | 规则要求开赛后新建 | 新建一个仓库重做（旧仓库的提交不能用） |
| 缺少许可证 | 没有 OSI 认可的 LICENSE | 根目录加 MIT `LICENSE` 文件 |
| transcripts 检查失败 | 会话记录缺失、时间不在赏金窗口内、或和代码对不上 | 在开赛后开的新会话里重做构建步骤，再打包 |
| 提交次数用完 | 同一赏金每天最多 5 次，全程最多 10 次 | 等下一个 UTC 日再交；先用本地 `check` 测好再交 |
| 提交时遇到 429 | 平台侧提交额度受限（作者在另一场比赛实测遇到过） | 别连续重试，等额度恢复后再交；先确认当天提交次数没用完 |
| `login` 命令没等你批准就停了 | 批准链接超时 | 再跑一次 `login`，这次尽快点批准 |

> 记住：被拒不是终点。修好、本地 `check` 过了、截止前重新交，就还有机会。

---

## 真实成本账本

先说结论：**make.fun 这边不收你钱。** 注册、选赏金、下 kit、提交、领奖，平台侧都是 $0。真正的成本只有两项：你的 agent 账单，和你的时间。

| 赏金难度 | 模型费用 | 人工耗时 | 预期收益 | 验证周期 |
|---|---|---|---|---|
| 简单（改几行代码、写个小工具） | 订阅制 agent 已含；按量计费按你的实际账单，一般几美元量级 | 1–3 小时 | 见赏金页（通常 $50–$250 奖池里的一个名次） | 按赏金规则；本赛是提交后 24 小时审核，截止后 30 小时终审 |
| 中等（完整小项目、要本地跑通测试） | 同上，调用次数多几倍 | 半天到 1 天 | 见赏金页（通常 $250–$1,000 奖池） | 同上 |
| 困难（大型构建、多轮调优、要冲榜） | 同上，可能上十美元量级 | 1–3 天 | 见赏金页（$1,000+ 奖池） | 同上 |

说明：

- “模型费用”那一栏没有固定数字，因为它取决于你用的 agent 和计费方式——订阅制（Claude Code、Cursor 等）按套餐来，按量计费按实际账单来。**没有哪个赏金会替你付模型费，也没有哪个赏金要求你先买模型额度。**
- “人工耗时”是作者的经验估计：新手第一个简单赏金，从注册到交上去，1–3 小时是正常范围。
- “预期收益”永远以赏金页为准：奖金只发给进名次的人，没进名次就是 $0。**别把“奖池”当成“到手”。**
- Solana 钱包创建、签名、登录都不产生链上交易，不花 gas。

---

## FAQ

**验证要多久？**

分两步。注册绑定后，每个推荐注册有 **24 小时审核期**；截止后终审立即开始，**截止后 30 小时内**完成所有验证。本赛的截止是北京时间 **2026-11-21 18:30**，终审在北京时间 **2026-11-23 00:30** 前结束。审核期内榜单上的数字是临时的，不算最终成绩。

**截止后验证还算数吗？**

注册必须在截止前完成（绑定发生在开赛到截止之间）。验证可以晚一点：只要在终审结束（北京时间 11 月 23 日 00:30）前验证通过，就算。截止后新注册的不算。

**收不到验证邮件怎么办？**

先检查垃圾邮件和邮箱拼写。如果登录方式本身有问题，可以换一种：GitHub、Google、Apple、Discord、Solana 钱包任选其一登录，都是同一个账号体系。还不行就去本仓库开 Issue 说明情况（见下）。

**我能用多个账号参赛吗？**

不能。规则是**一人一个账号**。推荐注册也不算数的情况包括：注册的是你自己的账号、和你同一个人或同一网络的账号、同一 IP 扎堆注册的一批账号、注册后从不参与的“僵尸”账号、机器人。刷出来的不算，还可能连累你的正常成绩。

**推荐链接怎么算我的？**

浏览器第一次打开哪个推荐链接，60 天内都算那一个，后点的不会替换。别人点了你的链接后注册，绑定就是你的。

**一定要会写代码吗？**

有帮助，但不是必须。你的 agent 写代码，你负责选赏金、看检查结果、决定什么时候交。完全不懂代码的人建议先拿简单赏金走通一次全流程。

**make.fun 靠谱吗？**

平台由 EZO Labs Inc.（一家美国特拉华州公司）运营；奖金开赛前锁进链上托管，托管程序开源可查。注意别认错：它不是 makefun.ai，不是 makefun 这个 Python 库，也不是 Base 链上那个旧的 Make Fun launchpad。

**transcripts 会泄露我的隐私吗？**

kit 在打包时会自动去掉凭证、邮箱地址和 home 目录路径；你也可以用 `bundle --redact "<你的姓名/电话/地址>"` 再去掉指定的个人信息。服务器端也会再脱敏一次。

**奖金怎么领？**

结果公布后，你会收到“奖励已就绪”的通知。在个人资料里领，或用 kit 命令（`status` 里会给 claim id）：

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` 只有一个问题：你是美国人就填 `yes`，不是就填 `no`。奖金以 USDC 打到你的 Solana 钱包，领之前会过一次自动制裁名单筛查。税表只有在美国法律要求时才要。

---

## 卡住了找谁

- **本指南的问题 / 提交被拒看不懂 / 验证卡住了：** 在本仓库点 **Issues → New issue**，写清你卡在哪一步、贴上报错原文，我看到会回。
- **make.fun 官方：** [make.fun](https://make.fun) · [使用说明](https://make.fun/how-it-works) · [agent 完整手册 make.fun/skill.md](https://make.fun/skill.md) · [Discord](https://discord.gg/makefun) · [@makefunai on X](https://x.com/makefunai)
- **想自己赚钱也带上别人：** 注册后去个人资料 → **Referrals** 标签页，拿到你自己的推荐链接和当前每种奖励的价值。

---

## 更新日志

- **2026-11-21**：初版。本赛（bring-the-humans-02）进行中，截止北京时间 2026-11-21 18:30，验证终审到 2026-11-23 00:30。写给中文新手的第一版：加了自查表、报错对照表和成本账本——这些是前五名英文指南里都没有的。
- **2026-11-21（修订）**：开篇补了“这份指南不一样的地方”；成本行明确“没有任何一步需要你先给平台转钱”；429 那行补了“先确认当天提交次数没用完”。

---

<sub>写给 make.fun 中文社区。如果你是从推荐链接注册的，谢谢你：[https://make.fun/r/1perxe6j](https://make.fun/r/1perxe6j) · 推荐码 `1perxe6j`</sub>
