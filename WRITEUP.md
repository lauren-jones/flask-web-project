# Write-up Template

### Analyze, choose, and justify the appropriate resource option for deploying the app.

_For **both** a VM or App Service solution for the CMS app:_

- _Analyze costs, scalability, availability, and workflow_
- _Choose the appropriate solution (VM or App Service) for deploying the app_
- _Justify your choice_

### Cost analysis

App Service:

The cost of the App Service depends on the pricing tier you opt for. Free and shared plans are ideal for testing your applications in Azure, and Basic, standard and premium plans are intended for production workloads and run on dedicated VM instances.

The App Service is typically priced on a Pay-As-You-Go (PAYG) model, although there are options to save money with savings plans and reservations.

Here is a comparison of the different PAYG hourly prices in the different tiers:

|                   | Free | Shared | Basic  | Standard | Premium |
| ----------------- | ---- | ------ | ------ | -------- | ------- |
| PAYG hourly price | Free | $0.013 | $0.075 | $0.10    | $0.20   |

The pricing tier you choose determines your available usage, such as how many apps you can run, the disk space you have, auto-scaling capabilities and much more.

VMs:

VMs also have PAYG pricing, with the option of savings plans and reservations. The cost of a VM depends on factors such as its performance capabilities and location.

Comparison:

It can be difficult to compare exactly the same resources between the App Service and VMs, as the offering varies between the products and their tiers. However, to give an indication of cost comparison, here is an example of the relative cost of two similar resources on a VM solution versus App Service solution. The cost is for 1 month and uses estimates from Microsoft:

- VM with Windows OS, B1 instance (1 core, 1 GB RAM, 4 GB Storage) located in East US - available on STANDARD pricing tier - $10.22
- App Service with Windows OS, B1 instance (1 core, 1.75 GB RAM, 10 GB Storage) located in East US - this is available on BASIC pricing tier - $54.75

The App Service can therefore be more expensive than VMs - it entirely depends on your requirements.

### Scalability analysis

App Service:

You can scale the App Service either up or out, manually or automatically. To scale automatically, the App Service allows you to set predefined rules and schedules based on demand (available in standard pricing tier and above).

By scaling up, you get more CPU, memory and disk space, along with extra features like dedicated virtual machines. You scale up by changing the pricing tier of the App Service plan that your app belongs to.

You can scale out by increasing the number of VM instances that run your app. You can scale out to as many as 30 instances, depending on your pricing tier. The App Service provides an integrated load balancer and can easily increase instances.

It is important to note that the App Service has inherent hardware limitations that impact scalability.

VMs:

Like the App Service, a VM solution has the ability to scale either vertically (increasing compute power of VM) or horizontally (increasing number of VM instances).

Virtual machine scale sets provide an automated and flexible way to manage your application's horizontal scalability. They allow you to create and manage a group of load balanced VM's. The number of VM instances can automatically increase or decrease in response to demand or a defined schedule.

In practice, you can create as many Azure VMs as you need, therefore hardware limitations are not a concern for scalability with VMs.

### Availability analysis

Microsoft guarantees that the App Service will be available 99.95% of the time, but only when your application is running on either a single or multiple instances. There is no SLA guarantee for either the Free or Shared pricing tiers. You can host your apps anywhere in Microsoft's global datacenter infrastructure.

If you only have one VM then your service will not be highly available, but you have the ability to implement high availability using virtual machine scale sets. VM scale sets allow your application to be distributed across availability or fault zones.

### Workflow analysis

The App Service makes it easy to implement a CI/CD workflow, by integrating with source code repositories such as GitHub and Azure Repos.

On a VM, you have the freedom to implement any workflow, as you have control over the tooling installed on the VM. However, there is going to be more effort required to get your workflow up and running.

### Chosen solution:

Given that the CMS app is a lightweight application with no high performance compute needs, I propose using the App Service. The cost for the App Service varies depending on the pricing tier, however we should be able to use a low tier to reduce cost. The App Service is likely to be more cost effective than a comprehensive VM solution. The CMS app is unlikely to exceed the hardware limitations of the App Service, based on current expected usage. The App Service supports Python, and is therefore compatible with our app. There is no requirement for us to have full control of the operating system or custom software, which would require a VM solution.

### Assess app changes that would change your decision.

_Detail how the app and any other needs would have to change for you to change your decision in the last section._

If the CMS app was expected to scale beyond the hardware limitations of the App Service, we would need to review our solution. Also, if we introduced a requirement for custom software or tooling to our app, this would likely require us to change to a VM solution.
