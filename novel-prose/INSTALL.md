# 安装指南（Cherry Studio 手机端）

> 截至 2026-10-24，Cherry Studio 手机端最新版是 **0.4.0**。技能库从 **0.2.1** 开始提供；低于这个版本请先升级。
>
> 手机端界面文案会随版本和语言变化，下面同时写英文/中文标签。找不到时以 **Skills / 技能** 为准。

## 0. 两个前提

1. **标准模式**：技能只在标准模式（Standard）可用；极简模式（Minimal）不使用技能。
2. **模型支持工具调用**：`create_skill`、`install_skill` 都是工具，模型不支持 function calling 时无法安装。

## 1. 装 App（已装可跳过）

### iOS

1. 先装 TestFlight。
2. 打开公测链接：<https://testflight.apple.com/join/2ryzjB66>
3. 接受邀请，安装 “Cherry Studio - 全能 AI 工作站”。

App Store 是否上架以商店页面为准；没有商店版时用 TestFlight。

### Android

任选一种：

- **Google Play**：搜索 `Cherry Studio`，包名 `by.alga.cherrystudio`。
- **GitHub Releases**：打开 <https://github.com/CherryHQ/cherry-studio-app/releases>，下载最新的 `cherry-studio-<版本>-android.apk`（ARM64），在系统里允许“安装未知应用”后安装。

## 2. 装技能：方式 A（推荐，不用 GitHub）

适合只想尽快用起来的人。代价是只安装 `SKILL.md`，`references/` 不会一起装；核心规则都在主文件里，够用。

1. 打开 App，进入侧栏 **Skills（技能）**。
2. 点右上 **More（更多）** → **Create Skill（创建技能）**。
3. 把本包的 `SKILL.md` 发到手机（微信文件传输、AirDrop、网盘都行），在 Cherry 对话里作为**文本附件**发给它；或者打开文件复制正文（第二个 `---` 之后的部分）粘贴到输入框。
4. 补一句：

   > 逐字读取附件里的 SKILL.md 正文，用 create_skill 创建一个名为 `novel-prose` 的技能，description 用文件里的原文，正文不要改写，并绑定到我当前的小说 Agent。

5. 批准 `create_skill` 工具调用。
6. 打开 **Agent 菜单 → 编辑 → 技能**，确认 `novel-prose` 已启用。

安装后从**下一条消息**开始生效。

## 3. 装技能：方式 B（GitHub，完整包，可更新）

适合想要 `references/`、以后能一键更新的人。

1. 新建一个 **public** 仓库。
2. 上传整个 `novel-prose/` 文件夹，保持目录名与 `name` 一致。
3. 复制文件夹链接，例如：

   ```
   https://github.com/<你的用户名>/<仓库名>/tree/main/novel-prose
   ```

4. 回到 App，任选一种：
   - **Skills → Discover（发现）**，在搜索框粘贴链接；
   - 或在对话里说：`安装这个技能：<链接>`，然后批准 `install_skill`。
5. 安装后到 **Agent 菜单 → 编辑 → 技能** 启用它。

以后更新：技能详情页点 **Update skill**，会跟随原链接拉新版。

## 4. 方式 C：不安装，直接当 Agent 指令

把 `SKILL.md` 去掉 frontmatter 的正文，粘贴进 Agent 的“指令 / 提示词”，保存。

- 优点：零门槛，任何版本都能用。
- 缺点：占上下文、不能复用、不能更新，也没有 `references/` 的按需读取。

## 5. 绑定与调用

- **手机端默认没有全局开关**，安装后要按 Agent 单独启用：Agent 菜单 → 编辑 → 技能 → 打开 `novel-prose`。如果你的版本有全局开关，也确认它是开的。
- 对话输入框 **+ → Skills** 可以显式选它；也可以直接说“用 novel-prose 写……”。
- 技能开关随 Agent 配置保存，从下一条消息生效，不会打断正在生成的回复。

## 6. 验证是否装好

发一条：

> 用 novel-prose 写一场深夜便利店的戏，800 字，冷幽默，结尾停在动作上。

如果装好，过程里会出现 **Read Skill（读取技能）** 的提示，正文会按规则来：短句、具体动作、不总结升华。

没生效时按顺序查：

| 现象 | 处理 |
| --- | --- |
| 找不到 Skills / 技能 | 升级到 0.2.1 以上；确认不是极简模式 |
| Agent 不用技能 | Agent 编辑里没启用；或版本有全局开关但关着 |
| 安装报错 | 检查 `SKILL.md` 的 frontmatter、`name` 与文件夹名是否一致 |
| GitHub 安装失败 | 仓库必须是 public；链接指向文件夹或 `SKILL.md` 均可 |
| 更新后没变化 | 点 **Update skill**；或卸载后重装 |

## 7. 来源

- [Cherry Studio 手机端仓库](https://github.com/CherryHQ/cherry-studio-app)
- [手机端技能机制文档](https://github.com/CherryHQ/cherry-studio-app/blob/main/docs/references/agent/agent-skills.md)
- [0.2.1 发布说明（技能库）](https://github.com/CherryHQ/cherry-studio-app/releases/tag/v0.2.1)
- [0.4.0 发布说明（当前版）](https://github.com/CherryHQ/cherry-studio-app/releases/tag/v0.4.0)
- [桌面端技能文档（概念参考）](https://docs.cherryai.com.cn/advanced-basic/extensions/skills)
- [iOS TestFlight 公测](https://testflight.apple.com/join/2ryzjB66)
- [Android APK 下载](https://github.com/CherryHQ/cherry-studio-app/releases)
