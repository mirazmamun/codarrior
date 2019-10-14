---
title: Terraform - Running Local script to Complement Functionality
tags:
  - Terraform
  - IaC
  - AWS
date: 2019-10-14 12:47:03
---


Here in [SEEK AI](https://www.seek.com.au/about/), to manage Infrastructure as Code (IaC), we
use [Terraform](https://www.terraform.io) (aka TF) a lot. I have been a avid user of AWS CloudFormation for a while
but recently converted to TF. Here are some reasons:

- The CLI toolkit `terraform` is more versatile in its domain. It comes with everything for
managing Infrastructure like planning, destroying, state management, tainting resource for destruction. Whereas `aws cli`
is a mixed bag of all commands.
- Managing version and applying delta is so easy due to efficient resource graph
management by TF
- Creating and reusing modular resource configuration is easy with TF. For `aws cli` it is done
via creating separate CloudFormation stack and using output of those stack which act as independent entities.
But for TF, it is all under the same graph. So, for CloudFormation, you can accidentally delete a stack, crippling
the functionality of the stack, which is unlikely in TF

But, TF is not perfect like humans. Some lacking I have felt is emanating from limiter number of `providers`. Although you
can create custom `providers`, still for small functionality it seems to be a hassle to maintain and publish them in repo, such an overfill
of effort when you can do without it.

But there are ways to give your workflow a boost with `provisioner`. A `provisioner` allows you to
execute scripts at some `resource` life-cycle like resource _creation_ or _destroy_. This is handy as you can:

- Use your own script with any runtime available on the host running _Terraform_, like `python, nodejs, php` and so forth.
So it definitely frees you from Terraform's DSL which is HCL.
- Complement the functionality available from out-of-the-box functions and interpolation and `providers`
- It is fun to extend custom capabilities with less effort

Let's consider a use case:

> We need to create a custom title for an IAM Policy Document that will have the IP address
> as a part of the title and in Condition statement

So basically we need to retrieve the public IP address of the host running TF and put it in
a file. We then can make use of `file` intrinsic function or `local` provider's `data source` to
read content of the file and make use of it.

```
#!/bin/bash

ip=$(curl -s https://api.ipify.org)
echo "My public IP address is: $ip"
```
