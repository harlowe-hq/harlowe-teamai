# Harlowe TeamAI 成员接入说明

这是团队共享 AI 资源仓库，用于分发 Skills、规则和工作文档。

## 接入

先由仓库所有者在 GitHub Settings → Collaborators 中邀请成员。需要贡献资源的成员需有写权限。每位成员使用自己的 GitHub 账号登录，不共享账号或访问令牌。

在 AI 工具中安装 TeamAI Skill 后输入：

```text
/teamai 帮我加入团队 TeamAI，仓库地址是 https://github.com/JasonHarlowe/harlowe-teamai
```

也可以在工作项目目录运行：

```bash
npm install -g teamai-cli@latest
gh auth login
teamai init https://github.com/JasonHarlowe/harlowe-teamai
teamai pull
teamai doctor
```

默认仅配置当前项目。需要整台机器使用团队资源时，自行选择 `--scope user`。初始化后需执行 `teamai pull` 或重新开启支持启动钩子的 AI 会话。

## 更新与贡献

成员执行 `teamai pull` 同步资源；支持启动钩子的工具在新会话开始时也会触发后台同步。

分享资源可向 AI 说明 `/teamai 把这个 Skill 分享给团队`，或执行 `teamai push`。审核 PR 并合并后，团队成员才能同步到正式版本。主分支保护需要仓库所有者在 GitHub 上配置。

## 初始设置

会话自动发布和使用统计上传均已关闭。业务系统权限仍由各系统独立管理。

## 退出

向 AI 说明 `/teamai 卸载 TeamAI`；本机资源和钩子可移除，GitHub 仓库保留。
