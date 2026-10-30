# 安装

```bash
# 方式一：dsh plugin 命令
dsh plugin --profile <your-profile> add file:C:/path/to/dsh-life-engine

# 方式二：手动
# 1. 把目录 link/join 到 <DSH_HOME>/profiles/<profile>/node_modules/dsh-life-engine
# 2. 在 profile 的 package.json dependencies 加 "@local/dsh-life-engine": "link:..."
# 3. 在 profile 的 package.json dsh.profile.bundles 加 "@local/dsh-life-engine"
# 4. 重启 dsh
```

## 配置

cordis.patch.yml 的 config 段设置 `workspace` 为你的工作区路径。所有路径会自动解析。

## 依赖

- node:sqlite (Node.js 22+)
- 可选：本地向量模型 (bge-small-zh 或类似，端口 17861) → 用于 kb_search 向量检索

## MIT License
