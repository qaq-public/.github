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

## 测开团队的定位
笔者曾先后就职于网易游戏、莉莉丝、哔哩哔哩游戏等多家游戏，综合不同公司的情况，大致总结如下: 

高效研发支援团队，专注于通过自主开发及外部工具集成提高研发团队工作效率和开发质量，从而提升游戏版本迭代速度、质量，同时致力于提升全公司工作流程效率和质量。
核心职能：
-  设计和开发内部工具，以解决QA、程序、策划、美术、运营等团队在游戏开发和维护过程中遇到的技术障碍与协作障碍。
- 通过深入了解各岗位工作流程，识别效率瓶颈，抽象问题，并开发或集成解决方案，如自动化测试、数据监控、内容管理系统等。
- 根据团队需求和项目阶段，及时将合适的工具和改进方案推广给相关人员，确保团队能够快速、高效地适应新工具，提高生产力。
- 主动发现并指出工作中的低效或错误行为，引入行业最佳实践和高效工具，帮助团队优化工作方法，减少错误，提高工作质量。

## QAQ平台的定位
游戏研发周期相对较长，研发人员较多，由此导致射击的工具也比较多。QAQ承担着**管道**和**胶水**的作用。
- 管道 打通不知职位人员的壁垒，把工作流串联起来。
- 胶水 以IM(飞书)和Git(GitLab)为中心把不同的工具粘合起来。模糊平台之间的分界线，使数据在不同的平台之间流动起来，让用户在使用体验上像是使用一个完整的产品。