# Token 消耗排名 - 在线版使用说明

## 快速部署

### 方式一：Vercel 部署（推荐）

1. 将以下两个文件放到同一个 Git 仓库：
   - `token消耗排名.html` — 前端页面
   - `token-data.csv` — 数据文件（从 DeepSeek 导出的 CSV）

2. 推送代码到 GitHub

3. 在 [Vercel](https://vercel.com) 导入该仓库，一键部署

4. 部署后，每次更新数据只需：
   - 在 DeepSeek 后台导出最新的 CSV
   - 替换仓库中的 `token-data.csv`
   - 提交代码，Vercel 会自动重新部署

### 方式二：GitHub Pages 部署

1. 将文件推送到 GitHub 仓库
2. 仓库 Settings → Pages → Source 选择对应分支
3. 访问 `https://用户名.github.io/仓库名/`

## 使用方式

用户打开页面后有三种方式加载数据：

1. **🔄 刷新数据** — 自动加载同目录下的 `token-data.csv`（默认配置）
2. **📊 上传 CSV** — 手动选择本地 CSV 文件
3. 拖拽 CSV 文件到页面任意位置

## 自定义数据源

如果 CSV 文件不在同一目录下，编辑 HTML 文件，修改第 1 行的配置：

```javascript
const CSV_FILE = 'token-data.csv';
```

改为你的 CSV 文件路径，例如：
```javascript
const CSV_FILE = 'https://example.com/data/latest.csv';
```

## CSV 文件格式

从 DeepSeek 导出的 CSV 格式，包含以下列：
- `user_id` — 用户 ID
- `utc_date` — 日期
- `model` — 模型名称
- `api_key_name` — API Key 名称（用于区分账号）
- `api_key` — API Key
- `type` — 类型（request_count / input_cache_hit_tokens / input_cache_miss_tokens / output_tokens）
- `price` — 单价
- `amount` — 数量
