# Harlowe TeamAI

Harlowe 团队共享的 AI Skills、工作方法与参考资料。适用于销售、市场、电商、内容、设计等同事，无需编程，用自然语言让 AI 按团队方法完成任务。

## 1. 普通同事：下载 Skill 后导入（推荐）

适合销售、市场、电商、内容、设计等同事。**无需安装 Node.js、Git、GitHub CLI 或 TeamAI，也无需仓库邀请。** 使用的 AI 工具需要支持安装本地 Skills。

1. 点击 [下载 Harlowelife Skill 安装包](https://github.com/harlowe-hq/harlowe-teamai/raw/refs/heads/main/downloads/guide-harlowelife-commercial.zip)。
2. 在 AI 工具的 Skills / 技能管理页面，使用“安装”或“导入”入口选择这个 ZIP。不同工具入口不同；支持 ZIP 导入的工具可直接导入，要求文件夹的工具先解压，再选择完整的 `guide-harlowelife-commercial` 文件夹。
3. 安装后按工具提示重新开启会话，发送下面这句话验证：

```text
请使用 guide-harlowelife-commercial，介绍这套 Skill 能帮我完成哪些工作，并为新销售列一个品牌培训提纲。
```

如果使用的 AI 助手支持执行本机安装，也可以把安装包交给它，并说明：

```text
请把附件中的 guide-harlowelife-commercial 安装为当前 AI 工具可用的 Skill，保留全部参考文件，并检查是否能读取。只安装这个业务 Skill，不配置 TeamAI 自动同步。
```

**更新方式：**团队发布新版后，重新下载并替换旧 Skill；手动导入不会自动更新。

### 如果 AI 工具没有 Skills 导入功能

解压安装包，将 `SKILL.md` 和 `references/` 中的 Markdown 文件加入该工具的项目或知识库，然后告诉 AI：

```text
请先读取 SKILL.md，按其中的工作方法处理任务，并根据需要查阅我上传的参考资料。
```

这种方式是使用参考资料，不等同于安装原生 Skill；可用文件数量和读取方式取决于所用工具，更新时也需手动替换文件。

## 2. 需要自动同步的同事：接入 TeamAI

只在希望团队资源更新后自动同步时使用此方式。需要支持本地 Skills 和命令执行的 AI 工具，例如 Codex、Claude Code、Cursor。

| 环境 | 是否需要 |
|---|---|
| Node.js 20+（含 npm） | 需要，用于运行 TeamAI CLI |
| Git | 需要，用于同步资源仓库 |
| GitHub CLI（`gh`） | 下面的标准 GitHub 登录流程使用；采用其他 Git 接入方式时可不使用 |

### 让 AI 帮忙安装和配置

把下面整段发给支持本地命令执行的 AI 工具：

```text
请帮我配置 Harlowe 团队资源的自动同步：

1. 安装并加载 TeamAI Skill：
   https://github.com/Tencent/teamai-cli/tree/main/skills/teamai
2. 加入已有团队仓库，不要新建仓库：
   https://github.com/harlowe-hq/harlowe-teamai
3. 检查 Node.js 20+、Git，以及标准 GitHub 接入流程使用的 GitHub CLI。
   缺少时指导我安装；需要登录时指导我在浏览器授权。
4. 默认在当前工作文件夹配置；若需要整台电脑使用，再让我选择。
5. 执行 teamai pull、teamai list skills 和 teamai doctor，
   确认 guide-harlowelife-commercial 已安装。
6. 检查当前工具的启动钩子，告诉我是否能自动同步、是否还需信任或启用。

请帮我执行配置，需要我操作时清楚说明。
```

### 自己使用终端配置

已安装上表环境的同事，可在日常工作文件夹中执行：

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

初始化时选择自己使用的 AI 工具。同步列表应出现 `guide-harlowelife-commercial`，且诊断没有阻止该工具工作的错误。初始化本身不复制资源，需要执行 `teamai pull` 或在支持启动钩子的工具中开启新会话。

如果出现成员登记写入失败，但提示本机已配置，先执行 `teamai pull` 检查资源同步；直接向公司仓库提交修改时，再联系维护人开通写权限。

## 3. 日常怎么用

目前提供的 Skill 是 [Harlowelife 品牌与商业共识](skills/guide-harlowelife-commercial/SKILL.md)，名称为 `guide-harlowelife-commercial`。包含品牌定位、用户、产品、销售、内容审美、数据证据和路线参考。

导入 Skill 或完成 TeamAI 同步后，按工具提示重新开启会话。日常直接向 AI 提任务，不需要每次使用 `/teamai`：

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

**手动导入的同事：**重新下载上面的 ZIP，替换旧 Skill。网页项目或知识库中的资料同样需要手动替换。

**已接入 TeamAI 的同事：**按下面的方式自动或手动同步。

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

手动导入的同事：确认工具支持 Skills、安装已启用，且完整保留 `SKILL.md` 和 `references/`，再重新开启会话。网页知识库方式则请 AI 先读取上传的 `SKILL.md`。

TeamAI 用户：确认当前工作文件夹已接入正确团队，执行 `teamai pull`、`teamai list skills` 后重新开启会话；仍有问题时执行 `teamai doctor`。

**已经安装了 TeamAI，为什么没有自动更新？**

安装 CLI 不等于完成团队接入。还需初始化当前工作文件夹，并确保所用工具支持启动钩子且已启用、获得信任。暂时可以手动运行 `teamai pull`。

**想把自己的方法分享给团队？**

普通同事将修改后的文件交给维护人即可。已接入 TeamAI 且有写权限的成员，可向 AI 发送 `/teamai 把这个 Skill 分享给团队`，通过 `teamai push` 提交修改，审核合并后由其他成员同步。

**以后不想使用？**

手动安装的 Skill 在 AI 工具的技能管理页面移除，上传到知识库的资料在对应项目中移除。TeamAI 用户可向 AI 发送 `/teamai 卸载 TeamAI`，请它移除本机的相关配置。

## 仓库目录

- `skills/`：团队 Skills，包含入口 `SKILL.md` 和参考资料。
- `downloads/`：供同事手动导入的 ZIP 安装包；维护人更新 Skill 时需同步重新打包。
- `docs/`：共享工作文档；[成员接入与更新说明](docs/team-onboarding.md)。
- `teamai.yaml`：团队资源分发配置。
