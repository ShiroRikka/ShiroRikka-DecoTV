# DecoTV v0.4.0 - OrionTV 完整支持版本 🎉

## 🌟 更新亮点

这是一个重要的功能更新版本，**全面支持 OrionTV 1.3.11 客户端**！现在你可以使用 OrionTV 享受 DecoTV 的全部功能，包括播放记录同步、收藏管理、多设备协同等。

### 🎯 主要新功能

- ✨ **OrionTV 1.3.11 完整兼容**：实现完整的 LunaTV 兼容 API
- 🔐 **Cookie 认证系统**：安全的用户认证，支持多设备登录
- 🌐 **完整 CORS 支持**：解决跨域访问问题，确保客户端正常工作
- 📱 **多设备数据同步**：播放记录、收藏、搜索历史自动同步
- 📚 **完善的使用文档**：详细的 OrionTV 配置指南

## 📝 完整更新日志

### ✨ Added - 新功能

1. **OrionTV 客户端完整支持**

   - 新增 `/api/search/resources` API - 获取视频源列表
   - 新增 `/api/search/one` API 的 CORS 支持 - 单源搜索
   - 实现 LunaTV 兼容的认证系统
   - 支持 OrionTV 1.3.11 及更高版本

2. **CORS 跨域支持**

   - 为搜索 API 添加完整的 CORS headers
   - 实现 OPTIONS 预检请求处理
   - 支持跨域 Cookie 认证

3. **完善文档**
   - 新增 `docs/OrionTV使用指南.md`
   - 包含快速开始、API 列表、常见问题解答
   - 提供详细的配置步骤和技术说明

### 🔧 Changed - 改进

1. **API 认证增强**

   - `/api/search/resources` 现在需要登录认证
   - `/api/search/one` 保持认证要求
   - 更安全的用户数据保护

2. **错误处理优化**

   - 统一的错误响应格式
   - 更友好的错误提示信息
   - 改进的网络异常处理

3. **代码质量提升**
   - 规范化 CORS 响应头
   - 统一 API 响应格式
   - 优化类型定义

### 🐛 Fixed - 修复

1. **OrionTV 兼容性问题**

   - 修复"请检查网络或者服务器地址是否可用"错误
   - 解决跨域请求失败问题
   - 修复 CORS 预检请求被拒绝

2. **认证相关问题**

   - 修复部分 API 缺少认证检查
   - 改进 Cookie 验证逻辑
   - 修复跨域 Cookie 传递

3. **API 响应问题**
   - 修复缺少 CORS 头导致的请求失败
   - 统一所有响应的 CORS 配置
   - 修复 OPTIONS 方法未实现

### 🔧 Technical - 技术细节

1. **LunaTV API 兼容层**

   - 实现 OrionTV 所需的核心 API
   - 保持与原版 LunaTV 的接口兼容
   - 支持 Cookie-based 认证机制

2. **跨域资源共享 (CORS)**

   - Access-Control-Allow-Origin
   - Access-Control-Allow-Credentials
   - Access-Control-Allow-Methods
   - Access-Control-Allow-Headers

3. **认证系统**

   - HMAC-SHA256 签名验证
   - Cookie 安全属性配置
   - 支持 SameSite=None 跨站传递

4. **多客户端支持**
   - OrionTV 客户端（LunaTV API）
   - TVBox 客户端（配置文件）
   - Web 浏览器访问

## 🚀 OrionTV 快速开始

### 1️⃣ 准备工作

确保你的 DecoTV 已部署并可以通过浏览器访问，例如：

```
https://your-deco-tv.com
```

### 2️⃣ 配置 OrionTV

1. 打开 OrionTV 客户端
2. 进入 **设置** → **服务器配置**
3. 填写以下信息：
   - **服务器地址**: `https://your-deco-tv.com` （你的 DecoTV 域名）
   - **用户名**: 你的 DecoTV 用户名
   - **密码**: 你的 DecoTV 密码
4. 点击 **登录**

### 3️⃣ 开始使用

登录成功后，你可以：

- 🔍 搜索影视内容
- ⭐ 收藏喜欢的影片
- 📝 自动同步播放记录
- 📱 在多设备间无缝切换

## 📋 支持的 API 列表

DecoTV v0.4.0 支持以下 OrionTV/LunaTV API：

| API 端点                | 功能           | 认证 |
| ----------------------- | -------------- | ---- |
| `/api/login`            | 用户登录       | ❌   |
| `/api/search/resources` | 获取视频源列表 | ✅   |
| `/api/search/one`       | 单源搜索       | ✅   |
| `/api/detail`           | 获取视频详情   | ✅   |
| `/api/favorites`        | 收藏管理       | ✅   |
| `/api/playrecords`      | 播放记录       | ✅   |
| `/api/searchhistory`    | 搜索历史       | ✅   |
| `/api/image-proxy`      | 图片代理       | ❌   |

## 📖 详细文档

查看完整的 OrionTV 使用指南：

- [docs/OrionTV 使用指南.md](./docs/OrionTV使用指南.md)

## 🔄 升级指南

### 从 v0.3.x 升级

1. **拉取最新代码**：

   ```bash
   git pull origin main
   ```

2. **安装依赖**（如有新增）：

   ```bash
   pnpm install
   ```

3. **重新构建**：

   ```bash
   pnpm build
   ```

4. **重启服务**

### 配置迁移

- ✅ 无需修改现有配置
- ✅ 现有 TVBox 配置继续可用
- ✅ 数据库自动兼容
- ✅ 用户数据自动保留

## 🛠️ 技术要求

- **Node.js**: >= 18.17.0
- **部署平台**:
  - ClawCloud (推荐)
  - Vercel
  - 自托管服务器
- **存储**: Upstash Redis 或本地存储

## 🐛 已知问题

- 暂无

## 🙏 致谢

感谢所有提出建议和反馈的用户！特别感谢 OrionTV 用户的测试和反馈。

## 📞 支持与反馈

遇到问题或有建议？

- 🐛 [提交 Issue](https://github.com/Decohererk/DecoTV/issues)
- 💬 [GitHub Discussions](https://github.com/Decohererk/DecoTV/discussions)

---

**完整更新日志**: [v0.3.0...v0.4.0](https://github.com/Decohererk/DecoTV/compare/v0.3.0...v0.4.0)

**下载**: [GitHub Releases](https://github.com/Decohererk/DecoTV/releases/tag/v0.4.0)
