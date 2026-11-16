# Harlowe TeamAI

Harlowe 团队共享 AI Skills、规则和工作文档。

[成员接入与更新说明](docs/team-onboarding.md)

- `teamai.yaml`：团队配置。
- `docs/`：共享工作文档。
- `skills/`：可同步到 AI 工具的团队 Skills。

## Harlowelife 品牌与商业 Skill

[guide-harlowelife-commercial](skills/guide-harlowelife-commercial/SKILL.md) 包含品牌定位、用户、产品、销售、内容审美、数据证据和路线参考。资料基线为 2026-11-11，版本 1.0；报价、产品状态和技术主张需结合最新依据核实。

已接入 TeamAI 的同事执行 `teamai pull` 同步，或在支持启动钩子的 AI 工具中开启新会话。然后向 AI 提出：

```text
使用 guide-harlowelife-commercial，为新销售准备一份 10 分钟的品牌与产品培训。
```

```text
使用 guide-harlowelife-commercial，为 SOLA Desk 写中文产品详情页，标出需要核实的内容。
```

也可以下载本仓库，将 `skills/guide-harlowelife-commercial` 整个文件夹安装到支持 Skills 的 AI 工具中，保留全部参考文件。
