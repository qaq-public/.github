# QAQ

QAQ全称Quality Assurence Qualification，是一个一站式的云原生测试平台，致力于质量体系建设和游戏品质提升，解决测试领域测试资产难维护、测试质量难度量，测试工具分散等痛点。覆盖游戏研发全流程，平台集成质量门户、效能提升、测试环境构建、游戏持续集成、功能测试、客户端性能测试、服务端性能测试、安全测试、自动化测试等优秀产品服务，满足项目从研发到运营各阶段的测试需求，360度保障游戏质量。

QAQ基础组件包含：
- static *人性化的文件存储服务，golang + vue3实现*
- gateway *Springboot Gateway实现的API网关，依赖mysql*
- uniauth *rbac权限管理，OAuth2登陆，与飞书交互等功能，springboot实现依赖mysql*
- uniauth-web *QAQ门户、全局导航、gateway和uniauth的对应的前端操作界面，react实现*
- docs *平台文档系统，QAQ主站及子产品通过iframe引入docs的页面做产品介绍等文档，docusaurus实现*

可选
- upload "基于s3的文件存储服务，无界面, django-rest-framework实现"

平台服务本身服务发现依赖Kubernets提供的能力，其他微服务治理推荐使用Service Mess([istio](https://istio.io/latest/about/service-mesh/))的方式，需自行引入


## 如何部署
QAQ从其前身发展至今，经历过多种部署方式：
- 第一代：服务器裸机部署 + supervisor进程管理
- 第二代：Docker部署 + Docker Compose进程管理
- 第三代：Kubernetes Kustomize
- 最新：Helm

Requirements:
- a kubernetes cluster with ingress-nginx、PersistentVolume、helm3
- a domian with https cert
- a feishu application

Optional:
- spreate mysql

tofix:
`helm install -n qaq-dev`