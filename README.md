# Like Sports Project

<p align="center">
  <strong style="font-size: 2em;">Like Sports</strong>
</p>

<p align="center">
  <strong>做自己喜欢的</strong>
</p>

## 项目概述

Like Sports是一个基于人工智能的运动训练和分析平台，致力于为篮球和网球等运动提供动作分析、比赛数据、视频编辑分享等服务。

### 子项目

本仓库包含以下三个主要子项目：

1. **Like Sports App** (`like-sports-app/`)
   - Flutter开发的移动应用
   - 支持iOS和Android平台
   - 提供实时动作分析和视频处理功能
   - [查看详情](like-sports-app/README.md)

2. **Like Sports API** (`like-sports-api/`)
   - Go语言开发的后端服务
   - RESTful API设计
   - 处理用户认证、数据存储和业务逻辑
   - [查看详情](like-sports-api/README.md)

3. **Like Sports Website** (`like-sports-os/`)
   - Next.js开发的官方网站
   - 响应式设计
   - 产品展示和用户下载入口
   - [查看详情](like-sports-os/README.md)

## 技术栈

- **移动端**
  - Flutter 3.24.1
  - Dart
  - TensorFlow Lite

- **后端**
  - Go 1.21+
  - MySQL 8.0
  - Docker

- **网站**
  - Next.js 14.1.0
  - React 18
  - TypeScript

## 开发环境设置

### 前置要求

- Flutter SDK 3.24.1
- Go 1.21+
- Node.js 18+
- Docker & Docker Compose
- MySQL 8.0

### 快速开始

1. 克隆仓库：

```bash
git clone https://github.com/like-sports/like-sports.git
cd like-sports
```

2. 启动API服务：

```bash
cd like-sports-api
make dev
```

3. 运行移动应用：

```bash
cd like-sports-app
flutter pub get
flutter run
```

4. 启动网站：

```bash
cd like-sports-os
npm install
npm run dev
```

## 部署

### Like Sports App

iOS TestFlight 部署流程:

```bash
# 1. 确保版本号匹配
# pubspec.yaml 中的版本号必须与git tag一致
version: 1.0.0+1

# 2. 创建并推送tag触发自动部署
git tag 1.0.0+1
git push origin 1.0.0+1
```

部署完成后:

- GitHub Actions 会自动构建并上传到 TestFlight
- 通过飞书机器人接收部署状态通知
- 在 App Store Connect 查看构建状态

### Like Sports API

服务器部署:

```bash
# 1. 登录服务器
ssh root@47.101.156.168

# 2. 更新代码并部署
cd /root/like-sports-api
make deploy-prod  # 自动处理镜像构建、推送和部署
```

服务包含:

- Nginx 反向代理 (80/443端口)
- API 服务 (8080端口)
- MySQL 数据库 (3306端口)
- Let's Encrypt SSL证书自动续期

### Like Sports Website

网站部署:

```bash
# 1. 构建并推送镜像
cd like-sports-os
npm run docker-push  # 构建并推送到阿里云容器仓库

# 2. 在服务器上更新
ssh root@47.101.156.168
cd /root/like-sports-api  # 网站部署配置在API项目中
docker compose pull website
docker compose up -d website
```

访问地址:

- 正式环境: <https://like-sports.com>
- API接口: <https://api.like-sports.com>

## 联系我们

- 邮箱：<contact@like-sports.com>
- 网站：<https://like-sports.com>
- 地址：北京市通州区西集镇企业发展服务中心9202号

## 备案信息

京ICP备2024100884号-1
