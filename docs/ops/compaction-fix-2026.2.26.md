# OpenClaw 2026.2.26 上下文压缩修复

## 背景
默认 `compaction.mode: "safeguard"` 在大上下文时可能**静默失败**，导致上下文无法自动压缩。

## 修复方案（配置级）
将 compaction.mode 改为 `default`。

### openclaw.json 示例
```json
{
  "agents": {
    "defaults": {
      "compaction": {
        "mode": "default"
      }
    }
  }
}
```

### CLI 一键修改
```bash
openclaw config.patch --json '{"agents":{"defaults":{"compaction":{"mode":"default"}}}}'
```

## 说明
- 此修复无需升级 OpenClaw 版本
- 与浏览器 Relay 修复独立
- 修改后 Gateway 会自动重启
