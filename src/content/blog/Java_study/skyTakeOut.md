---
title: 苍穹外卖项目记录
publishDate: 2025-07-23 20:05:22
description: 重启Java学习！！！
tags:
  - Java
  - 记录
  - 苍穹外卖
heroImage:
  src: ./face_cang.jpg
  color: "#B4C6DA"
language: 中文
---

## Day1

### Springboot各层之间的关系：

HTTP请求 → Controller → Service → Repository → Database
                         ↑
外部服务/其他组件 ← Service

```Markdown
・Controller 层（表示层）：  
负责接收用户请求（如 HTTP 请求）并将其分发给 Service 层进行业务处理，处理完后将结果返回给用户。该层主要关注请求的解析和响应格式的封装。

・Service 层（业务逻辑层）：  
专注于业务逻辑的实现，根据业务规则进行数据处理与转换。该层会调用数据访问层（Repository 层）进行持久化相关操作，并可能整合其他第三方服务或组件，实现整体的业务流程。

・Repository 层（数据访问层 / DAO）：  
与数据库交互，负责数据的持久化和查询操作。通过调用框架（如 Spring Data JPA、MyBatis 等）提供的接口或自定义方法，对数据库进行增删改查等操作。

・Domain/Entity 层（实体层 / 模型层）：  
定义与数据库表结构相对应的实体类或模型类，通常包含对象属性以及与数据库表的映射关系。有时也会将数据的验证或简单的逻辑方法放到实体中，以保持模型与业务概念的一致性。

通过上述分层，项目结构更加清晰：Controller 专注处理请求，Service 专注业务逻辑，Repository 与数据库打交道，而实体层定义核心数据结构，从而实现低耦合、高内聚的开发目标。
```

**第一次运行后端代码失败！原因为：代码存放路径存在中文**

### 本项目层次关系
sky-take-out
├── sky-common            // 公共模块，存放工具类、常量等
├── sky-pojo              // 实体类模块，存放数据模型
├── sky-server            // 核心业务模块，包含控制器、服务等
│   ├── src/main/java     // Java 源代码
│   │   └── com.sky
│   │       ├── controller    // 控制器层，处理HTTP请求
│   │       ├── service       // 服务层，处理业务逻辑
│   │       ├── mapper        // 数据访问层，与数据库交互
│   │       ├── aspect        // 切面，处理横切关注点
│   │       ├── config        // 配置类
│   │       ├── filter        // 过滤器
│   │       ├── handler       // 处理器
│   │       ├── interceptor   // 拦截器
│   │       ├── task          // 定时任务
│   │       └── websocket     // WebSocket相关
│   └── src/main/resources    // 资源文件
│       ├── application.yml   // 应用配置
│       └── mapper            // MyBatis映射文件
└── pom.xml                   // Maven项目配置文件

### 理清设计架构

#### 1. common 文件夹

- **用途**: 存放项目中可以被多个模块共享的通用类和工具类。
- **常见文件类型**:
    - 工具类（Utility Classes）：实现常用的功能，例如字符串处理、日期处理、文件处理等。
    - 常量类（Constants）：定义许多全局使用的常量。
    - 异常类（Custom Exceptions）：定义自定义的异常，用于处理业务逻辑层中的特定情况。
    - 配置类：项目中使用的配置信息的集中管理。

#### 2. server文件夹

- **用途**: 通常存放与应用服务器相关的代码，包括控制器、服务层和数据访问层的实现。
- **常见文件类型**:
    - 控制器（Controllers）：处理 HTTP 请求，调用服务层逻辑。
    - 服务类（Services）：包含业务逻辑，处理数据，也可能进行事务管理。
    - 数据访问对象（DAOs）：与数据库进行交互的类，使用 ORM 框架（如 MyBatis）进行数据的 CRUD（增删改查）操作。
    - 配置相关的类（如 Spring 配置、MyBatis 配置等）。

#### 3. pojo 文件夹

- **用途**: 存放 Plain Old Java Objects（POJOs），即简单的 Java 对象，用于表示数据模型。
- **常见文件类型**:
    - 实体类（Entities）：通常与数据库表直接映射，用于表示数据库中的记录。
    - 数据传输对象（DTOs）：在不同层之间传递的数据结构，通常较为简单，不包含业务逻辑。
    - 可能还包括值对象（Value Objects）：用来表示不可变的数据结构。

#### 总结

- **common**: 通用工具类和常量等。
- **server**: 服务层、控制器和数据访问层等与业务逻辑相关的实现。
- **pojo**: 数据模型和简单数据结构，用于存储和传输数据。