![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659434745739-ffa88bec-e362-4ba1-95ba-6b873a3f0d5c.png)

English ｜ [中文](/profile/README-cn.md)

# Introduction
## Project positioning
For a data-driven application, multiple subsystems or middleware are generally required to support offline batch task processing, near-line streaming task processing, and online real-time requests. In the traditional architecture, the three are separated and the supporting tools are different. Service operation and maintenance and upper-layer programming interfaces and operation methods are different, which makes it difficult to work collaboratively, operation and maintenance, and overall optimization. The technical team has to spend a lot of manpower and machine costs to maintain the system operation. On the other hand, data-driven An important feature of the system is that data and policies change frequently, and there is a lack of flexible policy orchestration capabilities and policy solution version management, sharing, and rebuilding capabilities, which makes application development, testing, and deployment very difficult.

**FloweEngine is a declarative cloud-native flow orchestration framework covering offline, near-line, and online scenarios. It supports the whole process of solution development and application management, and aims to help build data-driven applications quickly and correctly.**

**It includes the following core features：**

- Simple and consistent declarative API/SDK/GUI
- Unified business/data flow orchestration (offline, online, nearline)
- open architecture, the built-in Runtime supports more than 80% of the scenarios
- Application solution save, migration, one-click reconstruction
## ![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659430395047-653128b3-b3a9-4910-bfd4-abc1f48eafe8.png)
## Architecture 
In terms of architecture, flowengine consists of APP, DATA, and HUB, which are responsible for engine management, data management and program (asol), components (sc), task templates (job, streamJob, func) and other resource management.
![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659429691404-c171ed8b-e729-4d23-a1c8-f476ca7c2bb5.png)
In terms of workload management, two-level management is adopted. The engine manager manages multiple engines. The engine is coordinated and managed by the engineKernel. The engines form independent logical (physical) units, which makes it easier for developers or users to combine actual business operations. Very good business split, so as to achieve a more natural balance between availability and utilization.
## Decomposition & Mapping
The key to developing data-driven scenario applications through flowengine is the analysis and mapping of scenarios. In flowengine, we map an application into the following form. Take a recommended scenario as an example:
![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659431199237-35792eea-b7e7-4c0c-bb04-bcaf97e9deb1.png)
As shown in the figure, the process of training an AI model to a service is an engine. The engine declares the operation logic of this process and exposes data and service interfaces to the outside world. FlowengineData connects to external business systems, completes data processing, and binds it to each scene engine. Different engines provide different external services, such as model inference services or recommendation services. Ultimately, together they form a complete scene service. Developing a scenario is the process of defining data flow and engine services, and completing the entire development process through declarative API or interface operations.
## Origin
The framework originally originated from 4paradigm, and has developed from the end of 2017 to the present. From the initial MLOPS tool, to the delivery tool of AI scene projects, to the underlying support framework of the AI business system, it has gone through three stages, user group, From in-company delivery development, to product development, to customer developers, it continues to expand. At present, the commercial version is widely used by industry giants such as finance, retail, telecommunications, etc. Its user experience and stability have undergone the long-term test of its business, and it has also been accepted by developers. In order to better satisfy customers, enthusiasts understand and learn , Contribution, Fourth Paradigm decided to contribute it to the community, and make it better with the help of the community.
# Project Highlight

1）Easy to learn & use

- Consistent UI and API, easy to complete the development, deployment and operation of the pipeline

![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659432901940-508c6865-daa8-482f-a45a-1c57685e2bc7.png "Offline batch orchestration")
![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659432910918-1076b223-4385-4118-a210-a49dba788de7.png "Online real-time orchestration")
![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659432921819-01863c30-f09a-4737-afd0-bd67c0fafd65.png "Nearline streaming orchestration")

- The architecture is layered and the learning curve is flat. From the use scheme to the development scheme, from the use of third-party resources to the development of custom resources, it can better focus on the problem itself

![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659433297587-07323c8c-9a49-4362-a95f-c73bd07a320b.png)

![image.png](https://cdn.nlark.com/yuque/0/2022/png/28211224/1659432921819-01863c30-f09a-4737-afd0-bd67c0fafd65.png "Nearline streaming orchestration")

2）easy to maintenance

- Improves infrastructure consistency and reduces the number of services by integrating online, offline, and near-line orchestration
- Separation of infrastructure and scene applications, solution version management, support for import and export, easier reconstruction and migration
- Cloud-native architecture, two-level load management, can easily achieve elastic scaling according to business characteristics

# Quick Start
see details： [Installation Guide](https://github.com/flow-engine/flowengine-release) 
# Contact us
* Join our WeChat group：
  <div align="left">
  <img src="https://cdn.nlark.com/yuque/0/2022/png/28211224/1659592484664-36f51f94-2ab6-43ce-abd7-4dd2f9d07c2f.png" width=25% title="wechat">
  </div>
* Issue on github：https://github.com/flow-engine/.github/issues
# Contribute

Currently, the code is being sorted out, and it will be open soon！

You can submit issues or join group discussions to jointly promote the development of the project！

# License

The code is released under the Apache License 2.0. You can use it in your own projects for 100% free.

---
A Open Source Project From 4paradigm.com
