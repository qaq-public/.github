<p align="center">
  <img width="192px" src="./logo.svg">
</p>
<p align="center">
😄 让测试充满乐趣！😄
</p>

# QAQ

## QAQ是什么
QAQ是一些*测开基建* + 一种*设计模式* + 一些基于这些*测开基建*和*设计模式*开发或改造的*测试服务*组成的集合体。
开源版本会包含的测试服务：
- 包体管理平台 - 网易TestEase平替
- 测试用例管理平台
- PerfDragon - 腾讯PerfDog平替
- GitDog
- 私服管理平台
- 为完待续...

## QAQ由来
作者曾先后在多家游戏公司担任测试开发工作，积累了丰富的经验。将其中较为通用的部分抽离了出来，形成了QAQ。

---

QAQ全称Quality Assurence Qualification，是一个一站式的云原生测试平台，致力于质量体系建设和游戏品质提升，解决测试领域测试资产难维护、测试质量难度量，测试工具分散等痛点。覆盖游戏研发全流程，平台集成质量门户、效能提升、测试环境构建、游戏持续集成、功能测试、客户端性能测试、服务端性能测试、安全测试、自动化测试等优秀产品服务，满足项目从研发到运营各阶段的测试需求，360度保障游戏质量。

QAQ基础组件包含：
- static *人性化的文件存储服务，golang + vue3实现*
- gateway *Springboot Gateway实现的API网关，依赖mysql*
- uniauth *rbac权限管理，OAuth2登陆，与飞书交互等功能，springboot实现依赖mysql*
- uniauth-web *QAQ门户、全局导航、gateway和uniauth的对应的前端操作界面，react实现*
- docs *平台文档系统，QAQ主站及子产品通过iframe引入docs的页面做产品介绍等文档，docusaurus实现* 这里还有一个备选方案，使用飞书[云文档组件](https://open.feishu.cn/document/uYjL24iN/uYDO3YjL2gzN24iN3cjN/access-notice)，优点是不用部署docs，缺点是样式不可控

可选
- upload "基于s3的文件存储服务，无界面, django-rest-framework实现"

平台服务本身服务发现依赖Kubernets提供的能力，其他微服务治理推荐使用Service Mess([istio](https://istio.io/latest/about/service-mesh/))的方式，需自行引入

## 如何部署
QAQ从其前身发展至今，经历过多种部署方式：
- 第一代：服务器裸机部署 + supervisor进程管理
- 第二代：Docker部署 + Docker Compose进程管理[docker-compose](https://github.com/qaq-public/docker-compose)
- 第三代：Kubernetes Kustomize [kustomize](https://github.com/qaq-public/kustomize)
- 第四代：Helm Charts [helm-charts](https://github.com/qaq-public/helm-charts)

第一代方式不推荐，后续三代部署方式各有优缺点，且都有提供。请根据自身情况，自行选用。

