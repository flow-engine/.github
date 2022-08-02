![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659434745739-ffa88bec-e362-4ba1-95ba-6b873a3f0d5c.png#clientId=u48b5bad2-fff4-4&crop=0&crop=0&crop=1&crop=1&from=paste&id=u326cb212&margin=%5Bobject%20Object%5D&name=image.png&originHeight=167&originWidth=641&originalType=binary&ratio=1&rotation=0&showTitle=false&size=19367&status=done&style=none&taskId=u7fd8b14b-116e-4b29-a12d-464d2089226&title=)
# 简介
## 定位
对于一个数据策略型应用，一般需要多个子系统或者中间件来支持离线批量任务处理，近线流式任务处理，和在线实时请求，在现有架构中，三者割裂，支撑工具各有不同，服务运维和上层编程接口及操作方式各不相同，导致协同工作，运营维护，整体优化变得很困难，技术团队不得不花费大量人力和机器成本来维持系统运转，另一方面，数据策略类系统一个重要特点就是频繁变化，缺少灵活的策略编排能力及策略方案版本管理，分享，重建能力，导致应用开发，测试，部署都十分困难。
**FloweEngine 是一个覆盖离线，近线，在线场景的声明式云原生的流程编排框架，覆盖方案开发，应用管理全过程，旨在助力快速，正确的搭建策略应用。**
**其包含以下核心内容：**

- 简单一致的声明式API/SDK/GUI
- 统一的业务流，数据流编排（离线编排，在线编排，流式编排）（低门槛，低代码）
- 架构开放的基础上，内置Runtime支撑80%以上场景 （开放性，组件化）
- 应用方案沉淀，迁移，一键重建（以 asol 为核心）
## ![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659430395047-653128b3-b3a9-4910-bfd4-abc1f48eafe8.png#clientId=u48b5bad2-fff4-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=377&id=ua794e2cb&margin=%5Bobject%20Object%5D&name=image.png&originHeight=754&originWidth=1096&originalType=binary&ratio=1&rotation=0&showTitle=false&size=83768&status=done&style=none&taskId=u28eb6c25-a647-41ae-86d4-c1a6b70ca7a&title=&width=548)
## 基本架构 
在架构上，flowengine由APP，DATA，HUB三部分构成，分别负责引擎管理，数据管理和方案（asol），组件（sc），任务模版（job，streamJob，func）等资源管理。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659429691404-c171ed8b-e729-4d23-a1c8-f476ca7c2bb5.png#clientId=u48b5bad2-fff4-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=351&id=u6024ad2c&margin=%5Bobject%20Object%5D&name=image.png&originHeight=702&originWidth=1212&originalType=binary&ratio=1&rotation=0&showTitle=false&size=108607&status=done&style=none&taskId=u409ada3b-cf98-4361-a2d4-ff1d3b22f7a&title=&width=606)
在负载管理上，采用了两级管理，引擎manager管理多个引擎，引擎内部由engineKernel协调管理，引擎彼此形成独立的逻辑（物理）单元，这样能够便于开发者或者使用者能够结合实际业务做很好的业务拆分，从而更自然的获得可用性和利用率上的平衡。
## 业务分解及技术映射
通过flowengine开发数据策略类场景应用，关键是对场景的分析及映射。在flowengine里我们将一个应用映射成如下形态。 以一个推荐场景为例：
![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659431199237-35792eea-b7e7-4c0c-bb04-bcaf97e9deb1.png#clientId=u48b5bad2-fff4-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=355&id=u8e069de4&margin=%5Bobject%20Object%5D&name=image.png&originHeight=710&originWidth=1676&originalType=binary&ratio=1&rotation=0&showTitle=false&size=167003&status=done&style=none&taskId=u9167c64a-45b5-41a2-b079-b3d99654643&title=&width=838)
如图，一个AI模型训练到服务的过程就是一个引擎，引擎内部声明了这个过程的运行逻辑，对外暴露数据和服务接口。 而flowengineData对接外部业务系统，并将数据加工完成，绑定到各个场景引擎上，不同引擎对外提供不同的服务，如模型推理服务或是推荐服务。 最终，它们一起形成了一个完整的场景服务。开发一个场景即是定义数据流和引擎服务的过程，通过声明式的API或者界面操作完成整个开发过程。
## 起源
该框架最初源自于第四范式，从2017年末一直发展到现在，从最初的MLOPS工具，到AI场景项目的交付工具，再到AI业务系统的底层支撑框架历经了三个阶段，用户群，从公司内部交付开发，到产品开发，再到客户开发者不断扩大。当前，商业版本被金融，零售，电信等行业巨头广泛使用，其使用体验及稳定性表现接受了其业务的长期考验，也被开发者所接受，为了更好的满足客户，爱好者学习，了解，贡献，第四范式决定将其贡献到社区，借助社区的力量，让它能够变得更好。
# 框架特点
框架具备两个鲜明特点：1）好上手    2）好维护
1）好上手 

- 一致的可视化交互界面和开发接口，轻松完成pipeline的开发，部署，运行。

![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659432901940-508c6865-daa8-482f-a45a-1c57685e2bc7.png#clientId=u48b5bad2-fff4-4&crop=0.1256&crop=0.1153&crop=1&crop=1&from=paste&height=597&id=u2e64a3a2&margin=%5Bobject%20Object%5D&name=image.png&originHeight=1366&originWidth=2802&originalType=binary&ratio=1&rotation=0&showTitle=true&size=389611&status=done&style=none&taskId=u07f0b4b2-1e51-42bc-8380-3213f04dc8f&title=%E7%A6%BB%E7%BA%BF%E6%89%B9%E9%87%8F%E7%BC%96%E6%8E%92&width=1225 "离线批量编排")
![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659432910918-1076b223-4385-4118-a210-a49dba788de7.png#clientId=u48b5bad2-fff4-4&crop=0.1174&crop=0.111&crop=1&crop=1&from=paste&height=612&id=uc417bc4d&margin=%5Bobject%20Object%5D&name=image.png&originHeight=1386&originWidth=2820&originalType=binary&ratio=1&rotation=0&showTitle=true&size=426878&status=done&style=none&taskId=u4761db44-cf7a-46e8-9140-e91862b6c4c&title=%E5%9C%A8%E7%BA%BF%E5%AE%9E%E6%97%B6%E7%BC%96%E6%8E%92&width=1245 "在线实时编排")
![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659432921819-01863c30-f09a-4737-afd0-bd67c0fafd65.png#clientId=u48b5bad2-fff4-4&crop=0.1207&crop=0.0611&crop=1&crop=1&from=paste&height=602&id=u509cbbbb&margin=%5Bobject%20Object%5D&name=image.png&originHeight=1370&originWidth=2812&originalType=binary&ratio=1&rotation=0&showTitle=true&size=274645&status=done&style=none&taskId=uff8e412c-119b-4cde-ae11-58529f51a51&title=%E8%BF%91%E7%BA%BF%E6%B5%81%E5%BC%8F%E7%BC%96%E6%8E%92&width=1236 "近线流式编排")

- 逻辑分层，学习曲线平缓，从使用方案到开发方案，从使用第三方资源到自己开发自定义资源，能够更好聚焦问题本身。

![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659433297587-07323c8c-9a49-4362-a95f-c73bd07a320b.png#clientId=u48b5bad2-fff4-4&crop=0&crop=0.1019&crop=0.9785&crop=1&from=paste&height=671&id=u74ce8819&margin=%5Bobject%20Object%5D&name=image.png&originHeight=1372&originWidth=2820&originalType=binary&ratio=1&rotation=0&showTitle=false&size=478173&status=done&style=none&taskId=u4c97ef3a-bd8a-44b5-b425-384b04ec529&title=&width=1380)

- 业务场景内聚，纵向隔离，便于管理及业务差异化发展 。通过flowengine层的抽象，使得场景间相互独立，开发运维更加内聚，能够更好的在业务维护进行优化管理，减少相互影响以及引入不必要的信息过载。

2）好维护

- 通过整合在线，离线，近线编排，提升了基础设施的一致性和中间件数量
- 基础设施和场景应用分离，方案版本化管理，支持导入导出，重建和迁移更容易
- 云原生架构，两级负载管理，可以轻松根据业务特点完成弹性伸缩。
# 如何使用
详见：
# 和我们联系
加入我们的官方微信群：
在github上提issue：
# 加入贡献
详见：
repo结构简介 
如何编译打包 
A Open Source Project From 4paradigm.com
