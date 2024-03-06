### Three common cloud service types
1. [[Service Types#Infrastructure as a Service | Infrastructure as a Service (IaaS)]]
2. [[Service Types#Platform as a Service | Platform as a Service (PaaS)]]
3. Software as a Service (SaaS)

### Infrastructure as a Service
##### Overview
Infrastructure as a Service (IaaS) provides the most flexibility to you. The cloud provider is responsible for maintaining server hardware, network connectivity, and physical security, but the rest is configurable by you. This includes installing and configuring appropriate operating systems on the cloud-provided hardware, as well as maintaining them; network configuration; storage/database configuration. IaaS in some sense is just renting hardware and figuring out what to do with it.

##### When does IaaS make sense?
- If you manage all of your own servers on your own premises, and want to moves things over to the cloud to no longer mange hardware upgrades, networking, and physical security. Sometimes offloading just a bit of responsibility to a cloud provider can make sense. With IaaS you can do this, but still garner a good degree of flexibility and control.
- Rapidly replicating established configurations in the cloud can be helpful. You can push development or test environments up to the cloud in a representative state, and then shut them down quickly if they are no longer needed.



### Platform as a Service
##### Overview
Platform as a Service (PaaS) fits right between renting hardware with [[Service Types#Infrastructure as a Service|IaaS]], and paying for a complete software solution with [[Service Types#Software as a Service|SaaS]]. With PaaS, the cloud provider still maintains physical infrastructure, physical security, and connection to the internet, and now they maintain operating systems, middleware, development tools, and business intelligence. Here you don't need to worry about database and operating system patching, nor licensing. This gives a complete development environment without the overhead of maintaining infrastructure.

###### When does PaaS make sense?
- If you want to reduce the amount of developer time focused on scaling cloud systems, and keeping them highly available PaaS might start to make sense, if you are alright relinquishing some control to the cloud provider.
- If you want to mine business data and perform analytics, PaaS provides integrated tooling to find insights and patterns and predict outcomes, which can help inform business decisions.

### Software as a Service
##### Overview
Software as a Service (SaaS) is the most complete cloud service from a product perspective. Rather than renting hardware, this is renting a developed application. Any messaging applications, or email clients are SaaS implementations. These are quick to start, require the least amount of technical knowledge, but are the least flexible of service types.

##### When does SaaS make sense?
- If your company needs some messaging tools to coordinate teams, grabbing an established messaging tool makes a lot of sense. Why reinvent the wheel if generally messaging tools are congruent?
- Financial tracking also looks pretty similar across businesses, and so something off the shelf might be perfect for your business for this case.

### Who is Responsible for What?
If something has a checkmark, ❌, the cloud provider has you covered and is responsible. Wherever ✔️and ❌ both appear, there is shared responsibility.
You will always be responsible for information and data, devices, and accounts and identities. When you run and manage your own hardware on-premises, you are responsible for everything.

| Responsibility | SaaS | PaaS | IaaS | On-prem |
| --------------- | ----- | ------ | ---- | -------------- |
| Information and data | ❌ | ❌ | ❌ | ❌ |
| Devices (Mobile and PCs) | ❌ | ❌ | ❌ | ❌ |
| Account and identities | ❌ | ❌ | ❌ | ❌ |
| Identity and directory infrastructure | ✔️❌ | ✔️❌ | ❌ | ❌ |
| Applications | ✔️ | ✔️❌ | ❌ | ❌ |
| Network controls | ✔️ | ✔️❌ | ❌ | ❌ |
| Operating system | ✔️ | ✔️ | ❌ | ❌
| Physical hosts | ✔️ | ✔️ | ✔️ | ❌ |
| Physical network | ✔️ | ✔️ | ✔️ | ❌ |
| Physical datacenter | ✔️ | ✔️ | ✔️ | ❌ |