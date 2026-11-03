# Coze 智能体生成器（DSH 插件）

在 DSH 对话中注册 `coze_generate_agent` 工具：说一句需求，即可生成任意行业的
Coze（扣子，coze.cn）智能体；**配置令牌后自动创建到你的 Coze 空间（可自动发布）**，
未配置时输出配置包 + 粘贴指引。

与 `dify-agent-generator` 插件完全对应：相同的参数、相同的整句需求解析、
相同的提示词生成逻辑；自动创建走 Coze Open API（`POST /v1/bot`）。

## 配置（cordis.patch.yml）

| 键 | 说明 | 默认 |
|---|---|---|
| `cozeApiBase` | Coze Open API 地址 | `https://api.coze.cn` |
| `cozeToken` | 个人访问令牌（PAT）：coze.cn 右上角头像 →「扣子 API」→「个人访问令牌」 | 空（未填则不自动创建） |
| `cozeSpaceId` | 空间 ID：coze.cn 个人空间页 URL `/space/{space_id}` 中的数字串 | 空 |
| `cozePublish` | 创建后是否自动发布 | `false` |

## 用法

对 AI 说：「帮我生成一个宠物选择助手」。

- 已配置令牌：智能体直接出现在你的 Coze 空间（自动设置名称/简介/人设/开场白/建议问题），传 `publish=true` 或配置 `cozePublish: true` 还会自动发布
- 未配置令牌 / `create_in_coze=false`：返回完整配置（YAML）+ 粘贴步骤，可传 `save_path` 存文件

生成逻辑与 Dify 插件版 `coze-agent-generator` 完全一致。
