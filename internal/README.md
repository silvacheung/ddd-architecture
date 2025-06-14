# 这里是内部的模块代码
## 注意！
1. 这里面的第一层级应该只有目录
2. 这里应该以模块来组织目录名称
3. 这里的模块代码对外只有cmd的main.go文件可以引用

## 模块代码目录结构应该使用`清洁的DDD领域驱动设计(Clean DDD)`的结构来组织，例如：
```text
|-internal
  |-example // 模块(主领域)
    |-kernel // DDD领域核心层
      |-application // 应用服务层
        |-user_service.go // user子领域应用层服务
        |-user_model.go // user子领域应用层模型定义
        |-order_service.go // order子领域应用层服务
        |-order_model.go // order子领域应用层服务
      |-domain // 领域层
        |-user_model.go // user子领域模型
        |-user_repository.go // user子领域存储
        |-user_service.go // user子领域服务
        |-order_model.go // order子领域模型
        |-order_repository.go // order子领域存储
        |-order_service.go // order子领域服务
    |-infras // 基础设施层
      |-cron // 定时
        |-user_cron.go // user领域定时实现
        |-order_cron.go // order领域定时实现
      |-cache // 缓存
        |-user_cache.go // user领域缓存实现
        |-order_cache.go // order领域缓存实现
      |-event // 事件
        |-user_event.go // 消费关于user领域的事件，并做出处理
        |-order_event.go // 消费关于order领域的事件，并做出处理
      |-repos // 存储
        |-mysql_user_repository.go // mysql实现user领域的Repository
        |-mysql_order_repository.go // mysql实现order领域的Repository
    |-cqrs // 命令查询分离层
      |-user_command.go 
      |-user_query.go
      |-order_command.go
      |-order_query.go
```

## 整洁架构、DDD 和 CQRS 简介
![clean-ddd-cqrs.png](clean-ddd-cqrs.png)