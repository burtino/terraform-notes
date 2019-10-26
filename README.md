# terraform-notes

[Terraform](https://www.terraform.io) is a tool to manage infrasrtucture as code from [Hashicorp](https://www.hashicorp.com/).

## Installation and Version Management

### tfenv
[tfenv](https://github.com/tfutils/tfenv) is a terraform version manager inspired by [rbenv](https://github.com/rbenv/rbenv). It makes it easy to operate on different terraform projects and modules of different version compatibility.

### terragrunt
[terragrunt](https://github.com/gruntwork-io/terragrunt) is a thin wrapper for terraform that provides extra tools for working with multiple Terraform modules. [terragrunt](https://github.com/gruntwork-io/terragrunt) comes from by Yevgeniy Brikman and team at [gruntwork](https://gruntwork.io/). He wrote [Terraform up and Running](http://shop.oreilly.com/product/0636920225010.do). 
Gruntwork also created [terratest](https://github.com/gruntwork-io/terratest). With terratest you can write automated tests against your infrastructure code.

### tgenv
[tgenv](https://github.com/cunymatthieu/tgenv) [terragrunt](https://github.com/gruntwork-io/terragrunt) version manager inspried by and using code from tfenv.

## CI Tools

### Atlantis

[Atlantis](https://www.runatlantis.io/) provides Terraform Pull Request Automation. They maintain an [official container](https://hub.docker.com/r/runatlantis/atlantis) on dockerhub. 

### Custom CI Workflow Example

An example of an automated CI workflow for contributing code to a terraform inventory.

1. Open a Pull Request
1. Automatically run:
   1. `terraform plan`
   1. [tflint](https://github.com/wata727/tflint)
   1. [terratest](https://github.com/gruntwork-io/terratest)
1. Comment the results of checks back to the pull request. 
1. Team member reviews and approves.
1. A `terraform apply` occurs and the output is commented on the pull request. 
1. Merge Pull Request (assuming successful apply)

If you were creating a workflow for developing a terraform module in a non production environment, you could modify this workflow to both create and then destory the resources. 

Terraform testing creates real resources on a cloud provider. It is common for terraform non-production environments to be on-demand and destoryed after the test is completed to save money. 

Terraform commands are limiated to the speed of the provider's API. Resources of different types are created at different speeds. For example an AWS Cloudfront distribution takes ~30-35 minutes to create. An AWS S3 bucket only seconds.




