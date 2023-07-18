# Write-up Template

### Analyze, choose, and justify the appropriate resource option for deploying the app.

_For **both** a VM or App Service solution for the CMS app:_

- _Analyze costs, scalability, availability, and workflow_
- _Choose the appropriate solution (VM or App Service) for deploying the app_
- _Justify your choice_

### VM solution:

A VM solution is likely to be more costly than the App Service. You have the freedom to scale your compute resources either vertically or horizontally, either by adding more VM's or by increasing compute power. If you only have one VM then your service will not be highly available, but you have the ability to implement high availability using virtual machine scale sets. You have the freedom to implement any workflow on a VM, as you have control over the tooling installed on the VM.

### App Service solution:

An App Service solution is likely to be more cost effective than a scalable, highly available VM solution. You can scale the App Service vertically by changing the pricing tier, and horizontally by increasing/decreasing the number of VM instances the App Service is running. You will always be paying for your pricing plan, even if your application is not running. It is important to note that the App Service has some hardware limitations, such as a maximum of 14GB memory. The App Service makes it very easy to implement a CI/CD workflow, by integrating with source code repositories such as GitHub and Azure Repos.

### Chosen solution:

Given that the CMS app is a lightweight application with no high performance compute needs, I propose using the App Service. The cost for the App Service varies depending on the pricing tier, however we should be able to use a low tier to reduce cost. The App Service is likely to be more cost effective than a comprehensive VM solution. The CMS app is unlikely to exceed the hardware limitations of the App Service, based on current expected usage. The App Service supports Python, and is therefore compatible with our app. There is no requirement for us to have full control of the operating system or custom software, which would require a VM solution.

### Assess app changes that would change your decision.

_Detail how the app and any other needs would have to change for you to change your decision in the last section._

If the CMS app was expected to scale beyond the hardware limitations of the App Service, we would need to review our solution. Also, if we introduced a requirement for custom software or tooling to our app, this would likely require us to change to a VM solution.
