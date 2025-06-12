# Yudao Project Architecture

## 1. Introduction

Yudao is a modular, Spring Boot-based rapid development platform. It aims to provide a comprehensive solution for building various business applications quickly. The project is open-source and emphasizes ease of use and extensibility.

## 2. Core Framework (`yudao-framework`)

The `yudao-framework` module forms the foundation of the project. It consists of several Spring Boot starter modules that provide common functionalities, including:

*   Data Permission
*   IP Utilities
*   Multi-tenancy
*   Excel Handling
*   Job Scheduling (Quartz)
*   Monitoring (Spring Boot Admin, SkyWalking)
*   Message Queues (Redis, RabbitMQ, Kafka, RocketMQ)
*   Database Access (MyBatis Plus, Dynamic Datasource)
*   Security (Spring Security)
*   Testing Utilities
*   Web Utilities (Spring MVC, Swagger)
*   WebSocket Support

This framework provides reusable components and a standardized way of building modules.

## 3. Modules (`yudao-module-*`)

The project is divided into several business modules, each responsible for a specific domain. These modules leverage the `yudao-framework` for common functionalities. Key modules include:

*   **`yudao-module-system`**: Core system functionalities like user management, roles, permissions, departments, menus, tenants, dictionaries, logging, error codes, notifications, sensitive words, and application management for SSO.
*   **`yudao-module-infra`**: Infrastructure services such as code generation, API documentation (Swagger), database documentation, form building, configuration management, scheduled tasks, file services (S3, local, FTP), WebSocket examples, API logging, database monitoring (MySQL, Redis), message queues, Java application monitoring, tracing, logging center, and service protection (distributed locks, idempotency, rate limiting).
*   **`yudao-module-bpm`**: Business Process Management powered by Flowable, supporting features like BPMN designer, simple form-based designer, various task assignment strategies (assignee, candidate users/groups), and process lifecycle management.
*   **`yudao-module-pay`**: Payment system integration, supporting multiple payment channels and managing payment/refund orders.
*   **`yudao-module-mall`**: E-commerce module with features for product management, promotions, trade (orders, cart), and statistics.
*   **`yudao-module-member`**: Manages C-end users (members), including member profiles, tags, levels, groups, and points/rewards.
*   **`yudao-module-mp`**: WeChat Official Account management, including account setup, data statistics, fan management, message handling, auto-replies, tags, menus, and material management.
*   **`yudao-module-report`**: Data reporting and visualization, including a report designer and a dashboard/large screen designer.
*   **`yudao-module-crm`**: Customer Relationship Management functionalities.
*   **`yudao-module-erp`**: Enterprise Resource Planning functionalities.
*   **`yudao-module-ai`**: AI large model integration.
*   **`yudao-module-iot`**: Internet of Things functionalities.


## 4. Server (`yudao-server`)

The `yudao-server` module is the main application entry point. It packages all the framework and business modules into a runnable Spring Boot application. It handles server startup, configuration loading, and request dispatching.

## 5. User Interface (`yudao-ui`)

The project includes several UI applications, primarily for administration purposes:

*   **`yudao-ui-admin-vue3`**: Admin UI based on Vue3 and Element Plus.
*   **`yudao-ui-admin-vben`**: Admin UI based on Vue3 and Vben (Ant Design Vue).
*   **`yudao-ui-admin-vue2`**: Admin UI based on Vue2 and Element UI.
*   **`yudao-ui-admin-uniapp`**: Admin UI for mobile using uni-app.
*   **`yudao-ui-mall-uniapp`**: Mall UI for mobile using uni-app.

These UIs interact with the backend modules via RESTful APIs.

## 6. Database

The application supports multiple database systems, including:

*   MySQL
*   Oracle
*   PostgreSQL
*   SQL Server
*   MariaDB
*   DM (国产达梦)
*   TiDB

SQL scripts for schema creation and data initialization are provided in the `sql/` directory for each supported database. MyBatis Plus is used as the primary ORM and data access framework.

## 7. Key Technologies

*   **Backend**: Java (JDK 8 or 17/21), Spring Boot 2.7.x / 3.2.x, Spring Security, Spring MVC
*   **Database**: MySQL, MyBatis Plus, Druid, Redis (Redisson)
*   **Workflow**: Flowable
*   **Job Scheduling**: Quartz
*   **Frontend**: Vue.js (Vue2/Vue3), Element UI, Element Plus, Ant Design Vue, uni-app
*   **Build & Dependency Management**: Maven
*   **API Documentation**: Swagger (Springdoc)
*   **Monitoring**: Spring Boot Admin, SkyWalking
*   **Messaging**: Event, Redis Streams, RabbitMQ, Kafka, RocketMQ

## 8. Deployment

The application can be deployed using various methods:

*   As a standalone JAR file.
*   Using Docker (docker-compose files are provided in `script/docker/`).
*   Deployment scripts for Jenkins are also available (`script/jenkins/`).

This architecture allows for a scalable and maintainable system, enabling developers to add new features and modules efficiently.
