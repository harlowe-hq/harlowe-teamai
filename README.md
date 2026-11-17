# Harlowe TeamAI

Harlowe 团队共享的 AI Skills、工作方法与参考资料。适用于销售、市场、电商、内容、设计等同事，无需编程，用自然语言让 AI 按团队方法完成任务。

## 1. 选择使用方式

- **希望自动获得团队更新**：在支持本地 Skills 和命令执行的 AI 工具中接入 TeamAI，例如 Codex、Claude Code、Cursor，按下面的安装步骤操作。
- **只想先使用一个 Skill**：下载本仓库，将 `skills/guide-harlowelife-commercial` 整个文件夹交给支持安装 Skills 的 AI 工具，保留全部参考文件。这种方式更新时需要重新安装。
- **使用普通网页聊天工具**：如无 Skills 安装功能，可将 Skill 中的 Markdown 资料加入该工具的项目或知识库，并在对话中说明要按这些资料工作；这种方式不会通过 TeamAI 自动同步。

## 2. 首次安装：复制给 AI 即可

打开支持本地命令执行的 AI 工具，把下面整段发给它：

```text
我是 Harlowe 团队的非开发同事，请帮我完成以下配置：

1. 安装并加载 TeamAI Skill：
   https://github.com/Tencent/teamai-cli/tree/main/skills/teamai
2. 加入已有团队仓库，不要新建仓库：
   https://github.com/harlowe-hq/harlowe-teamai
3. 先帮我检查 Node.js 20+、Git 和 GitHub CLI，缺少时指导我安装。
4. 默认在当前工作文件夹配置；若需要整台电脑使用，再让我选择。
5. 需要 GitHub 登录时，指导我在浏览器授权。
6. 执行资源同步和诊断，确认 guide-harlowelife-commercial 已安装，
   并告诉我当前 AI 工具是否支持自动同步、是否还需要信任钩子。

请帮我执行配置，需要我操作时清楚说明。
```

同事主要配合安装、登录和授权，无需自行编写代码。首次配置结束后，重新开启 AI 会话，再按下面的例子使用。

### 自己使用终端安装

已安装 Node.js 20+、Git 和 GitHub CLI 的同事，可在日常工作文件夹中执行：

```bash
npm install -g teamai-cli@latest
gh auth login --web --git-protocol https
teamai init https://github.com/harlowe-hq/harlowe-teamai
teamai pull
teamai list skills
teamai doctor
```

已经登录 GitHub 的，可跳过登录命令。默认配置当前工作文件夹；希望用户范围使用时，将初始化命令改为：

```bash
teamai init https://github.com/harlowe-hq/harlowe-teamai --scope user
```

初始化时选择自己使用的 AI 工具。成功标准是同步列表出现 `guide-harlowelife-commercial`，且诊断没有阻止该工具工作的错误。初始化本身不复制团队资源，需要运行 `teamai pull` 或在支持启动钩子的工具中开启新会话。

如果出现成员登记写入失败，但提示本机已配置，先执行 `teamai pull` 检查是否能同步资源；需要向公司仓库提交修改时，再联系维护人开通写权限。

## 3. 日常怎么用

目前提供的 Skill 是 [Harlowelife 品牌与商业共识](skills/guide-harlowelife-commercial/SKILL.md)，名称为 `guide-harlowelife-commercial`。包含品牌定位、用户、产品、销售、内容审美、数据证据和路线参考。

同步并重新开启会话后，直接向 AI 提任务，不需要每次使用 `/teamai`：

**新人培训**

```text
使用 guide-harlowelife-commercial，为新销售准备一份 10 分钟的品牌与产品培训，包含常见客户问题和回答。
```

**电商详情页**

```text
使用 guide-harlowelife-commercial，为 SOLA Desk 写中文产品详情页。先说明使用场景与购买理由，再介绍产品，标出需要核实的内容。
```

**市场与渠道**

```text
使用 guide-harlowelife-commercial，为欧洲分销商准备一页产品介绍，区分已确认事实和试销建议。
```

**文案审核**

```text
使用 guide-harlowelife-commercial，检查下面这段宣传文案的品牌语气、产品事实和健康主张，并给出可使用的修改稿：
[粘贴文案]
```

AI 会按任务读取相关参考文件，同事无需读完所有资料。当前资料基线为 **2026-11-11，版本 1.0**；报价、上市状态和技术主张需结合最新依据核实。需要分析实际业务数据时，另行提供资料或授权相应业务工具。

## 4. 团队资源更新后怎么同步

支持并已启用 TeamAI 启动钩子的 AI 工具，会在新会话开始时触发后台同步。需要立即更新，或工具没有启动钩子时，向 AI 发送：

```text
/teamai 帮我同步最新团队资源，并确认 guide-harlowelife-commercial 可用。
```

也可以在接入过的工作文件夹执行：

```bash
teamai pull
```

同步后重新开启会话，让 AI 发现新安装或更新的 Skill。手动安装 Skill、网页项目或知识库中的资料，需要自行替换为新版。

## 5. 常见问题

**AI 说找不到 Skill？**

确认当前工作文件夹已接入正确团队；执行 `teamai pull`、`teamai list skills`，然后重新开启会话。仍有问题时，让 AI 执行 `teamai doctor` 检查。也可以把本仓库的 Skill 链接交给 AI，请它检查是否安装完整。

**已经安装了 TeamAI，为什么没有自动更新？**

安装 CLI 不等于完成团队接入。还需初始化当前工作文件夹，并确保所用工具支持启动钩子且已启用、获得信任。暂时可以手动运行 `teamai pull`。

**想把自己的方法分享给团队？**

向 AI 发送 `/teamai 把这个 Skill 分享给团队`。有写权限的成员可通过 `teamai push` 提交修改，审核合并后由其他成员同步；没有写权限的同事可先把文件交给维护人。

**以后不想使用？**

向 AI 发送 `/teamai 卸载 TeamAI`，请它移除本机的相关配置。

## 仓库目录

- `skills/`：团队 Skills，包含入口 `SKILL.md` 和参考资料。
- `docs/`：共享工作文档；[成员接入与更新说明](docs/team-onboarding.md)。
- `teamai.yaml`：团队资源分发配置。
