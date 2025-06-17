```
POLICY-ID                      SEVERITY PASS  TITLE                                                               FILE-PATH                      LINE EXCEPTED EXCEPTION
lacework-iac-aws-network-1     High     false EKS should not allow public access to API endpoint                  main.tf                        111  false    
lacework-iac-aws-encryption-10 High     false EKS Clusters should encrypt secrets                                 main.tf                        111  false    
lacework-iac-aws-logging-1     Medium   false EKS Cluster should have control plane logging enabled               main.tf                        111  false    
lacework-iac-aws-logging-24    Low      false Ensure VPC Flow Logging is enabled for all VPCs                     .terraform/modules/vpc/main.tf 29   false    
ckv-aws-41                     Critical true  Ensure no hard coded AWS access & secret keys exists in provider    main.tf                        4    false    
lacework-iac-aws-network-9     High     true  Ensure Amazon EKS Node group has implicit SSH access from 0.0.0.0/0 main.tf                        132  false    
lacework-iac-aws-network-14    High     true  Ensure VPC Subnets Do Not Automatically Assign Public IP Addresses  .terraform/modules/vpc/main.tf 98   false    
lacework-iac-aws-network-14    High     true  Ensure VPC Subnets Do Not Automatically Assign Public IP Addresses  .terraform/modules/vpc/main.tf 225  false    
ckv-aws-60                     Medium   true  Ensure IAM role allows only specific services or principals         main.tf                        75   false    
ckv-aws-61                     Medium   true  Ensure IAM role allows only specific principals                     main.tf                        75   false    
ckv-aws-60                     Medium   true  Ensure IAM role allows only specific services or principals         main.tf                        49   false    
ckv-aws-61                     Medium   true  Ensure IAM role allows only specific principals                     main.tf                        49   false    
(base) xxradar@Philippes-MacBook-Pro devopsfuture %
```


