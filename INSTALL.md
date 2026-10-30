# 安装

## 方式一：dsh plugin 命令（推荐）

```bash
dsh plugin --profile <your-profile> add file:C:/path/to/dsh-life-engine
```

## 方式二：手动

```bash
# 1. 把目录 link/join 到 <DSH_HOME>/profiles/<profile>/node_modules/dsh-life-engine
# 2. 在 profile 的 package.json dependencies 加 "@local/dsh-life-engine": "link:..."
# 3. 在 profile 的 package.json dsh.profile.bundles 加 "@local/dsh-life-engine"
# 4. 重启 dsh
```

## 配置

cordis.patch.yml 的 config 段设置 `workspace` 为你的工作区路径。

### KB 引擎（lib/kb.cjs）

KB 引擎是自包含的，唯一依赖是 Node.js 内置模块（fs/path/zlib/string_decoder）。

环境变量：
- `KB_WORKSPACE` — 工作区根目录（默认 `~/`）
- `DSH_DATA` — 会话数据目录（默认 `D:/dsh-data`，可在代码内改）

### 向量模型

KB 检索需要本地向量模型（bge-small-zh 或兼容），运行在 `127.0.0.1:17861`。
安装方法：用 `@huggingface/transformers` 加载 `Xenova/bge-small-zh-v1.5`（~100MB），暴露 OpenAI 兼容 `/v1/embeddings` 端点。

## MIT License
