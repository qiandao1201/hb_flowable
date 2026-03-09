前端部署
# 进入项目目录
cd lx-ui

# 安装依赖
npm install

# 建议不要直接使用 cnpm 安装依赖，会有各种诡异的 bug。可以通过如下操作解决 npm 下载速度慢的问题
npm install --registry=https://registry.npmmirror.com

# 启动服务
npm run dev

# 构建测试环境
npm run build:stage

# 构建生产环境
npm run build:prod

后端部署

# 数据源配置
spring:
datasource:
type: com.alibaba.druid.pool.DruidDataSource
driverClassName: com.mysql.cj.jdbc.Driver
druid:
# 主库数据源
master:
url: 数据库地址
username: 数据库账号
password: 数据库密码

# 开发环境配置
server:
# 服务器的HTTP端口，默认为8080
port: 端口
servlet:
# 应用的访问路径
context-path: /应用路径

首次启动项目前，将 yml 中 flowable 的 database-schema-update 设置为true
# flowable相关表
flowable:
# true 会对数据库中所有表进行更新操作。如果表不存在，则自动创建(建议开发时使用)
database-schema-update: true
# 关闭定时任务JOB
async-executor-activate: false


依次导入sql目录下的sql文件
1、lx_xxxx.sql 框架sql，包含用户，角色权限等基础数据
2、quartz.sql 定时服务sql
3、tony-flowable.sql 流程任务相关sql

