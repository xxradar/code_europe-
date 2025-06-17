```
(base) xxradar@Philippes-MacBook-Pro devopsfuture % chmod +x configure-kubeconfig.sh
(base) xxradar@Philippes-MacBook-Pro devopsfuture % terraform init

Initializing the backend...
Initializing modules...
Downloading registry.terraform.io/terraform-aws-modules/vpc/aws 4.0.2 for vpc...
- vpc in .terraform/modules/vpc

Initializing provider plugins...
- Finding hashicorp/aws versions matching ">= 4.35.0, >= 5.0.0"...
- Installing hashicorp/aws v5.100.0...
- Installed hashicorp/aws v5.100.0 (signed by HashiCorp)

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
(base) xxradar@Philippes-MacBook-Pro devopsfuture % terraform apply

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # aws_eks_cluster.this will be created
  + resource "aws_eks_cluster" "this" {
      + arn                           = (known after apply)
      + bootstrap_self_managed_addons = true
      + certificate_authority         = (known after apply)
      + cluster_id                    = (known after apply)
      + created_at                    = (known after apply)
      + endpoint                      = (known after apply)
      + id                            = (known after apply)
      + identity                      = (known after apply)
      + name                          = "devops-future-eks"
      + platform_version              = (known after apply)
      + role_arn                      = (known after apply)
      + status                        = (known after apply)
      + tags                          = {
          + "Environment" = "devops-future"
          + "Terraform"   = "true"
        }
      + tags_all                      = {
          + "Environment" = "devops-future"
          + "Terraform"   = "true"
        }
      + version                       = "1.27"

      + vpc_config {
          + cluster_security_group_id = (known after apply)
          + endpoint_private_access   = true
          + endpoint_public_access    = true
          + public_access_cidrs       = [
              + "0.0.0.0/0",
            ]
          + subnet_ids                = (known after apply)
          + vpc_id                    = (known after apply)
        }
    }

  # aws_eks_node_group.this will be created
  + resource "aws_eks_node_group" "this" {
      + ami_type               = (known after apply)
      + arn                    = (known after apply)
      + capacity_type          = (known after apply)
      + cluster_name           = "devops-future-eks"
      + disk_size              = 20
      + id                     = (known after apply)
      + instance_types         = [
          + "t3.medium",
        ]
      + node_group_name        = "devops-future-node-group"
      + node_group_name_prefix = (known after apply)
      + node_role_arn          = (known after apply)
      + release_version        = (known after apply)
      + resources              = (known after apply)
      + status                 = (known after apply)
      + subnet_ids             = (known after apply)
      + tags                   = {
          + "Environment" = "devops-future"
          + "Terraform"   = "true"
        }
      + tags_all               = {
          + "Environment" = "devops-future"
          + "Terraform"   = "true"
        }
      + version                = (known after apply)

      + scaling_config {
          + desired_size = 3
          + max_size     = 3
          + min_size     = 1
        }
    }

  # aws_iam_role.eks_cluster_role will be created
  + resource "aws_iam_role" "eks_cluster_role" {
      + arn                   = (known after apply)
      + assume_role_policy    = jsonencode(
            {
              + Statement = [
                  + {
                      + Action    = "sts:AssumeRole"
                      + Effect    = "Allow"
                      + Principal = {
                          + Service = "eks.amazonaws.com"
                        }
                    },
                ]
              + Version   = "2012-10-17"
            }
        )
      + create_date           = (known after apply)
      + force_detach_policies = false
      + id                    = (known after apply)
      + managed_policy_arns   = (known after apply)
      + max_session_duration  = 3600
      + name                  = "devops-future-eks-cluster-role"
      + name_prefix           = (known after apply)
      + path                  = "/"
      + tags                  = {
          + "Environment" = "devops-future"
          + "Terraform"   = "true"
        }
      + tags_all              = {
          + "Environment" = "devops-future"
          + "Terraform"   = "true"
        }
      + unique_id             = (known after apply)
    }

  # aws_iam_role.eks_node_role will be created
  + resource "aws_iam_role" "eks_node_role" {
      + arn                   = (known after apply)
      + assume_role_policy    = jsonencode(
            {
              + Statement = [
                  + {
                      + Action    = "sts:AssumeRole"
                      + Effect    = "Allow"
                      + Principal = {
                          + Service = "ec2.amazonaws.com"
                        }
                    },
                ]
              + Version   = "2012-10-17"
            }
        )
      + create_date           = (known after apply)
      + force_detach_policies = false
      + id                    = (known after apply)
      + managed_policy_arns   = (known after apply)
      + max_session_duration  = 3600
      + name                  = "devops-future-eks-node-role"
      + name_prefix           = (known after apply)
      + path                  = "/"
      + tags                  = {
          + "Environment" = "devops-future"
          + "Terraform"   = "true"
        }
      + tags_all              = {
          + "Environment" = "devops-future"
          + "Terraform"   = "true"
        }
      + unique_id             = (known after apply)
    }

  # aws_iam_role_policy_attachment.eks_cluster_policy will be created
  + resource "aws_iam_role_policy_attachment" "eks_cluster_policy" {
      + id         = (known after apply)
      + policy_arn = "arn:aws:iam::aws:policy/AmazonEKSClusterPolicy"
      + role       = "devops-future-eks-cluster-role"
    }

  # aws_iam_role_policy_attachment.eks_cni_policy will be created
  + resource "aws_iam_role_policy_attachment" "eks_cni_policy" {
      + id         = (known after apply)
      + policy_arn = "arn:aws:iam::aws:policy/AmazonEKS_CNI_Policy"
      + role       = "devops-future-eks-node-role"
    }

  # aws_iam_role_policy_attachment.eks_registry_policy will be created
  + resource "aws_iam_role_policy_attachment" "eks_registry_policy" {
      + id         = (known after apply)
      + policy_arn = "arn:aws:iam::aws:policy/AmazonEC2ContainerRegistryReadOnly"
      + role       = "devops-future-eks-node-role"
    }

  # aws_iam_role_policy_attachment.eks_worker_node_policy will be created
  + resource "aws_iam_role_policy_attachment" "eks_worker_node_policy" {
      + id         = (known after apply)
      + policy_arn = "arn:aws:iam::aws:policy/AmazonEKSWorkerNodePolicy"
      + role       = "devops-future-eks-node-role"
    }

  # module.vpc.aws_default_network_acl.this[0] will be created
  + resource "aws_default_network_acl" "this" {
      + arn                    = (known after apply)
      + default_network_acl_id = (known after apply)
      + id                     = (known after apply)
      + owner_id               = (known after apply)
      + tags                   = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-default"
          + "Terraform"   = "true"
        }
      + tags_all               = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-default"
          + "Terraform"   = "true"
        }
      + vpc_id                 = (known after apply)

      + egress {
          + action          = "allow"
          + from_port       = 0
          + ipv6_cidr_block = "::/0"
          + protocol        = "-1"
          + rule_no         = 101
          + to_port         = 0
        }
      + egress {
          + action     = "allow"
          + cidr_block = "0.0.0.0/0"
          + from_port  = 0
          + protocol   = "-1"
          + rule_no    = 100
          + to_port    = 0
        }

      + ingress {
          + action          = "allow"
          + from_port       = 0
          + ipv6_cidr_block = "::/0"
          + protocol        = "-1"
          + rule_no         = 101
          + to_port         = 0
        }
      + ingress {
          + action     = "allow"
          + cidr_block = "0.0.0.0/0"
          + from_port  = 0
          + protocol   = "-1"
          + rule_no    = 100
          + to_port    = 0
        }
    }

  # module.vpc.aws_default_route_table.default[0] will be created
  + resource "aws_default_route_table" "default" {
      + arn                    = (known after apply)
      + default_route_table_id = (known after apply)
      + id                     = (known after apply)
      + owner_id               = (known after apply)
      + route                  = (known after apply)
      + tags                   = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-default"
          + "Terraform"   = "true"
        }
      + tags_all               = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-default"
          + "Terraform"   = "true"
        }
      + vpc_id                 = (known after apply)

      + timeouts {
          + create = "5m"
          + update = "5m"
        }
    }

  # module.vpc.aws_default_security_group.this[0] will be created
  + resource "aws_default_security_group" "this" {
      + arn                    = (known after apply)
      + description            = (known after apply)
      + egress                 = (known after apply)
      + id                     = (known after apply)
      + ingress                = (known after apply)
      + name                   = (known after apply)
      + name_prefix            = (known after apply)
      + owner_id               = (known after apply)
      + revoke_rules_on_delete = false
      + tags                   = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-default"
          + "Terraform"   = "true"
        }
      + tags_all               = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-default"
          + "Terraform"   = "true"
        }
      + vpc_id                 = (known after apply)
    }

  # module.vpc.aws_eip.nat[0] will be created
  + resource "aws_eip" "nat" {
      + allocation_id        = (known after apply)
      + arn                  = (known after apply)
      + association_id       = (known after apply)
      + carrier_ip           = (known after apply)
      + customer_owned_ip    = (known after apply)
      + domain               = (known after apply)
      + id                   = (known after apply)
      + instance             = (known after apply)
      + ipam_pool_id         = (known after apply)
      + network_border_group = (known after apply)
      + network_interface    = (known after apply)
      + private_dns          = (known after apply)
      + private_ip           = (known after apply)
      + ptr_record           = (known after apply)
      + public_dns           = (known after apply)
      + public_ip            = (known after apply)
      + public_ipv4_pool     = (known after apply)
      + tags                 = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-us-west-2a"
          + "Terraform"   = "true"
        }
      + tags_all             = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-us-west-2a"
          + "Terraform"   = "true"
        }
      + vpc                  = true
    }

  # module.vpc.aws_internet_gateway.this[0] will be created
  + resource "aws_internet_gateway" "this" {
      + arn      = (known after apply)
      + id       = (known after apply)
      + owner_id = (known after apply)
      + tags     = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc"
          + "Terraform"   = "true"
        }
      + tags_all = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc"
          + "Terraform"   = "true"
        }
      + vpc_id   = (known after apply)
    }

  # module.vpc.aws_nat_gateway.this[0] will be created
  + resource "aws_nat_gateway" "this" {
      + allocation_id                      = (known after apply)
      + association_id                     = (known after apply)
      + connectivity_type                  = "public"
      + id                                 = (known after apply)
      + network_interface_id               = (known after apply)
      + private_ip                         = (known after apply)
      + public_ip                          = (known after apply)
      + secondary_private_ip_address_count = (known after apply)
      + secondary_private_ip_addresses     = (known after apply)
      + subnet_id                          = (known after apply)
      + tags                               = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-us-west-2a"
          + "Terraform"   = "true"
        }
      + tags_all                           = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-us-west-2a"
          + "Terraform"   = "true"
        }
    }

  # module.vpc.aws_route.private_nat_gateway[0] will be created
  + resource "aws_route" "private_nat_gateway" {
      + destination_cidr_block = "0.0.0.0/0"
      + id                     = (known after apply)
      + instance_id            = (known after apply)
      + instance_owner_id      = (known after apply)
      + nat_gateway_id         = (known after apply)
      + network_interface_id   = (known after apply)
      + origin                 = (known after apply)
      + route_table_id         = (known after apply)
      + state                  = (known after apply)

      + timeouts {
          + create = "5m"
        }
    }

  # module.vpc.aws_route.public_internet_gateway[0] will be created
  + resource "aws_route" "public_internet_gateway" {
      + destination_cidr_block = "0.0.0.0/0"
      + gateway_id             = (known after apply)
      + id                     = (known after apply)
      + instance_id            = (known after apply)
      + instance_owner_id      = (known after apply)
      + network_interface_id   = (known after apply)
      + origin                 = (known after apply)
      + route_table_id         = (known after apply)
      + state                  = (known after apply)

      + timeouts {
          + create = "5m"
        }
    }

  # module.vpc.aws_route_table.private[0] will be created
  + resource "aws_route_table" "private" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = (known after apply)
      + tags             = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-private"
          + "Terraform"   = "true"
        }
      + tags_all         = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-private"
          + "Terraform"   = "true"
        }
      + vpc_id           = (known after apply)
    }

  # module.vpc.aws_route_table.public[0] will be created
  + resource "aws_route_table" "public" {
      + arn              = (known after apply)
      + id               = (known after apply)
      + owner_id         = (known after apply)
      + propagating_vgws = (known after apply)
      + route            = (known after apply)
      + tags             = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-public"
          + "Terraform"   = "true"
        }
      + tags_all         = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc-public"
          + "Terraform"   = "true"
        }
      + vpc_id           = (known after apply)
    }

  # module.vpc.aws_route_table_association.private[0] will be created
  + resource "aws_route_table_association" "private" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # module.vpc.aws_route_table_association.private[1] will be created
  + resource "aws_route_table_association" "private" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # module.vpc.aws_route_table_association.private[2] will be created
  + resource "aws_route_table_association" "private" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # module.vpc.aws_route_table_association.public[0] will be created
  + resource "aws_route_table_association" "public" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # module.vpc.aws_route_table_association.public[1] will be created
  + resource "aws_route_table_association" "public" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # module.vpc.aws_route_table_association.public[2] will be created
  + resource "aws_route_table_association" "public" {
      + id             = (known after apply)
      + route_table_id = (known after apply)
      + subnet_id      = (known after apply)
    }

  # module.vpc.aws_subnet.private[0] will be created
  + resource "aws_subnet" "private" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-west-2a"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.1.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-private-us-west-2a"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/internal-elb"         = "1"
        }
      + tags_all                                       = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-private-us-west-2a"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/internal-elb"         = "1"
        }
      + vpc_id                                         = (known after apply)
    }

  # module.vpc.aws_subnet.private[1] will be created
  + resource "aws_subnet" "private" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-west-2b"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.2.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-private-us-west-2b"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/internal-elb"         = "1"
        }
      + tags_all                                       = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-private-us-west-2b"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/internal-elb"         = "1"
        }
      + vpc_id                                         = (known after apply)
    }

  # module.vpc.aws_subnet.private[2] will be created
  + resource "aws_subnet" "private" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-west-2c"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.3.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-private-us-west-2c"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/internal-elb"         = "1"
        }
      + tags_all                                       = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-private-us-west-2c"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/internal-elb"         = "1"
        }
      + vpc_id                                         = (known after apply)
    }

  # module.vpc.aws_subnet.public[0] will be created
  + resource "aws_subnet" "public" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-west-2a"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.4.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-public-us-west-2a"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/elb"                  = "1"
        }
      + tags_all                                       = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-public-us-west-2a"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/elb"                  = "1"
        }
      + vpc_id                                         = (known after apply)
    }

  # module.vpc.aws_subnet.public[1] will be created
  + resource "aws_subnet" "public" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-west-2b"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.5.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-public-us-west-2b"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/elb"                  = "1"
        }
      + tags_all                                       = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-public-us-west-2b"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/elb"                  = "1"
        }
      + vpc_id                                         = (known after apply)
    }

  # module.vpc.aws_subnet.public[2] will be created
  + resource "aws_subnet" "public" {
      + arn                                            = (known after apply)
      + assign_ipv6_address_on_creation                = false
      + availability_zone                              = "us-west-2c"
      + availability_zone_id                           = (known after apply)
      + cidr_block                                     = "10.0.6.0/24"
      + enable_dns64                                   = false
      + enable_resource_name_dns_a_record_on_launch    = false
      + enable_resource_name_dns_aaaa_record_on_launch = false
      + id                                             = (known after apply)
      + ipv6_cidr_block_association_id                 = (known after apply)
      + ipv6_native                                    = false
      + map_public_ip_on_launch                        = false
      + owner_id                                       = (known after apply)
      + private_dns_hostname_type_on_launch            = (known after apply)
      + tags                                           = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-public-us-west-2c"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/elb"                  = "1"
        }
      + tags_all                                       = {
          + "Environment"                             = "devops-future"
          + "Name"                                    = "devops-future-vpc-public-us-west-2c"
          + "Terraform"                               = "true"
          + "kubernetes.io/cluster/devops-future-eks" = "shared"
          + "kubernetes.io/role/elb"                  = "1"
        }
      + vpc_id                                         = (known after apply)
    }

  # module.vpc.aws_vpc.this[0] will be created
  + resource "aws_vpc" "this" {
      + arn                                  = (known after apply)
      + cidr_block                           = "10.0.0.0/16"
      + default_network_acl_id               = (known after apply)
      + default_route_table_id               = (known after apply)
      + default_security_group_id            = (known after apply)
      + dhcp_options_id                      = (known after apply)
      + enable_dns_hostnames                 = true
      + enable_dns_support                   = true
      + enable_network_address_usage_metrics = (known after apply)
      + id                                   = (known after apply)
      + instance_tenancy                     = "default"
      + ipv6_association_id                  = (known after apply)
      + ipv6_cidr_block                      = (known after apply)
      + ipv6_cidr_block_network_border_group = (known after apply)
      + main_route_table_id                  = (known after apply)
      + owner_id                             = (known after apply)
      + tags                                 = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc"
          + "Terraform"   = "true"
        }
      + tags_all                             = {
          + "Environment" = "devops-future"
          + "Name"        = "devops-future-vpc"
          + "Terraform"   = "true"
        }
    }

Plan: 31 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + cluster_ca_certificate = (known after apply)
  + cluster_endpoint       = (known after apply)
  + cluster_name           = "devops-future-eks"
╷
│ Warning: Argument is deprecated
│ 
│   with module.vpc.aws_eip.nat,
│   on .terraform/modules/vpc/main.tf line 1044, in resource "aws_eip" "nat":
│ 1044:   vpc = true
│ 
│ vpc is deprecated. Use domain instead.
│ 
│ (and one more similar warning elsewhere)
╵

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

aws_iam_role.eks_cluster_role: Creating...
aws_iam_role.eks_node_role: Creating...
module.vpc.aws_vpc.this[0]: Creating...
module.vpc.aws_eip.nat[0]: Creating...
aws_iam_role.eks_cluster_role: Creation complete after 1s [id=devops-future-eks-cluster-role]
aws_iam_role_policy_attachment.eks_cluster_policy: Creating...
aws_iam_role.eks_node_role: Creation complete after 1s [id=devops-future-eks-node-role]
aws_iam_role_policy_attachment.eks_cni_policy: Creating...
aws_iam_role_policy_attachment.eks_registry_policy: Creating...
aws_iam_role_policy_attachment.eks_worker_node_policy: Creating...
aws_iam_role_policy_attachment.eks_cluster_policy: Creation complete after 1s [id=devops-future-eks-cluster-role-20250617115717494600000001]
aws_iam_role_policy_attachment.eks_worker_node_policy: Creation complete after 1s [id=devops-future-eks-node-role-20250617115717515900000002]
aws_iam_role_policy_attachment.eks_registry_policy: Creation complete after 1s [id=devops-future-eks-node-role-20250617115717661500000003]
aws_iam_role_policy_attachment.eks_cni_policy: Creation complete after 1s [id=devops-future-eks-node-role-20250617115717679900000004]
module.vpc.aws_eip.nat[0]: Creation complete after 2s [id=eipalloc-07bee3ea56ec8426a]
module.vpc.aws_vpc.this[0]: Still creating... [10s elapsed]
module.vpc.aws_vpc.this[0]: Creation complete after 14s [id=vpc-0419f826851bed40b]
module.vpc.aws_default_route_table.default[0]: Creating...
module.vpc.aws_route_table.public[0]: Creating...
module.vpc.aws_route_table.private[0]: Creating...
module.vpc.aws_subnet.public[0]: Creating...
module.vpc.aws_subnet.public[2]: Creating...
module.vpc.aws_default_security_group.this[0]: Creating...
module.vpc.aws_subnet.private[2]: Creating...
module.vpc.aws_subnet.private[1]: Creating...
module.vpc.aws_subnet.private[0]: Creating...
module.vpc.aws_default_network_acl.this[0]: Creating...
module.vpc.aws_default_route_table.default[0]: Creation complete after 1s [id=rtb-052439d5c7547876d]
module.vpc.aws_internet_gateway.this[0]: Creating...
module.vpc.aws_route_table.public[0]: Creation complete after 2s [id=rtb-0803bd36a97148d02]
module.vpc.aws_route_table.private[0]: Creation complete after 2s [id=rtb-09b58ebc02469f46a]
module.vpc.aws_subnet.public[1]: Creating...
module.vpc.aws_subnet.public[2]: Creation complete after 2s [id=subnet-073aeea8c80b0ae7d]
module.vpc.aws_subnet.public[0]: Creation complete after 2s [id=subnet-045e96fa58bc2a310]
module.vpc.aws_subnet.private[2]: Creation complete after 2s [id=subnet-0daf33689d4d952f9]
module.vpc.aws_subnet.private[1]: Creation complete after 2s [id=subnet-0bd30d3e15dbbf0e9]
module.vpc.aws_internet_gateway.this[0]: Creation complete after 2s [id=igw-0747291db3dbd9ada]
module.vpc.aws_route.public_internet_gateway[0]: Creating...
module.vpc.aws_subnet.public[1]: Creation complete after 1s [id=subnet-0bd56298610d384ec]
module.vpc.aws_route_table_association.public[1]: Creating...
module.vpc.aws_route_table_association.public[0]: Creating...
module.vpc.aws_route_table_association.public[2]: Creating...
module.vpc.aws_nat_gateway.this[0]: Creating...
module.vpc.aws_default_network_acl.this[0]: Creation complete after 3s [id=acl-0205b02d91017174a]
module.vpc.aws_route_table_association.public[1]: Creation complete after 1s [id=rtbassoc-0e5fe1d36ba433085]
module.vpc.aws_route_table_association.public[2]: Creation complete after 1s [id=rtbassoc-0cfe6cc5819d783e2]
module.vpc.aws_default_security_group.this[0]: Creation complete after 4s [id=sg-06b6bdf607bfa2529]
module.vpc.aws_route_table_association.public[0]: Creation complete after 1s [id=rtbassoc-0780201f8468ea91d]
module.vpc.aws_route.public_internet_gateway[0]: Creation complete after 1s [id=r-rtb-0803bd36a97148d021080289494]
module.vpc.aws_subnet.private[0]: Creation complete after 4s [id=subnet-0809a54954221ea85]
module.vpc.aws_route_table_association.private[0]: Creating...
module.vpc.aws_route_table_association.private[1]: Creating...
module.vpc.aws_route_table_association.private[2]: Creating...
module.vpc.aws_route_table_association.private[1]: Creation complete after 1s [id=rtbassoc-0b9b64d093343ede3]
module.vpc.aws_route_table_association.private[0]: Creation complete after 1s [id=rtbassoc-0e230bcf141ce464f]
module.vpc.aws_route_table_association.private[2]: Creation complete after 1s [id=rtbassoc-05b61607ffa0480ed]
module.vpc.aws_nat_gateway.this[0]: Still creating... [10s elapsed]
module.vpc.aws_nat_gateway.this[0]: Still creating... [20s elapsed]
module.vpc.aws_nat_gateway.this[0]: Still creating... [30s elapsed]
module.vpc.aws_nat_gateway.this[0]: Still creating... [40s elapsed]
module.vpc.aws_nat_gateway.this[0]: Still creating... [50s elapsed]
module.vpc.aws_nat_gateway.this[0]: Still creating... [1m0s elapsed]
module.vpc.aws_nat_gateway.this[0]: Still creating... [1m10s elapsed]
module.vpc.aws_nat_gateway.this[0]: Still creating... [1m20s elapsed]
module.vpc.aws_nat_gateway.this[0]: Still creating... [1m30s elapsed]
module.vpc.aws_nat_gateway.this[0]: Still creating... [1m40s elapsed]
module.vpc.aws_nat_gateway.this[0]: Creation complete after 1m47s [id=nat-0f1c2f3a451d37479]
module.vpc.aws_route.private_nat_gateway[0]: Creating...
module.vpc.aws_route.private_nat_gateway[0]: Creation complete after 2s [id=r-rtb-09b58ebc02469f46a1080289494]
aws_eks_cluster.this: Creating...
aws_eks_cluster.this: Still creating... [10s elapsed]
aws_eks_cluster.this: Still creating... [20s elapsed]
aws_eks_cluster.this: Still creating... [30s elapsed]
aws_eks_cluster.this: Still creating... [40s elapsed]
aws_eks_cluster.this: Still creating... [50s elapsed]
aws_eks_cluster.this: Still creating... [1m0s elapsed]
aws_eks_cluster.this: Still creating... [1m10s elapsed]
aws_eks_cluster.this: Still creating... [1m20s elapsed]
aws_eks_cluster.this: Still creating... [1m30s elapsed]
aws_eks_cluster.this: Still creating... [1m40s elapsed]
aws_eks_cluster.this: Still creating... [1m50s elapsed]
aws_eks_cluster.this: Still creating... [2m0s elapsed]
aws_eks_cluster.this: Still creating... [2m10s elapsed]
aws_eks_cluster.this: Still creating... [2m20s elapsed]
aws_eks_cluster.this: Still creating... [2m30s elapsed]
aws_eks_cluster.this: Still creating... [2m40s elapsed]
aws_eks_cluster.this: Still creating... [2m50s elapsed]
aws_eks_cluster.this: Still creating... [3m0s elapsed]
aws_eks_cluster.this: Still creating... [3m10s elapsed]
aws_eks_cluster.this: Still creating... [3m20s elapsed]
aws_eks_cluster.this: Still creating... [3m30s elapsed]
aws_eks_cluster.this: Still creating... [3m40s elapsed]
aws_eks_cluster.this: Still creating... [3m50s elapsed]
aws_eks_cluster.this: Still creating... [4m0s elapsed]
aws_eks_cluster.this: Still creating... [4m10s elapsed]
aws_eks_cluster.this: Still creating... [4m20s elapsed]
aws_eks_cluster.this: Still creating... [4m30s elapsed]
aws_eks_cluster.this: Still creating... [4m40s elapsed]
aws_eks_cluster.this: Still creating... [4m50s elapsed]
aws_eks_cluster.this: Still creating... [5m0s elapsed]
aws_eks_cluster.this: Still creating... [5m10s elapsed]
aws_eks_cluster.this: Still creating... [5m20s elapsed]
aws_eks_cluster.this: Still creating... [5m30s elapsed]
aws_eks_cluster.this: Still creating... [5m40s elapsed]
aws_eks_cluster.this: Still creating... [5m50s elapsed]
aws_eks_cluster.this: Still creating... [6m0s elapsed]
aws_eks_cluster.this: Still creating... [6m10s elapsed]
aws_eks_cluster.this: Still creating... [6m20s elapsed]
aws_eks_cluster.this: Still creating... [6m30s elapsed]
aws_eks_cluster.this: Still creating... [6m40s elapsed]
aws_eks_cluster.this: Still creating... [6m50s elapsed]
aws_eks_cluster.this: Still creating... [7m0s elapsed]
aws_eks_cluster.this: Still creating... [7m10s elapsed]
aws_eks_cluster.this: Still creating... [7m20s elapsed]
aws_eks_cluster.this: Still creating... [7m30s elapsed]
aws_eks_cluster.this: Still creating... [7m40s elapsed]
aws_eks_cluster.this: Still creating... [7m50s elapsed]
aws_eks_cluster.this: Still creating... [8m0s elapsed]
aws_eks_cluster.this: Still creating... [8m10s elapsed]
aws_eks_cluster.this: Still creating... [8m20s elapsed]
aws_eks_cluster.this: Still creating... [8m30s elapsed]
aws_eks_cluster.this: Still creating... [8m40s elapsed]
aws_eks_cluster.this: Creation complete after 8m44s [id=devops-future-eks]
aws_eks_node_group.this: Creating...
aws_eks_node_group.this: Still creating... [10s elapsed]
aws_eks_node_group.this: Still creating... [20s elapsed]
aws_eks_node_group.this: Still creating... [30s elapsed]
aws_eks_node_group.this: Still creating... [40s elapsed]
aws_eks_node_group.this: Still creating... [50s elapsed]
aws_eks_node_group.this: Still creating... [1m0s elapsed]
aws_eks_node_group.this: Still creating... [1m10s elapsed]
aws_eks_node_group.this: Still creating... [1m20s elapsed]
aws_eks_node_group.this: Still creating... [1m30s elapsed]
aws_eks_node_group.this: Still creating... [1m40s elapsed]
aws_eks_node_group.this: Still creating... [1m50s elapsed]
aws_eks_node_group.this: Creation complete after 1m50s [id=devops-future-eks:devops-future-node-group]
╷
│ Warning: Argument is deprecated
│ 
│   with module.vpc.aws_eip.nat[0],
│   on .terraform/modules/vpc/main.tf line 1044, in resource "aws_eip" "nat":
│ 1044:   vpc = true
│ 
│ vpc is deprecated. Use domain instead.
╵

Apply complete! Resources: 31 added, 0 changed, 0 destroyed.

Outputs:

cluster_ca_certificate = "LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURCVENDQWUyZ0F3SUJBZ0lJTWRiKzhrWVZxLzB3RFFZSktvWklodmNOQVFFTEJRQXdGVEVUTUJFR0ExVUUKQXhNS2EzVmlaWEp1WlhSbGN6QWVGdzB5TlRBMk1UY3hNVFU0TlRKYUZ3MHpOVEEyTVRVeE1qQXpOVEphTUJVeApFekFSQmdOVkJBTVRDbXQxWW1WeWJtVjBaWE13Z2dFaU1BMEdDU3FHU0liM0RRRUJBUVVBQTRJQkR3QXdnZ0VLCkFvSUJBUURFU29hRXpqNXM2cE9YckNlL2JMcnVhVUFBOG51YnU4YW10Y3MrMWRVQ2drLzNFbnhTTUgxR0NMeEcKMTQ0OXZKZ1I5TUpWSmlpODdJQlJRaDVUNGN0SHFJZEJwTEFUNTlpNnJ3VlFvTXVlNHovdXFKQnZMOHNDdmRJRQpSZlRVTWdLMU1tclA5TEJDZjdYUm5XdWFDem1WUnNUKytRVCtvdWZXVHBuZEM1V3hkRktMQ3NvTGYzTzZZSUVYCnBQS21rcXk2MFdxcDVVTWdBZXJNMGFXeHFGWHpHS0o0QkE3Y3hPM1crUHViWlQ1TXUzZ1NNbHYrUThqS0RSeVYKVEFyQUY5NDNhelNncjJKT3FPTGxxMUw4bllLemtsR3ZYcTl2VTUvdFFwRkVHR3hOZ0JWQnBnNUpva0JXRGg5MApsOGE3eVFpR3EzLy9iR2lSdHp6b2M2UjM2Z29qQWdNQkFBR2pXVEJYTUE0R0ExVWREd0VCL3dRRUF3SUNwREFQCkJnTlZIUk1CQWY4RUJUQURBUUgvTUIwR0ExVWREZ1FXQkJSUWpxY0Vrb1V6MkNvVC83VGVvUEdCUGZHUVRUQVYKQmdOVkhSRUVEakFNZ2dwcmRXSmxjbTVsZEdWek1BMEdDU3FHU0liM0RRRUJDd1VBQTRJQkFRQm1FUkt1SVE4NgphcWZXbXZFakVrbVRQOWlBcUpKTTNlRnVkMmYyNi9TYk1pTWMxTzgyWnJwRVZCUVdiNWorSGFablozZDFOQkh1CmdIdFBYdU5TaWhHVkQ2enhNUTRuSm5lTFRjMzArcjkwaUsrOUR1M1Q3dE4rbFE2RytpMkgzOTdjeWhkQWl2YTAKY3pQd3RiUzhXTWU3dWRzS3RVa1liRXIvVzUvZEdHOW94UVN0a012WG9zcG9UbGllRU1RRHJEc0tpVUg1dENUQgp3bW10VUVIeXFNVCtjTGlMVG9WcER1bGd3VzA2dFViaEdGUVVTNXNtY1FoUHZwZDFSVTN5WVh2aEhFQ0Vodk84CnpuTUl6ZmM1T3dvYmNRSnV5Sm5RVHEySjVic3Q5T2VGMTNnQjVnWHcxYlFYUkZNanVITVY0Ny9haVVnS3BBSG8KK1NGV3NIQ29PRmt0Ci0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K"
cluster_endpoint = "https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com"
cluster_name = "devops-future-eks"
(base) xxradar@Philippes-MacBook-Pro devopsfuture % ./configure-kubeconfig.sh 
Kubeconfig file created at: /Users/xxradar/testing/devopsfuture/devops-future-kubeconfig
To use this config file, run:
export KUBECONFIG=/Users/xxradar/testing/devopsfuture/devops-future-kubeconfig
(base) xxradar@Philippes-MacBook-Pro devopsfuture % export KUBECONFIG=/Users/xxradar/testing/devopsfuture/devops-future-kubeconfig
(base) xxradar@Philippes-MacBook-Pro devopsfuture % kubectl get no
E0617 14:10:42.991431   89475 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:10:43.364022   89475 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:10:43.735065   89475 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:10:44.101535   89475 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:10:44.471347   89475 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
Unable to connect to the server: getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string "json:\"apiVersion,omitempty\""; Kind string "json:\"kind,omitempty\"" }
(base) xxradar@Philippes-MacBook-Pro devopsfuture % kubectl get no
E0617 14:11:47.321086   90011 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:11:47.683944   90011 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:11:48.049924   90011 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:11:48.417056   90011 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:11:48.806976   90011 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
Unable to connect to the server: getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string "json:\"apiVersion,omitempty\""; Kind string "json:\"kind,omitempty\"" }
(base) xxradar@Philippes-MacBook-Pro devopsfuture % 
(base) xxradar@Philippes-MacBook-Pro devopsfuture % kubectl get po
E0617 14:11:51.942860   90155 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:11:52.308676   90155 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:11:52.678894   90155 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:11:53.047663   90155 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
E0617 14:11:53.414723   90155 memcache.go:265] "Unhandled Error" err="couldn't get current server API group list: Get \"https://C3B6B7564CE3BB49C8C8D3A0A80FDEA9.gr7.us-west-2.eks.amazonaws.com/api?timeout=32s\": getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string \"json:\\\"apiVersion,omitempty\\\"\"; Kind string \"json:\\\"kind,omitempty\\\"\" }"
Unable to connect to the server: getting credentials: decoding stdout: couldn't get version/kind; json parse error: json: cannot unmarshal string into Go value of type struct { APIVersion string "json:\"apiVersion,omitempty\""; Kind string "json:\"kind,omitempty\"" }
(base) xxradar@Philippes-MacBook-Pro devopsfuture % 
(base) xxradar@Philippes-MacBook-Pro devopsfuture % 
(base) xxradar@Philippes-MacBook-Pro devopsfuture % 
(base) xxradar@Philippes-MacBook-Pro devopsfuture % 
(base) xxradar@Philippes-MacBook-Pro devopsfuture % 
(base) xxradar@Philippes-MacBook-Pro devopsfuture % 
(base) xxradar@Philippes-MacBook-Pro devopsfuture % export AWS_DEFAULT_OUTPUT=json
(base) xxradar@Philippes-MacBook-Pro devopsfuture % kubectl get po                
No resources found in default namespace.
(base) xxradar@Philippes-MacBook-Pro devopsfuture % kubectl get po -A
NAMESPACE     NAME                      READY   STATUS    RESTARTS   AGE
kube-system   aws-node-gkgg5            2/2     Running   0          6m31s
kube-system   aws-node-r9djw            2/2     Running   0          6m31s
kube-system   aws-node-wpn2v            2/2     Running   0          6m30s
kube-system   coredns-9556476b9-jnwl4   1/1     Running   0          9m54s
kube-system   coredns-9556476b9-kf9xn   1/1     Running   0          9m54s
kube-system   kube-proxy-2pqml          1/1     Running   0          6m31s
kube-system   kube-proxy-r9ndk          1/1     Running   0          6m31s
kube-system   kube-proxy-xfmws          1/1     Running   0          6m30s
(base) xxradar@Philippes-MacBook-Pro devopsfuture %
```
