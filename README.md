# openclaw-shield

OpenClaw 云服务器安全护盾 Skill。

该 Skill 用于在 Agent 执行命令、文件操作、网络访问前进行安全检查，并在输出前做敏感信息脱敏，重点覆盖提示词注入、外部输入污染、云平台 metadata 访问拦截、审计留痕等场景。

## 主要能力

- 输入安全检测：注入、编码绕过、零宽字符等
- 来源分级：`OWNER_DIRECT`、`TAINTED_OWNER`、`AGENT_AUTO`、`EXTERNAL_DRIVEN`
- 操作前置检查：命令、路径、网络、包安装
- 风险处置：按来源与风险等级执行 `pass/warn/confirm/block`
- 输出脱敏：凭证、连接串、私钥、IP 等敏感信息过滤
- 云端加固：强制拦截 metadata 地址访问（如 `169.254.169.254`）
- 审计记录：全链路可追踪事件日志

## 仓库结构

- `SKILL.md`：Skill 主说明与执行流程
- `agents/openai.yaml`：Skill UI 元数据
- `references/permission-matrix.md`：权限矩阵与来源判定
- `references/detection-and-redaction.md`：威胁检测与脱敏规则
- `references/cloud-boundaries-config.md`：云服务器边界与配置模板
- `references/audit-and-playbook.md`：审计事件与部署检查清单

## 使用方式

1. 将本仓库内容放到本地 Codex skills 目录，例如：

```bash
~/.codex/skills/openclaw-shield
```

2. 在会话中触发与安全执行相关任务时，Codex 会根据 `SKILL.md` 规则执行检查与过滤。

## 适用场景

- 云服务器上的 Agent 自动化执行
- 需要防注入、防越权、防信息泄露的工程任务
- 需要审计可追溯的安全合规场景

## 许可

当前仓库未附加单独许可证文件，如需开源发布建议补充 `LICENSE`。
