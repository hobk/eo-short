# EdgeOne 短链接服务

基于腾讯云 EdgeOne构建的简单快速、无服务器短链接服务。

⚠️（[KV存储](https://console.cloud.tencent.com/edgeone/pages?tab=kv)开放名额有限，**审核通过后可用**）


## 🚀 核心功能

- **短链生成**: 自动生成随机短链接标识符，支持自定义
- **访问统计**: 实时跟踪每个短链接的访问次数
- **管理界面**: 简洁的 Web 界面管理所有短链接

## 🔧 一键部署

### 1. 部署：

[![使用国内版EdgeOne Pages 部署](https://cdnstatic.tencentcs.com/edgeone/pages/deploy.svg)](https://console.cloud.tencent.com/edgeone/pages/new?repository-url=https%3A%2F%2Fgithub.com%2Fhobk%2Feo-short%2F)（国内版）

[使用国际版部署](https://edgeone.ai/pages/new?repository-url=https%3A%2F%2Fgithub.com%2Fhobk%2Feo-short%2F)

### 2. 新建并绑定 KV 数据库
- 第一步项目部署后，进入 EdgeOne 控制台
- 在项目设置中，导航到 **KV 存储** 部分
- 创建一个新的 KV 数据库命名空间
- 使用指定变量名 `my_kv` 将此 KV 数据库命名空间绑定到您的项目
- 找到最新一次的部署，重新部署即可生效，建议绑定自定义域名

### 3. 配置管理页面（可选，未设置则不启用管理页面）
如果需要管理界面（支持查看所有短链，删除短链），可以在 **项目设置 --> 环境变量** 中设置：
- 变量名为`ADMIN_PATH`: 管理页面路径，例如设置变量值为`abc123`，则管理页面地址为`https://你的自定义域名/abc123`
- ⚠️安全提示：请勿设置常用路径，以免被他人恶意访问


## 🎯 使用方法

1. **访问管理界面**: 打开您的 EdgeOne Pages 域名
2. **创建短链接**: 在输入框中粘贴长 URL，点击创建
3. **使用短链接**: 访问生成的短链接会自动重定向到原始 URL
4. **查看统计**: 在管理界面查看所有短链接及其访问次数


## ✨ 项目特色

- **零静态文件**: 整个前端是一个自包含的 HTML 文档，直接从函数提供服务，无需单独的前端框架或构建过程
- **动态路由**: 单个 EdgeOne Function 作为通用路由器：
  - 为根路径 (`/`) 提供主仪表板
  - 将有效的短链接 (`/:slug`) 重定向到原始 URL
  - 跟踪每个链接的访问次数
- **无服务器架构**: 基于 EdgeOne 的全球基础设施，确保低延迟和高可用性
- **简单部署**: 只需最少的设置，配置 KV 绑定并部署函数即可

## 🔒 安全特性

- 自动输入验证和清理
- 防止恶意 URL 注入
- 基于 EdgeOne 的全球 CDN 防护、加速
- 可选的管理界面密码保护



### API 接口
- `POST /api/create` - 创建新的短链接
- `GET /api/links` - 获取所有短链接列表
- `DELETE /api/delete` - 删除指定的短链接


## 🤝 贡献

欢迎贡献代码、报告问题和功能请求！请随时查看 [issues 页面](https://github.com/hobk/eo-short/issues)。

## 许可证

MIT License
