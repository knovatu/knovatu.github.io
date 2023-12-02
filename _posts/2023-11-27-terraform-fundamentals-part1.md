---
title: Terraform Fundamentals (part. 1)
author: grucci
date: 2023-11-30 -0300
img_path: /assets/img/articles/terraform-fundamentals/
categories: [IaC, Terraform, Fundamentals]
tags: [iac, terraform, fundamentals]
---

## Terraform, what's this?

Terraform is an Infrastructure as Code (IaC) tool created by Hashicorp, which allow for the automated and consistent creation, management, and provisioning of cloud and on-premises infrastructure resources.

It is a declarative programming tool that utilizes a high-level language called HCL (Hashicorp Configuration Language) and can manage both low-level components (ex:. storage) and high-level components (ex:. SaaS).

## Key features of Terraform

* No need to install an application other than the Terraform binary.
* Terraform files have the .tf extension.
* Plugins are downloaded after Terraform initialization into the .terraform folder, based on the configurations.
* Stores all states of infrastructure provisioning, and any modifications are recorded when applying Terraform code.

## Composition of the Terraform Architecture

Terraform Core analyzes configurations and establishes dependencies between resources.

Terraform Providers act as intermediaries between Terraform Core and the corresponding APIs.

## Terraform Components

### *Backend*

The backend is a Terraform configuration that specifies where the state file will be stored.

There are various ways to store the state file, and the choice depends on the project's needs and requirements.

Local (default): The state is stored locally on the file system of the computer where Terraform is being executed. However, this is not recommended for production or collaborative environments as it may lead to synchronization and security issues.

Remote: The state can be stored remotely in a backend such as Amazon S3, Azure Storage, Google Cloud Storage, or others. This is highly recommended for production environments and collaborative teams as it offers benefits such as more granular access control, collaborative work capability, and increased security.

Example backend configuration:

```terraform
1 terraform {
2   backend "s3" {
3     bucket         = "s3-bucket-name"
4     key            = "path/to/terraform.tfstate"
5     region         = "region-aws"
6     encrypt        = true
7   }
8 }
```

### *State File*

The Terraform state refers to a file that tracks information about provisioned resources, their configurations, and dependencies between them. This state file is crucial for Terraform to understand the current state of the infrastructure and determine what changes are necessary to achieve the desired state.

The state file serves several purposes for Terraform:

Resource Tracking: The state file keeps a record of all resources provisioned by Terraform. It stores unique identifiers, configurations, and metadata associated with each resource.

Dependency Control: The state file records dependencies between resources. This is crucial to ensure that resources are created or modified in the correct order, avoiding dependency issues.

Concurrency and Locking: The state file is used to coordinate concurrent operations from multiple instances of Terraform. It provides a locking mechanism to ensure that only one instance of Terraform at a time can modify the state.

It is essential to manage the state properly to avoid conflicts and ensure the integrity of the infrastructure managed by Terraform.

Example of a state file:

![statefile-example](statefile.png)

### *Provider*

Terraform Providers are plugins used to interact and connect with a service or resource provider, such as cloud providers, storage providers, network providers, and others. They act as bridges between the Terraform Core and the API of the service or resource to be provisioned or managed. Each provider is responsible for translating instructions in the Terraform configuration into appropriate calls to the underlying provider's API.

Some Providers require configurations before using them (credentials, cloud region, endpoint URL, etc.).

![terraformcore-provider](terraformcore-api.png)

For example, if you are using Terraform to provision resources on Amazon Web Services (AWS), you will need the AWS provider. Similarly, if you are working with Microsoft Azure, you will need the Azure provider. Each provider has its own specific resources and parameters that can be configured in the Terraform configuration file.

```terraform
1  provider “aws” {
2    region = “us-east-1”
3  }
```

The modular structure of Terraform allows users to choose and incorporate specific providers as needed to meet the requirements of the infrastructure they are creating. This approach provides a wide range of flexibility and support for different environments and infrastructure services.

![provider](providers.png)
