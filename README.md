# terraform-random-separator
Create a random separator string in HashiCorp Terraform.

This configuration uses the `terraform_remote_state` datasource and native functions in Terraform to output a randomized string value name, of a length determined by a separate Terraform Cloud workspace configured to use https://github.com/vaficionado/terraform-random-integer as its source. 

To adjust the length of the integer, adjust the `min` and `max` values in https://github.com/vaficionado/terraform-random-integer/blob/master/main.tf

To adjust the separator configuration (length, character types, etc) adjust the `special`, `upper`, `lower`, and `number` values in `main.tf`

The function returns a single string output of `separator` and requires two workspace variables to be configured as follows:
* `organization` : the name of the Terraform Cloud organization where the workspaces are configured
* `length-workspace` : the name of the Terraform Cloud workspace where the `integer` output can be obtained (typically linked to https://github.com/vaficionado/terraform-random-integer)

Note that the string value in `outputs.tf` is customized using string interpolation to add `-` characters before and after the randomly generated string. This can be changed by removing the interpolation syntax around `random_string.separator.result`

For more information on how to link this configuration to a Terraform Cloud workspace, see this blog post:
https://www.hashicorp.com/blog/using-terraform-cloud-and-version-control-systems/

