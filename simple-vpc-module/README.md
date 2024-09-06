<!-- BEGIN_TF_DOCS -->

## Requirements
The following requirements are needed by this module:

- [terraform] ~> 1.9.0
- [aws provider plugin] >= 5.60.0

## Inputs

The below inputs need to be passed. If we dont pass the inputs, the default values listed below will be taken

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| region | AWS region in which the VPC should be creted | string | ap-south-1 | yes |
| environment | Specify the environment name. Accepted values are production/staging | string | production | yes |
| vpc_cidr | The IPv4 CIDR block for the VPC | string | 10.0.0.0/16 | yes |
| vpc_name | Name for the VPC | string | production-vpc | yes |
| availability_zones | List of availability zones | list(string) | ["ap-south-1a", "ap-south-1b"] | yes |
| public_subnet_cidrs | CIDR blocks for public subnets | list(string) | ["10.0.2.0/24", "10.0.4.0/24"] | yes |
| private_subnet_cidrs | CIDR blocks for private subnets | list(string) | ["10.0.1.0/24", "10.0.3.0/24"] | yes |


## Resources
The below aws resources will be created

| Name |
|------|
| VPC |
| Internet gateway |
| Elastic IPs for NAT gateways |
| NAT gateways |
| Public Subnets |
| Private Subnets |
| Routes |
| Route tables |
| Route table associations |



## Requirements

The following requirements are needed by this module:

- <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) (~> 1.5.0)

- <a name="requirement_aws"></a> [aws](#requirement\_aws) (>= 5.0.0)

## Providers

The following providers are used by this module:

- <a name="provider_aws"></a> [aws](#provider\_aws) (>= 5.0.0)

## Modules

No modules.

## Resources

The following resources are used by this module:

- [aws_internet_gateway.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/internet_gateway) (resource)
- [aws_route_table.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route_table) (resource)
- [aws_route_table_association.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route_table_association) (resource)
- [aws_subnet.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/subnet) (resource)
- [aws_vpc.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc) (resource)

## Required Inputs

No required inputs.

## Optional Inputs

The following input variables are optional (have default values):

### <a name="input_igw_parameters"></a> [igw\_parameters](#input\_igw\_parameters)

Description: IGW parameters

Type:

```hcl
map(object({
    vpc_name = string
    tags     = optional(map(string), {})
  }))
```

Default: `{}`

### <a name="input_rt_association_parameters"></a> [rt\_association\_parameters](#input\_rt\_association\_parameters)

Description: RT association parameters

Type:

```hcl
map(object({
    subnet_name = string
    rt_name     = string
  }))
```

Default: `{}`

### <a name="input_rt_parameters"></a> [rt\_parameters](#input\_rt\_parameters)

Description: RT parameters

Type:

```hcl
map(object({
    vpc_name = string
    tags     = optional(map(string), {})
    routes = optional(list(object({
      cidr_block = string
      use_igw    = optional(bool, true)
      gateway_id = string
    })), [])
  }))
```

Default: `{}`

### <a name="input_subnet_parameters"></a> [subnet\_parameters](#input\_subnet\_parameters)

Description: Subnet parameters

Type:

```hcl
map(object({
    cidr_block = string
    vpc_name   = string
    tags       = optional(map(string), {})
  }))
```

Default: `{}`

### <a name="input_vpc_parameters"></a> [vpc\_parameters](#input\_vpc\_parameters)

Description: VPC parameters

Type:

```hcl
map(object({
    cidr_block           = string
    enable_dns_support   = optional(bool, true)
    enable_dns_hostnames = optional(bool, true)
    tags                 = optional(map(string), {})
  }))
```

Default: `{}`

## Outputs

The following outputs are exported:

### <a name="output_vpcs"></a> [vpcs](#output\_vpcs)

Description: VPC Outputs
<!-- END_TF_DOCS -->
