# Railway部署指南

## 部署前准备

1. 确保项目已成功推送到GitHub仓库
2. 确保项目包含以下文件：
   - `Procfile`（指定启动命令）
   - `system.properties`（指定Java版本）
   - `src/main/resources/application-railway.properties`（Railway环境配置）

## Railway部署步骤

1. 登录Railway平台 (https://railway.app/)
2. 点击"New Project" > "Deploy from GitHub repo"
3. 选择你的GitHub仓库
4. 部署配置：
   - 选择"Spring Boot"作为框架
   - 等待自动检测项目

## 环境变量设置

在Railway项目的"Variables"选项卡中添加以下环境变量：

```
SPRING_PROFILES_ACTIVE=railway
JDBC_DATABASE_URL=jdbc:mysql://<你的数据库链接>/milk_store?createDatabaseIfNotExist=true&useSSL=false&allowPublicKeyRetrieval=true
JDBC_DATABASE_USERNAME=<数据库用户名>
JDBC_DATABASE_PASSWORD=<数据库密码>
```

可以选择添加其他环境变量：

```
DEEPSEEK_API_KEY=<你的API密钥>
```

## 添加MySQL数据库

1. 在Railway控制台点击"New" > "Database" > "Add MySQL"
2. 添加后，Railway会自动生成并连接数据库

## 部署排查

如果部署失败，请检查以下内容：

1. 日志错误信息
2. 是否正确设置了环境变量
3. 确保pom.xml中指定了正确的主类
4. 是否成功连接了数据库

## 设置自定义域名（可选）

1. 在项目设置中选择"Settings" > "Domains"
2. 添加并验证你的自定义域名 