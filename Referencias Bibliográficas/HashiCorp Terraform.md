202207151943
Estado: #idea 
Tags: #cloud #terraform

# HashiCorp Terraform
Author: Educative.io
Year: 2022

---
## Referencias

Infrastructure is the collection of resources an application runs on. Traditionally, this was composed of servers, storage, and networking. With the advent of virtualization, servers are now split into both physical resources and virtual machines. Cloud providers create additional abstractions, starting with Infrastructure as a Service (IaaS) and moving up to Platform as a Service (PaaS) and Software as a Service (SaaS). Traditional infrastructure was deployed using manual and cumbersome processes that made mistakes and inconsistencies rather common. The various services offered by cloud providers and other vendors now introduce a software-driven model of creation and configuration.

[What is Infrastructure as Code?](https://www.educative.io/courses/hashicorp-terraform-certified-associate-preparation-guide/JYLQQO46nnJ)


IaC is the practice of defining and provisioning infrastructure resources through a machine-readable format. The infrastructure provisioned and managed using IaC can include bare-metal servers, virtual machines, networking resources, storage volumes, or even databases provided as a service


The code created for IaC may be stored in a **version control system** **(VCS)** to enable change-tracking and team collaboration. IaC can also be combined with other common software development practices like automated testing, deployment pipelines, and reusable components

**HashiCorp Configuration Language (HCL)** is the low-level syntax of Terraform language


A block has a type (`resource` in this example). Each block type defines how many labels must follow the type keyword. The `resource` block type expects two labels, `aws_instance` and `example` in the example above. A particular block type may have any number of required labels, or it may require none, as with the nested `network_interface` block type.

Argument names, block type names, and the names of most Terraform-specific constructs like resources or input variables are all **identifiers**.

Identifiers can contain letters, digits, underscores (`_`), and hyphens (`-`). To avoid ambiguity with literal numbers, the first character of an identifier mustn’t be a digit.


By defining infrastructure as code, the deployment of that infrastructure should be consistent across multiple builds and environments

By defining the web server deployment in code, it can be reused by each new deployment that requires a set of web servers.

The provisioning process of infrastructure can be incorporated into the existing application development workflow, creating a consistent and repeatable process that flows through development, QA, staging, and production environments.


Terraform has a multi-cloud and provider-agnostic approach that makes it ideal for use across multiple clouds and services.

[Multi-cloud and Provider-agnostic - HashiCorp Terraform Certified Associate Preparation Guide (educative.io)](https://www.educative.io/courses/hashicorp-terraform-certified-associate-preparation-guide/g24G2oMY9qk)


The creation and manipulation of resources managed by Terraform need to be tracked in some manner. Terraform achieves this through the implementation of **state**. When a resource is created, such as an EC2 instance in AWS, Terraform creates an entry in the state that maps the metadata about the resource (such as `instance-id`) to key/value pairs in the entry. The tracking of resource metadata serves multiple functions.

Terraform won’t make any changes to the environment if there aren’t any made to the configuration. The state is what allows Terraform to map the resources defined in the configuration to the resources that exist in the real world.

Terraform maintains a list of dependencies in the state file so that it can properly deal with dependencies that no longer exist in the current configuration.

It’s important to note that choosing not to refresh the state means that the reality of our infrastructure deployment may not match what’s in the state file. This can lead to inconsistent results or outright failure when we apply the plan. The risk of not refreshing the state should be balanced against any performance improvements.



Terraform is written in the **Go programming language (Golang)** and provided as a single binary that includes core components required to parse and deploy Terraform configurations. It doesn’t include the code necessary to interact with various providers and provisioners. That code is supplied via plugins. Each plugin is executed as a separate process communicating with the core Terraform binary using an RPC interface.

We can proceed in two different ways:

-   We can use multiple different providers in a configuration.
-   We can use multiple instances of the same provider.

[Plugin-based Architecture - HashiCorp Terraform Certified Associate Preparation Guide (educative.io)](https://www.educative.io/courses/hashicorp-terraform-certified-associate-preparation-guide/N8yzpOmDrnm)


With the introduction of version 0.13, providers can be automatically downloaded from a public or private repository. The official public repository for Terraform is located at [registry.terraform.io](http://registry.terraform.io/), which includes three types of providers


Providers can be added through a `required_providers` nested block inside the `terraform` code block. An example is shown below:


`hostname/organization/provider`. If the hostname is omitted, Terraform assumes we’re using the public Terraform registry, [registry.terraform.io](http://registry.terraform.io/).

By default, each configuration will download its own copy of the provider plugins. In order to reduce download times and improve performance, plugin caching can be enabled, either through the `plugin_cache_dir` setting in the Terraform CLI configuration file or by using the `TF_PLUGIN_CACHE_DIR` environment variable.


There may be scenarios where we don’t want Terraform to download plugins, such as in a disconnected or highly regulated environment.


. The location of pre-downloaded plugins can be configured by setting the environment variable `TF_PLUGIN_DIR` or by using the `--plugin-dir` argument during initialization.


[How Terraform Finds and Fetches Providers - HashiCorp Terraform Certified Associate Preparation Guide (educative.io)](https://www.educative.io/courses/hashicorp-terraform-certified-associate-preparation-guide/mE5r5x7v0KG)


When a resource is created, we may have some scripts or operations we’d like to perform locally or on the remote resource. Terraform **provisioners** are used to accomplish this goal.

There are three basic provisioner use cases:

-   Loading data into a virtual machine.
-   Bootstrapping a virtual machine for a config manager.
-   Saving data locally on the system.

We may wish to run a script locally as part of our Terraform configuration by using the `local-exec` provision

When a creation-time provisioner fails, it sets the resource as tainted because it has no way of knowing how to remediate the issue outside of deleting the resource and trying again. This behavior can be altered using the `on_failure` argument. When a destroy-time provisioner fails, Terraform doesn’t destroy the resource and tries to run the provisioner again during the next execution of `terraform apply`


When a creation-time provisioner fails, it sets the resource as tainted because it has no way of knowing how to remediate the issue outside of deleting the resource and trying again. This behavior can be altered using the `on_failure` argumen


[Using Provisioners, local-exec, or remote-exec - HashiCorp Terraform Certified Associate Preparation Guide (educative.io)](https://www.educative.io/courses/hashicorp-terraform-certified-associate-preparation-guide/7AqGBYwZjMw)


As is common in many command-line interfaces (CLIs), Terraform has a help system. When we first start with Terraform, we learn the primary commands of `init`, `plan`, `apply`, and `destroy`.




The `provider` block configures the specified provider, in this case `aws`. A provider is a plugin that Terraform uses to create and manage your resources.

You can use multiple provider blocks in your Terraform configuration to manage resources from different providers. You can even use different providers together. For example, you could pass the IP address of your AWS EC2 instance to a monitoring resource from DataDog.


Use `resource` blocks to define components of your infrastructure. A resource might be a physical or virtual component such as an EC2 instance, or it can be a logical resource such as a Heroku application.

Resource blocks have two strings before the block: the resource type and the resource name. In this example, the resource type is `aws_instance` and the name is `app_server`. The prefix of the type maps to the name of the provider. In the example configuration, Terraform manages the `aws_instance` resource with the `aws` provider. Together, the resource type and resource name form a unique ID for the resource. For example, the ID for your EC2 instance is `aws_instance.app_server`.

Terraform downloads the `aws` provider and installs it in a hidden subdirectory of your current working directory, named `.terraform`. The `terraform init` command prints out which version of the provider was installed. Terraform also creates a lock file named `.terraform.lock.hcl` which specifies the exact provider versions used, so that you can control when you want to update the providers used for your project.

We recommend using consistent formatting in all of your configuration files. The `terraform fmt` command automatically updates configurations in the current directory for readability and consistency.

Apply the configuration now with the `terraform apply` command. Terraform will print output similar to what is shown below. We have truncated some of the output to save space.

es, Terraform prints out the _execution plan_ which describes the actions Terraform will take in order to change your infrastructure to match the configuration.


For example, AWS assigns Amazon Resource Names (ARNs) to instances upon creation, so Terraform cannot know the value of the `arn` attribute until you apply the change and the AWS provider returns that value from the AWS API.


When you applied your configuration, Terraform wrote data into a file called `terraform.tfstate`. Terraform stores the IDs and properties of the resources it manages in this file, so that it can update or destroy those resources going forward.

Terraform has a built-in command called `terraform state` for advanced state management. Use the `list` subcommand to list of the resources in your project's state.


Terraform builds an execution plan that only modifies what is necessary to reach your desired state.

