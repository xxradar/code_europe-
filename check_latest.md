```
POLICY-ID                      SEVERITY PASS  TITLE                                                               FILE-PATH                               LINE EXCEPTED EXCEPTION
lacework-iac-aws-encryption-10 High     false EKS Clusters should encrypt secrets                                 main.tf                                 244  false    
lacework-iac-aws-encryption-24 High     false Ensure that CloudWatch Log Group is encrypted by KMS                main.tf                                 121  false    
lacework-iac-aws-encryption-24 High     false Ensure that CloudWatch Log Group is encrypted by KMS                .terraform/modules/vpc/vpc-flow-logs.tf 65   false    
lacework-iac-aws-network-1     High     false EKS should not allow public access to API endpoint                  main.tf                                 244  false    
lacework-iac-aws-monitoring-2  Low      false Ensure CloudWatch log groups retains logs for at least 1 year       main.tf                                 121  false    
lacework-iac-aws-monitoring-1  Low      false Ensure that detailed monitoring is enabled for EC2 instances        main.tf                                 335  false    
lacework-iac-aws-network-2     Low      false AWS resources must specify a Security Group                         main.tf                                 335  false    
lacework-iac-aws-monitoring-2  Low      false Ensure CloudWatch log groups retains logs for at least 1 year       .terraform/modules/vpc/vpc-flow-logs.tf 65   false    
ckv-aws-41                     Critical true  Ensure no hard coded AWS access & secret keys exists in provider    main.tf                                 4    false    
ckv-aws-88                     Critical true  EC2 instance should not have public IP                              main.tf                                 335  false    
lacework-iac-aws-iam-8         Critical true  Ensure IAM policies do not allow administrative privileges          .terraform/modules/vpc/vpc-flow-logs.tf 89   false    
lacework-iac-aws-iam-8         Critical true  Ensure IAM policies do not allow administrative privileges          .terraform/modules/vpc/vpc-flow-logs.tf 131  false    
ckv-aws-46                     Critical true  No hard coded access and secret key in EC2 instances                main.tf                                 335  false    
lacework-iac-aws-network-14    High     true  Ensure VPC Subnets Do Not Automatically Assign Public IP Addresses  .terraform/modules/vpc/main.tf          267  false    
lacework-iac-aws-network-9     High     true  Ensure Amazon EKS Node group has implicit SSH access from 0.0.0.0/0 main.tf                                 368  false    
lacework-iac-aws-network-14    High     true  Ensure VPC Subnets Do Not Automatically Assign Public IP Addresses  .terraform/modules/vpc/main.tf          131  false    
ckv-aws-61                     Medium   true  Ensure IAM role allows only specific principals                     main.tf                                 170  false    
ckv-aws-60                     Medium   true  Ensure IAM role allows only specific services or principals         main.tf                                 202  false    
ckv-aws-61                     Medium   true  Ensure IAM role allows only specific principals                     main.tf                                 202  false    
lacework-iac-aws-logging-1     Medium   true  EKS Cluster should have control plane logging enabled               main.tf                                 244  false    
ckv-aws-60                     Medium   true  Ensure IAM role allows only specific services or principals         main.tf                                 170  false    
lacework-iac-aws-logging-24    Low      true  Ensure VPC Flow Logging is enabled for all VPCs                     .terraform/modules/vpc/main.tf          28   false    
lacework-iac-aws-security-9    Low      true  Missing description for security group/security group rule          main.tf                                 273  false    
```
