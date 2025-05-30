<!-- by 朱淼佳 -->

## 2. 功能特性

本项目提供以下核心功能：

### 2.1 HTTP 请求与响应日志记录
- 基于 Spring AOP，创建一个拦截器，拦截所有的 HTTP 请求和响应。
- 在拦截器中记录请求的路径、方法、参数和响应数据。
- 优点：解耦业务代码和日志逻辑，实现灵活的日志记录。

- 使用 Spring 的 HandlerInterceptor：
- 实现 HandlerInterceptor 接口，在 preHandle 和 postHandle 方法中记录请求和响应。
- 优点：提供了更直接的方式来拦截和处理 HTTP 请求。

- 使用第三方库（如 Logbook）：
- 直接集成 Logbook，它能够自动记录 HTTP 请求和响应数据。
- 配置简单，支持多种扩展。

### 2.2 支持多种日志格式
- 基于日志框架（如 Logback 或 Log4j）配置格式：
- 通过 Logback 的配置文件（logback.xml）或 Log4j 的 YAML/JSON 配置文件，定义不同格式的日志输出模板。
- 优点：简单易用，支持多种输出格式。

- 使用日志适配器/转换器：
- 实现一个日志适配器，将日志内容转换为不同格式（如 JSON、XML 或自定义格式）。
- 优点：灵活性高，可根据需求定制输出。

- 多格式日志输出器：
- 创建一个自定义的日志输出器，根据配置动态选择日志格式（如 JSON、纯文本等）。
- 优点：支持在同一系统中同时输出不同格式的日志。

## 2.3 灵活的日志过滤
- 基于正则表达式的过滤：
- 使用正则表达式匹配 URL、请求参数或响应内容，动态过滤日志。
- 优点：更精确的过滤规则，适合复杂场景。
- 动态规则引擎：

- 集成规则引擎（如 Drools 或 EasyRules），支持以规则文件或动态加载的方式定义过滤条件。
- 优点：支持更复杂的逻辑和条件组合。

- 分布式过滤规则：
- 在分布式系统中，集中管理日志过滤规则，并同步到各服务实例。
- 优点：统一规则，便于维护。

##  2.4 配置动态调整
- 配置中心支持：
- 集成配置中心（如 Spring Cloud Config、Apollo 或 Nacos），动态加载日志相关配置。
- 优点：集中化管理，支持实时更新。

- 基于数据库的配置更新：
- 将日志配置存储在数据库中，通过管理界面实时修改和生效。
- 优点：易于操作，适合运维团队使用。

- 热点更新机制：
- 利用 Spring Boot 的 @ConfigurationProperties 和热加载机制，监听配置文件的变化并实时生效。
- 优点：实现简单，适合小型项目。

##  2.5 性能优化
- 日志批量写入：
- 将日志数据暂存到内存队列中，定期批量写入磁盘或外部存储。
- 优点：减少 I/O 操作，提高写入效率。

- 日志压缩存储：
- 在写入日志文件时，使用 GZIP 等压缩算法对数据进行压缩。
- 优点：节省存储空间，适合大规模日志数据。

##  2.6 扩展性强
- 支持多种存储目标：
- 提供接口支持，将日志写入文件、数据库、消息队列（如 Kafka、RabbitMQ）或云存储。
- 优点：适应不同的存储需求。

- 基于消息中间件的日志流转：
- 将日志数据作为消息发送到中间件（如 Kafka），再由独立服务处理日志存储或分析。

- 优点：支持高并发日志处理。


<!-- by 唐文广 -->
## 4. 快速开始
温馨提示：你需要完成环境的配置才能部署本项目，本项目要求JDK最低1.8及以上，安装了Gradle 3.3及以上版本。
按照以下步骤，您可以快速启动本项目：

### 4.1 克隆代码
首先，克隆项目代码到本地：
```bash
git clone https://github.com/anyEkko/logbook-spring-boot-demo.git
```
![alt text](img/image.png)

### 4.2 构建项目
使用 gradle 进行构建：
```bash
gradlew build
```
构建成功结果如下
![alt text](img/gradlewbuild.png)
 
### 4.3 启动服务
运行以下命令启动 Spring Boot 服务：
```bash
gradlew bootRun
```
启动成功后如下：
![alt text](img/gradlewbootRun.png)

### 4.4 访问服务
项目启动后，默认监听 `http://localhost:8080`，您可以通过浏览器或工具（如 Postman）访问测试。  
我们可以访问 `http://localhost:8080/echo/` + 任意你想测试的用例。  
例如：我们访问 `http://localhost:8080/echo/helloworld`。  
我们可以先在网页上看到helloworld字样。  
![alt text](img/helloworld2.png)  
我们在后台也可以清楚看到样例的信息： 
![alt text](img/helloworld.png)
---
=======
- 优点：支持高并发日志处理。

