!!! note
	(D):  有这个标识的，就表示被弃用的。
	更新于 2020-04，最新列表见[官网](https://docs.ansible.com/ansible/latest/modules/modules_by_category.html)

## Cloud modules

### Alicloud

- [ali_instance – Create, Start, Stop, Restart or Terminate an Instance in ECS. Add or Remove Instance to/from a Security Group](https://docs.ansible.com/ansible/latest/modules/ali_instance_module.html#ali-instance-module)
- [ali_instance_info – Gather information on instances of Alibaba Cloud ECS](https://docs.ansible.com/ansible/latest/modules/ali_instance_info_module.html#ali-instance-info-module)



### Amazon

- [aws_acm_info – Retrieve certificate information from AWS Certificate Manager service](https://docs.ansible.com/ansible/latest/modules/aws_acm_info_module.html#aws-acm-info-module)
- [aws_api_gateway – Manage AWS API Gateway APIs](https://docs.ansible.com/ansible/latest/modules/aws_api_gateway_module.html#aws-api-gateway-module)
- [aws_application_scaling_policy – Manage Application Auto Scaling Scaling Policies](https://docs.ansible.com/ansible/latest/modules/aws_application_scaling_policy_module.html#aws-application-scaling-policy-module)
- [aws_az_info – Gather information about availability zones in AWS](https://docs.ansible.com/ansible/latest/modules/aws_az_info_module.html#aws-az-info-module)
- [aws_batch_compute_environment – Manage AWS Batch Compute Environments](https://docs.ansible.com/ansible/latest/modules/aws_batch_compute_environment_module.html#aws-batch-compute-environment-module)
- [aws_batch_job_definition – Manage AWS Batch Job Definitions](https://docs.ansible.com/ansible/latest/modules/aws_batch_job_definition_module.html#aws-batch-job-definition-module)
- [aws_batch_job_queue – Manage AWS Batch Job Queues](https://docs.ansible.com/ansible/latest/modules/aws_batch_job_queue_module.html#aws-batch-job-queue-module)
- [aws_caller_info – Get information about the user and account being used to make AWS calls](https://docs.ansible.com/ansible/latest/modules/aws_caller_info_module.html#aws-caller-info-module)
- [aws_codebuild – Create or delete an AWS CodeBuild project](https://docs.ansible.com/ansible/latest/modules/aws_codebuild_module.html#aws-codebuild-module)
- [aws_codecommit – Manage repositories in AWS CodeCommit](https://docs.ansible.com/ansible/latest/modules/aws_codecommit_module.html#aws-codecommit-module)
- [aws_codepipeline – Create or delete AWS CodePipelines](https://docs.ansible.com/ansible/latest/modules/aws_codepipeline_module.html#aws-codepipeline-module)
- [aws_config_aggregation_authorization – Manage cross-account AWS Config authorizations](https://docs.ansible.com/ansible/latest/modules/aws_config_aggregation_authorization_module.html#aws-config-aggregation-authorization-module)
- [aws_config_aggregator – Manage AWS Config aggregations across multiple accounts](https://docs.ansible.com/ansible/latest/modules/aws_config_aggregator_module.html#aws-config-aggregator-module)
- [aws_config_delivery_channel – Manage AWS Config delivery channels](https://docs.ansible.com/ansible/latest/modules/aws_config_delivery_channel_module.html#aws-config-delivery-channel-module)
- [aws_config_recorder – Manage AWS Config Recorders](https://docs.ansible.com/ansible/latest/modules/aws_config_recorder_module.html#aws-config-recorder-module)
- [aws_config_rule – Manage AWS Config resources](https://docs.ansible.com/ansible/latest/modules/aws_config_rule_module.html#aws-config-rule-module)
- [aws_direct_connect_connection – Creates, deletes, modifies a DirectConnect connection](https://docs.ansible.com/ansible/latest/modules/aws_direct_connect_connection_module.html#aws-direct-connect-connection-module)
- [aws_direct_connect_gateway – Manage AWS Direct Connect Gateway](https://docs.ansible.com/ansible/latest/modules/aws_direct_connect_gateway_module.html#aws-direct-connect-gateway-module)
- [aws_direct_connect_link_aggregation_group – Manage Direct Connect LAG bundles](https://docs.ansible.com/ansible/latest/modules/aws_direct_connect_link_aggregation_group_module.html#aws-direct-connect-link-aggregation-group-module)
- [aws_direct_connect_virtual_interface – Manage Direct Connect virtual interfaces](https://docs.ansible.com/ansible/latest/modules/aws_direct_connect_virtual_interface_module.html#aws-direct-connect-virtual-interface-module)
- [aws_eks_cluster – Manage Elastic Kubernetes Service Clusters](https://docs.ansible.com/ansible/latest/modules/aws_eks_cluster_module.html#aws-eks-cluster-module)
- [aws_elasticbeanstalk_app – create, update, and delete an elastic beanstalk application](https://docs.ansible.com/ansible/latest/modules/aws_elasticbeanstalk_app_module.html#aws-elasticbeanstalk-app-module)
- [aws_glue_connection – Manage an AWS Glue connection](https://docs.ansible.com/ansible/latest/modules/aws_glue_connection_module.html#aws-glue-connection-module)
- [aws_glue_job – Manage an AWS Glue job](https://docs.ansible.com/ansible/latest/modules/aws_glue_job_module.html#aws-glue-job-module)
- [aws_inspector_target – Create, Update and Delete Amazon Inspector Assessment Targets](https://docs.ansible.com/ansible/latest/modules/aws_inspector_target_module.html#aws-inspector-target-module)
- [aws_kms – Perform various KMS management tasks](https://docs.ansible.com/ansible/latest/modules/aws_kms_module.html#aws-kms-module)
- [aws_kms_info – Gather information about AWS KMS keys](https://docs.ansible.com/ansible/latest/modules/aws_kms_info_module.html#aws-kms-info-module)
- [aws_netapp_cvs_active_directory – NetApp AWS CloudVolumes Service Manage Active Directory](https://docs.ansible.com/ansible/latest/modules/aws_netapp_cvs_active_directory_module.html#aws-netapp-cvs-active-directory-module)
- [aws_netapp_cvs_FileSystems – NetApp AWS Cloud Volumes Service Manage FileSystem](https://docs.ansible.com/ansible/latest/modules/aws_netapp_cvs_FileSystems_module.html#aws-netapp-cvs-filesystems-module)
- [aws_netapp_cvs_pool – NetApp AWS Cloud Volumes Service Manage Pools](https://docs.ansible.com/ansible/latest/modules/aws_netapp_cvs_pool_module.html#aws-netapp-cvs-pool-module)
- [aws_netapp_cvs_snapshots – NetApp AWS Cloud Volumes Service Manage Snapshots](https://docs.ansible.com/ansible/latest/modules/aws_netapp_cvs_snapshots_module.html#aws-netapp-cvs-snapshots-module)
- [aws_region_info – Gather information about AWS regions](https://docs.ansible.com/ansible/latest/modules/aws_region_info_module.html#aws-region-info-module)
- [aws_s3 – manage objects in S3](https://docs.ansible.com/ansible/latest/modules/aws_s3_module.html#aws-s3-module)
- [aws_s3_bucket_info – Lists S3 buckets in AWS](https://docs.ansible.com/ansible/latest/modules/aws_s3_bucket_info_module.html#aws-s3-bucket-info-module)
- [aws_s3_cors – Manage CORS for S3 buckets in AWS](https://docs.ansible.com/ansible/latest/modules/aws_s3_cors_module.html#aws-s3-cors-module)
- [aws_secret – Manage secrets stored in AWS Secrets Manager](https://docs.ansible.com/ansible/latest/modules/aws_secret_module.html#aws-secret-module)
- [aws_ses_identity – Manages SES email and domain identity](https://docs.ansible.com/ansible/latest/modules/aws_ses_identity_module.html#aws-ses-identity-module)
- [aws_ses_identity_policy – Manages SES sending authorization policies](https://docs.ansible.com/ansible/latest/modules/aws_ses_identity_policy_module.html#aws-ses-identity-policy-module)
- [aws_ses_rule_set – Manages SES inbound receipt rule sets](https://docs.ansible.com/ansible/latest/modules/aws_ses_rule_set_module.html#aws-ses-rule-set-module)
- [aws_sgw_info – Fetch AWS Storage Gateway information](https://docs.ansible.com/ansible/latest/modules/aws_sgw_info_module.html#aws-sgw-info-module)
- [aws_ssm_parameter_store – Manage key-value pairs in aws parameter store](https://docs.ansible.com/ansible/latest/modules/aws_ssm_parameter_store_module.html#aws-ssm-parameter-store-module)
- [aws_waf_condition – create and delete WAF Conditions](https://docs.ansible.com/ansible/latest/modules/aws_waf_condition_module.html#aws-waf-condition-module)
- [aws_waf_info – Retrieve information for WAF ACLs, Rule , Conditions and Filters](https://docs.ansible.com/ansible/latest/modules/aws_waf_info_module.html#aws-waf-info-module)
- [aws_waf_rule – create and delete WAF Rules](https://docs.ansible.com/ansible/latest/modules/aws_waf_rule_module.html#aws-waf-rule-module)
- [aws_waf_web_acl – create and delete WAF Web ACLs](https://docs.ansible.com/ansible/latest/modules/aws_waf_web_acl_module.html#aws-waf-web-acl-module)
- [cloudformation – Create or delete an AWS CloudFormation stack](https://docs.ansible.com/ansible/latest/modules/cloudformation_module.html#cloudformation-module)
- [cloudformation_info – Obtain information about an AWS CloudFormation stack](https://docs.ansible.com/ansible/latest/modules/cloudformation_info_module.html#cloudformation-info-module)
- [cloudformation_stack_set – Manage groups of CloudFormation stacks](https://docs.ansible.com/ansible/latest/modules/cloudformation_stack_set_module.html#cloudformation-stack-set-module)
- [cloudfront_distribution – create, update and delete aws cloudfront distributions](https://docs.ansible.com/ansible/latest/modules/cloudfront_distribution_module.html#cloudfront-distribution-module)
- [cloudfront_info – Obtain facts about an AWS CloudFront distribution](https://docs.ansible.com/ansible/latest/modules/cloudfront_info_module.html#cloudfront-info-module)
- [cloudfront_invalidation – create invalidations for aws cloudfront distributions](https://docs.ansible.com/ansible/latest/modules/cloudfront_invalidation_module.html#cloudfront-invalidation-module)
- [cloudfront_origin_access_identity – create, update and delete origin access identities for a cloudfront distribution](https://docs.ansible.com/ansible/latest/modules/cloudfront_origin_access_identity_module.html#cloudfront-origin-access-identity-module)
- [cloudtrail – manage CloudTrail create, delete, update](https://docs.ansible.com/ansible/latest/modules/cloudtrail_module.html#cloudtrail-module)
- [cloudwatchevent_rule – Manage CloudWatch Event rules and targets](https://docs.ansible.com/ansible/latest/modules/cloudwatchevent_rule_module.html#cloudwatchevent-rule-module)
- [cloudwatchlogs_log_group – create or delete log_group in CloudWatchLogs](https://docs.ansible.com/ansible/latest/modules/cloudwatchlogs_log_group_module.html#cloudwatchlogs-log-group-module)
- [cloudwatchlogs_log_group_info – get information about log_group in CloudWatchLogs](https://docs.ansible.com/ansible/latest/modules/cloudwatchlogs_log_group_info_module.html#cloudwatchlogs-log-group-info-module)
- [data_pipeline – Create and manage AWS Datapipelines](https://docs.ansible.com/ansible/latest/modules/data_pipeline_module.html#data-pipeline-module)
- [dms_endpoint – creates or destroys a data migration services endpoint](https://docs.ansible.com/ansible/latest/modules/dms_endpoint_module.html#dms-endpoint-module)
- [dms_replication_subnet_group – creates or destroys a data migration services subnet group](https://docs.ansible.com/ansible/latest/modules/dms_replication_subnet_group_module.html#dms-replication-subnet-group-module)
- [dynamodb_table – Create, update or delete AWS Dynamo DB tables](https://docs.ansible.com/ansible/latest/modules/dynamodb_table_module.html#dynamodb-table-module)
- [dynamodb_ttl – set TTL for a given DynamoDB table](https://docs.ansible.com/ansible/latest/modules/dynamodb_ttl_module.html#dynamodb-ttl-module)
- [ec2 – create, terminate, start or stop an instance in ec2](https://docs.ansible.com/ansible/latest/modules/ec2_module.html#ec2-module)
- [ec2_ami – create or destroy an image in ec2](https://docs.ansible.com/ansible/latest/modules/ec2_ami_module.html#ec2-ami-module)
- [ec2_ami_copy – copies AMI between AWS regions, return new image id](https://docs.ansible.com/ansible/latest/modules/ec2_ami_copy_module.html#ec2-ami-copy-module)
- [ec2_ami_info – Gather information about ec2 AMIs](https://docs.ansible.com/ansible/latest/modules/ec2_ami_info_module.html#ec2-ami-info-module)
- [ec2_asg – Create or delete AWS Autoscaling Groups](https://docs.ansible.com/ansible/latest/modules/ec2_asg_module.html#ec2-asg-module)
- [ec2_asg_info – Gather information about ec2 Auto Scaling Groups (ASGs) in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_asg_info_module.html#ec2-asg-info-module)
- [ec2_asg_lifecycle_hook – Create, delete or update AWS ASG Lifecycle Hooks](https://docs.ansible.com/ansible/latest/modules/ec2_asg_lifecycle_hook_module.html#ec2-asg-lifecycle-hook-module)
- [ec2_customer_gateway – Manage an AWS customer gateway](https://docs.ansible.com/ansible/latest/modules/ec2_customer_gateway_module.html#ec2-customer-gateway-module)
- [ec2_customer_gateway_info – Gather information about customer gateways in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_customer_gateway_info_module.html#ec2-customer-gateway-info-module)
- [ec2_eip – manages EC2 elastic IP (EIP) addresses](https://docs.ansible.com/ansible/latest/modules/ec2_eip_module.html#ec2-eip-module)
- [ec2_eip_info – List EC2 EIP details](https://docs.ansible.com/ansible/latest/modules/ec2_eip_info_module.html#ec2-eip-info-module)
- [ec2_elb – De-registers or registers instances from EC2 ELBs](https://docs.ansible.com/ansible/latest/modules/ec2_elb_module.html#ec2-elb-module)
- [ec2_elb_info – Gather information about EC2 Elastic Load Balancers in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_elb_info_module.html#ec2-elb-info-module)
- [ec2_elb_lb – Creates, updates or destroys an Amazon ELB](https://docs.ansible.com/ansible/latest/modules/ec2_elb_lb_module.html#ec2-elb-lb-module)
- [ec2_eni – Create and optionally attach an Elastic Network Interface (ENI) to an instance](https://docs.ansible.com/ansible/latest/modules/ec2_eni_module.html#ec2-eni-module)
- [ec2_eni_info – Gather information about ec2 ENI interfaces in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_eni_info_module.html#ec2-eni-info-module)
- [ec2_group – maintain an ec2 VPC security group](https://docs.ansible.com/ansible/latest/modules/ec2_group_module.html#ec2-group-module)
- [ec2_group_info – Gather information about ec2 security groups in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_group_info_module.html#ec2-group-info-module)
- [ec2_instance – Create & manage EC2 instances](https://docs.ansible.com/ansible/latest/modules/ec2_instance_module.html#ec2-instance-module)
- [ec2_instance_info – Gather information about ec2 instances in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_instance_info_module.html#ec2-instance-info-module)
- [ec2_key – create or delete an ec2 key pair](https://docs.ansible.com/ansible/latest/modules/ec2_key_module.html#ec2-key-module)
- [ec2_launch_template – Manage EC2 launch templates](https://docs.ansible.com/ansible/latest/modules/ec2_launch_template_module.html#ec2-launch-template-module)
- [ec2_lc – Create or delete AWS Autoscaling Launch Configurations](https://docs.ansible.com/ansible/latest/modules/ec2_lc_module.html#ec2-lc-module)
- [ec2_lc_find – Find AWS Autoscaling Launch Configurations](https://docs.ansible.com/ansible/latest/modules/ec2_lc_find_module.html#ec2-lc-find-module)
- [ec2_lc_info – Gather information about AWS Autoscaling Launch Configurations](https://docs.ansible.com/ansible/latest/modules/ec2_lc_info_module.html#ec2-lc-info-module)
- [ec2_metadata_facts – Gathers facts (instance metadata) about remote hosts within ec2](https://docs.ansible.com/ansible/latest/modules/ec2_metadata_facts_module.html#ec2-metadata-facts-module)
- [ec2_metric_alarm – Create/update or delete AWS Cloudwatch ‘metric alarms’](https://docs.ansible.com/ansible/latest/modules/ec2_metric_alarm_module.html#ec2-metric-alarm-module)
- [ec2_placement_group – Create or delete an EC2 Placement Group](https://docs.ansible.com/ansible/latest/modules/ec2_placement_group_module.html#ec2-placement-group-module)
- [ec2_placement_group_info – List EC2 Placement Group(s) details](https://docs.ansible.com/ansible/latest/modules/ec2_placement_group_info_module.html#ec2-placement-group-info-module)
- [ec2_scaling_policy – Create or delete AWS scaling policies for Autoscaling groups](https://docs.ansible.com/ansible/latest/modules/ec2_scaling_policy_module.html#ec2-scaling-policy-module)
- [ec2_snapshot – creates a snapshot from an existing volume](https://docs.ansible.com/ansible/latest/modules/ec2_snapshot_module.html#ec2-snapshot-module)
- [ec2_snapshot_copy – copies an EC2 snapshot and returns the new Snapshot ID](https://docs.ansible.com/ansible/latest/modules/ec2_snapshot_copy_module.html#ec2-snapshot-copy-module)
- [ec2_snapshot_info – Gather information about ec2 volume snapshots in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_snapshot_info_module.html#ec2-snapshot-info-module)
- [ec2_tag – create and remove tags on ec2 resources](https://docs.ansible.com/ansible/latest/modules/ec2_tag_module.html#ec2-tag-module)
- [ec2_transit_gateway – Create and delete AWS Transit Gateways](https://docs.ansible.com/ansible/latest/modules/ec2_transit_gateway_module.html#ec2-transit-gateway-module)
- [ec2_transit_gateway_info – Gather information about ec2 transit gateways in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_transit_gateway_info_module.html#ec2-transit-gateway-info-module)
- [ec2_vol – create and attach a volume, return volume id and device map](https://docs.ansible.com/ansible/latest/modules/ec2_vol_module.html#ec2-vol-module)
- [ec2_vol_info – Gather information about ec2 volumes in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_vol_info_module.html#ec2-vol-info-module)
- [ec2_vpc_dhcp_option – Manages DHCP Options, and can ensure the DHCP options for the given VPC match what’s requested](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_dhcp_option_module.html#ec2-vpc-dhcp-option-module)
- [ec2_vpc_dhcp_option_info – Gather information about dhcp options sets in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_dhcp_option_info_module.html#ec2-vpc-dhcp-option-info-module)
- [ec2_vpc_egress_igw – Manage an AWS VPC Egress Only Internet gateway](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_egress_igw_module.html#ec2-vpc-egress-igw-module)
- [ec2_vpc_endpoint – Create and delete AWS VPC Endpoints](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_endpoint_module.html#ec2-vpc-endpoint-module)
- [ec2_vpc_endpoint_info – Retrieves AWS VPC endpoints details using AWS methods](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_endpoint_info_module.html#ec2-vpc-endpoint-info-module)
- [ec2_vpc_igw – Manage an AWS VPC Internet gateway](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_igw_module.html#ec2-vpc-igw-module)
- [ec2_vpc_igw_info – Gather information about internet gateways in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_igw_info_module.html#ec2-vpc-igw-info-module)
- [ec2_vpc_nacl – create and delete Network ACLs](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_nacl_module.html#ec2-vpc-nacl-module)
- [ec2_vpc_nacl_info – Gather information about Network ACLs in an AWS VPC](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_nacl_info_module.html#ec2-vpc-nacl-info-module)
- [ec2_vpc_nat_gateway – Manage AWS VPC NAT Gateways](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_nat_gateway_module.html#ec2-vpc-nat-gateway-module)
- [ec2_vpc_nat_gateway_info – Retrieves AWS VPC Managed Nat Gateway details using AWS methods](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_nat_gateway_info_module.html#ec2-vpc-nat-gateway-info-module)
- [ec2_vpc_net – Configure AWS virtual private clouds](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_net_module.html#ec2-vpc-net-module)
- [ec2_vpc_net_info – Gather information about ec2 VPCs in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_net_info_module.html#ec2-vpc-net-info-module)
- [ec2_vpc_peer – create, delete, accept, and reject VPC peering connections between two VPCs](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_peer_module.html#ec2-vpc-peer-module)
- [ec2_vpc_peering_info – Retrieves AWS VPC Peering details using AWS methods](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_peering_info_module.html#ec2-vpc-peering-info-module)
- [ec2_vpc_route_table – Manage route tables for AWS virtual private clouds](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_route_table_module.html#ec2-vpc-route-table-module)
- [ec2_vpc_route_table_info – Gather information about ec2 VPC route tables in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_route_table_info_module.html#ec2-vpc-route-table-info-module)
- [ec2_vpc_subnet – Manage subnets in AWS virtual private clouds](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_subnet_module.html#ec2-vpc-subnet-module)
- [ec2_vpc_subnet_info – Gather information about ec2 VPC subnets in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_subnet_info_module.html#ec2-vpc-subnet-info-module)
- [ec2_vpc_vgw – Create and delete AWS VPN Virtual Gateways](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_vgw_module.html#ec2-vpc-vgw-module)
- [ec2_vpc_vgw_info – Gather information about virtual gateways in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_vgw_info_module.html#ec2-vpc-vgw-info-module)
- [ec2_vpc_vpn – Create, modify, and delete EC2 VPN connections](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_vpn_module.html#ec2-vpc-vpn-module)
- [ec2_vpc_vpn_info – Gather information about VPN Connections in AWS](https://docs.ansible.com/ansible/latest/modules/ec2_vpc_vpn_info_module.html#ec2-vpc-vpn-info-module)
- [ec2_win_password – gets the default administrator password for ec2 windows instances](https://docs.ansible.com/ansible/latest/modules/ec2_win_password_module.html#ec2-win-password-module)
- [ecs_attribute – manage ecs attributes](https://docs.ansible.com/ansible/latest/modules/ecs_attribute_module.html#ecs-attribute-module)
- [ecs_cluster – create or terminate ecs clusters](https://docs.ansible.com/ansible/latest/modules/ecs_cluster_module.html#ecs-cluster-module)
- [ecs_ecr – Manage Elastic Container Registry repositories](https://docs.ansible.com/ansible/latest/modules/ecs_ecr_module.html#ecs-ecr-module)
- [ecs_service – create, terminate, start or stop a service in ecs](https://docs.ansible.com/ansible/latest/modules/ecs_service_module.html#ecs-service-module)
- [ecs_service_info – list or describe services in ecs](https://docs.ansible.com/ansible/latest/modules/ecs_service_info_module.html#ecs-service-info-module)
- [ecs_task – run, start or stop a task in ecs](https://docs.ansible.com/ansible/latest/modules/ecs_task_module.html#ecs-task-module)
- [ecs_taskdefinition – register a task definition in ecs](https://docs.ansible.com/ansible/latest/modules/ecs_taskdefinition_module.html#ecs-taskdefinition-module)
- [ecs_taskdefinition_info – describe a task definition in ecs](https://docs.ansible.com/ansible/latest/modules/ecs_taskdefinition_info_module.html#ecs-taskdefinition-info-module)
- [efs – create and maintain EFS file systems](https://docs.ansible.com/ansible/latest/modules/efs_module.html#efs-module)
- [efs_info – Get information about Amazon EFS file systems](https://docs.ansible.com/ansible/latest/modules/efs_info_module.html#efs-info-module)
- [elasticache – Manage cache clusters in Amazon Elasticache](https://docs.ansible.com/ansible/latest/modules/elasticache_module.html#elasticache-module)
- [elasticache_info – Retrieve information for AWS Elasticache clusters](https://docs.ansible.com/ansible/latest/modules/elasticache_info_module.html#elasticache-info-module)
- [elasticache_parameter_group – Manage cache security groups in Amazon Elasticache](https://docs.ansible.com/ansible/latest/modules/elasticache_parameter_group_module.html#elasticache-parameter-group-module)
- [elasticache_snapshot – Manage cache snapshots in Amazon Elasticache](https://docs.ansible.com/ansible/latest/modules/elasticache_snapshot_module.html#elasticache-snapshot-module)
- [elasticache_subnet_group – manage Elasticache subnet groups](https://docs.ansible.com/ansible/latest/modules/elasticache_subnet_group_module.html#elasticache-subnet-group-module)
- [elb_application_lb – Manage an Application load balancer](https://docs.ansible.com/ansible/latest/modules/elb_application_lb_module.html#elb-application-lb-module)
- [elb_application_lb_info – Gather information about application ELBs in AWS](https://docs.ansible.com/ansible/latest/modules/elb_application_lb_info_module.html#elb-application-lb-info-module)
- [elb_classic_lb – Creates or destroys Amazon ELB](https://docs.ansible.com/ansible/latest/modules/elb_classic_lb_module.html#elb-classic-lb-module)
- [elb_classic_lb_info – Gather information about EC2 Elastic Load Balancers in AWS](https://docs.ansible.com/ansible/latest/modules/elb_classic_lb_info_module.html#elb-classic-lb-info-module)
- [elb_instance – De-registers or registers instances from EC2 ELBs](https://docs.ansible.com/ansible/latest/modules/elb_instance_module.html#elb-instance-module)
- [elb_network_lb – Manage a Network Load Balancer](https://docs.ansible.com/ansible/latest/modules/elb_network_lb_module.html#elb-network-lb-module)
- [elb_target – Manage a target in a target group](https://docs.ansible.com/ansible/latest/modules/elb_target_module.html#elb-target-module)
- [elb_target_group – Manage a target group for an Application or Network load balancer](https://docs.ansible.com/ansible/latest/modules/elb_target_group_module.html#elb-target-group-module)
- [elb_target_group_info – Gather information about ELB target groups in AWS](https://docs.ansible.com/ansible/latest/modules/elb_target_group_info_module.html#elb-target-group-info-module)
- [elb_target_info – Gathers which target groups a target is associated with](https://docs.ansible.com/ansible/latest/modules/elb_target_info_module.html#elb-target-info-module)
- [execute_lambda – Execute an AWS Lambda function](https://docs.ansible.com/ansible/latest/modules/execute_lambda_module.html#execute-lambda-module)
- [iam – Manage IAM users, groups, roles and keys](https://docs.ansible.com/ansible/latest/modules/iam_module.html#iam-module)
- [iam_cert – Manage server certificates for use on ELBs and CloudFront](https://docs.ansible.com/ansible/latest/modules/iam_cert_module.html#iam-cert-module)
- [iam_group – Manage AWS IAM groups](https://docs.ansible.com/ansible/latest/modules/iam_group_module.html#iam-group-module)
- [iam_managed_policy – Manage User Managed IAM policies](https://docs.ansible.com/ansible/latest/modules/iam_managed_policy_module.html#iam-managed-policy-module)
- [iam_mfa_device_info – List the MFA (Multi-Factor Authentication) devices registered for a user](https://docs.ansible.com/ansible/latest/modules/iam_mfa_device_info_module.html#iam-mfa-device-info-module)
- [iam_password_policy – Update an IAM Password Policy](https://docs.ansible.com/ansible/latest/modules/iam_password_policy_module.html#iam-password-policy-module)
- [iam_policy – Manage IAM policies for users, groups, and roles](https://docs.ansible.com/ansible/latest/modules/iam_policy_module.html#iam-policy-module)
- [iam_role – Manage AWS IAM roles](https://docs.ansible.com/ansible/latest/modules/iam_role_module.html#iam-role-module)
- [iam_role_info – Gather information on IAM roles](https://docs.ansible.com/ansible/latest/modules/iam_role_info_module.html#iam-role-info-module)
- [iam_server_certificate_info – Retrieve the information of a server certificate](https://docs.ansible.com/ansible/latest/modules/iam_server_certificate_info_module.html#iam-server-certificate-info-module)
- [iam_user – Manage AWS IAM users](https://docs.ansible.com/ansible/latest/modules/iam_user_module.html#iam-user-module)
- [kinesis_stream – Manage a Kinesis Stream](https://docs.ansible.com/ansible/latest/modules/kinesis_stream_module.html#kinesis-stream-module)
- [lambda – Manage AWS Lambda functions](https://docs.ansible.com/ansible/latest/modules/lambda_module.html#lambda-module)
- [lambda_alias – Creates, updates or deletes AWS Lambda function aliases](https://docs.ansible.com/ansible/latest/modules/lambda_alias_module.html#lambda-alias-module)
- [lambda_event – Creates, updates or deletes AWS Lambda function event mappings](https://docs.ansible.com/ansible/latest/modules/lambda_event_module.html#lambda-event-module)
- [lambda_facts – Gathers AWS Lambda function details as Ansible facts](https://docs.ansible.com/ansible/latest/modules/lambda_facts_module.html#lambda-facts-module) **(D)**
- [lambda_info – Gathers AWS Lambda function details](https://docs.ansible.com/ansible/latest/modules/lambda_info_module.html#lambda-info-module)
- [lambda_policy – Creates, updates or deletes AWS Lambda policy statements](https://docs.ansible.com/ansible/latest/modules/lambda_policy_module.html#lambda-policy-module)
- [lightsail – Create or delete a virtual machine instance in AWS Lightsail](https://docs.ansible.com/ansible/latest/modules/lightsail_module.html#lightsail-module)
- [rds – create, delete, or modify Amazon rds instances, rds snapshots, and related facts](https://docs.ansible.com/ansible/latest/modules/rds_module.html#rds-module)
- [rds_instance – Manage RDS instances](https://docs.ansible.com/ansible/latest/modules/rds_instance_module.html#rds-instance-module)
- [rds_instance_info – obtain information about one or more RDS instances](https://docs.ansible.com/ansible/latest/modules/rds_instance_info_module.html#rds-instance-info-module)
- [rds_param_group – manage RDS parameter groups](https://docs.ansible.com/ansible/latest/modules/rds_param_group_module.html#rds-param-group-module)
- [rds_snapshot – manage Amazon RDS snapshots](https://docs.ansible.com/ansible/latest/modules/rds_snapshot_module.html#rds-snapshot-module)
- [rds_snapshot_info – obtain information about one or more RDS snapshots](https://docs.ansible.com/ansible/latest/modules/rds_snapshot_info_module.html#rds-snapshot-info-module)
- [rds_subnet_group – manage RDS database subnet groups](https://docs.ansible.com/ansible/latest/modules/rds_subnet_group_module.html#rds-subnet-group-module)
- [redshift – create, delete, or modify an Amazon Redshift instance](https://docs.ansible.com/ansible/latest/modules/redshift_module.html#redshift-module)
- [redshift_cross_region_snapshots – Manage Redshift Cross Region Snapshots](https://docs.ansible.com/ansible/latest/modules/redshift_cross_region_snapshots_module.html#redshift-cross-region-snapshots-module)
- [redshift_info – Gather information about Redshift cluster(s)](https://docs.ansible.com/ansible/latest/modules/redshift_info_module.html#redshift-info-module)
- [redshift_subnet_group – manage Redshift cluster subnet groups](https://docs.ansible.com/ansible/latest/modules/redshift_subnet_group_module.html#redshift-subnet-group-module)
- [route53 – add or delete entries in Amazons Route53 DNS service](https://docs.ansible.com/ansible/latest/modules/route53_module.html#route53-module)
- [route53_health_check – add or delete health-checks in Amazons Route53 DNS service](https://docs.ansible.com/ansible/latest/modules/route53_health_check_module.html#route53-health-check-module)
- [route53_info – Retrieves route53 details using AWS methods](https://docs.ansible.com/ansible/latest/modules/route53_info_module.html#route53-info-module)
- [route53_zone – add or delete Route53 zones](https://docs.ansible.com/ansible/latest/modules/route53_zone_module.html#route53-zone-module)
- [s3_bucket – Manage S3 buckets in AWS, DigitalOcean, Ceph, Walrus and FakeS3](https://docs.ansible.com/ansible/latest/modules/s3_bucket_module.html#s3-bucket-module)
- [s3_bucket_notification – Creates, updates or deletes S3 Bucket notification for lambda](https://docs.ansible.com/ansible/latest/modules/s3_bucket_notification_module.html#s3-bucket-notification-module)
- [s3_lifecycle – Manage s3 bucket lifecycle rules in AWS](https://docs.ansible.com/ansible/latest/modules/s3_lifecycle_module.html#s3-lifecycle-module)
- [s3_logging – Manage logging facility of an s3 bucket in AWS](https://docs.ansible.com/ansible/latest/modules/s3_logging_module.html#s3-logging-module)
- [s3_sync – Efficiently upload multiple files to S3](https://docs.ansible.com/ansible/latest/modules/s3_sync_module.html#s3-sync-module)
- [s3_website – Configure an s3 bucket as a website](https://docs.ansible.com/ansible/latest/modules/s3_website_module.html#s3-website-module)
- [sns – Send Amazon Simple Notification Service messages](https://docs.ansible.com/ansible/latest/modules/sns_module.html#sns-module)
- [sns_topic – Manages AWS SNS topics and subscriptions](https://docs.ansible.com/ansible/latest/modules/sns_topic_module.html#sns-topic-module)
- [sqs_queue – Creates or deletes AWS SQS queues](https://docs.ansible.com/ansible/latest/modules/sqs_queue_module.html#sqs-queue-module)
- [sts_assume_role – Assume a role using AWS Security Token Service and obtain temporary credentials](https://docs.ansible.com/ansible/latest/modules/sts_assume_role_module.html#sts-assume-role-module)
- [sts_session_token – Obtain a session token from the AWS Security Token Service](https://docs.ansible.com/ansible/latest/modules/sts_session_token_module.html#sts-session-token-module)



### Atomic

- [atomic_container – Manage the containers on the atomic host platform](https://docs.ansible.com/ansible/latest/modules/atomic_container_module.html#atomic-container-module)
- [atomic_host – Manage the atomic host platform](https://docs.ansible.com/ansible/latest/modules/atomic_host_module.html#atomic-host-module)
- [atomic_image – Manage the container images on the atomic host platform](https://docs.ansible.com/ansible/latest/modules/atomic_image_module.html#atomic-image-module)



### Azure

- [azure_rm_acs – Manage an Azure Container Service(ACS) instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_acs_module.html#azure-rm-acs-module)
- [azure_rm_aks – Manage a managed Azure Container Service (AKS) instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_aks_module.html#azure-rm-aks-module)
- [azure_rm_aks_info – Get Azure Kubernetes Service facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_aks_info_module.html#azure-rm-aks-info-module)
- [azure_rm_aksversion_info – Get available kubernetes versions supported by Azure Kubernetes Service](https://docs.ansible.com/ansible/latest/modules/azure_rm_aksversion_info_module.html#azure-rm-aksversion-info-module)
- [azure_rm_appgateway – Manage Application Gateway instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_appgateway_module.html#azure-rm-appgateway-module)
- [azure_rm_applicationsecuritygroup – Manage Azure Application Security Group](https://docs.ansible.com/ansible/latest/modules/azure_rm_applicationsecuritygroup_module.html#azure-rm-applicationsecuritygroup-module)
- [azure_rm_applicationsecuritygroup_info – Get Azure Application Security Group facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_applicationsecuritygroup_info_module.html#azure-rm-applicationsecuritygroup-info-module)
- [azure_rm_appserviceplan – Manage App Service Plan](https://docs.ansible.com/ansible/latest/modules/azure_rm_appserviceplan_module.html#azure-rm-appserviceplan-module)
- [azure_rm_appserviceplan_info – Get azure app service plan facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_appserviceplan_info_module.html#azure-rm-appserviceplan-info-module)
- [azure_rm_automationaccount – Manage Azure Automation account](https://docs.ansible.com/ansible/latest/modules/azure_rm_automationaccount_module.html#azure-rm-automationaccount-module)
- [azure_rm_automationaccount_info – Get Azure automation account facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_automationaccount_info_module.html#azure-rm-automationaccount-info-module)
- [azure_rm_autoscale – Manage Azure autoscale setting](https://docs.ansible.com/ansible/latest/modules/azure_rm_autoscale_module.html#azure-rm-autoscale-module)
- [azure_rm_autoscale_info – Get Azure Auto Scale Setting facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_autoscale_info_module.html#azure-rm-autoscale-info-module)
- [azure_rm_availabilityset – Manage Azure Availability Set](https://docs.ansible.com/ansible/latest/modules/azure_rm_availabilityset_module.html#azure-rm-availabilityset-module)
- [azure_rm_availabilityset_info – Get Azure Availability Set facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_availabilityset_info_module.html#azure-rm-availabilityset-info-module)
- [azure_rm_azurefirewall – Manage Azure Firewall instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_azurefirewall_module.html#azure-rm-azurefirewall-module)
- [azure_rm_azurefirewall_info – Get AzureFirewall info](https://docs.ansible.com/ansible/latest/modules/azure_rm_azurefirewall_info_module.html#azure-rm-azurefirewall-info-module)
- [azure_rm_batchaccount – Manages a Batch Account on Azure](https://docs.ansible.com/ansible/latest/modules/azure_rm_batchaccount_module.html#azure-rm-batchaccount-module)
- [azure_rm_cdnendpoint – Manage a Azure CDN endpoint](https://docs.ansible.com/ansible/latest/modules/azure_rm_cdnendpoint_module.html#azure-rm-cdnendpoint-module)
- [azure_rm_cdnendpoint_info – Get Azure CDN endpoint facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_cdnendpoint_info_module.html#azure-rm-cdnendpoint-info-module)
- [azure_rm_cdnprofile – Manage a Azure CDN profile](https://docs.ansible.com/ansible/latest/modules/azure_rm_cdnprofile_module.html#azure-rm-cdnprofile-module)
- [azure_rm_cdnprofile_info – Get Azure CDN profile facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_cdnprofile_info_module.html#azure-rm-cdnprofile-info-module)
- [azure_rm_containerinstance – Manage an Azure Container Instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_containerinstance_module.html#azure-rm-containerinstance-module)
- [azure_rm_containerinstance_info – Get Azure Container Instance facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_containerinstance_info_module.html#azure-rm-containerinstance-info-module)
- [azure_rm_containerregistry – Manage an Azure Container Registry](https://docs.ansible.com/ansible/latest/modules/azure_rm_containerregistry_module.html#azure-rm-containerregistry-module)
- [azure_rm_containerregistry_info – Get Azure Container Registry facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_containerregistry_info_module.html#azure-rm-containerregistry-info-module)
- [azure_rm_cosmosdbaccount – Manage Azure Database Account instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_cosmosdbaccount_module.html#azure-rm-cosmosdbaccount-module)
- [azure_rm_cosmosdbaccount_info – Get Azure Cosmos DB Account facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_cosmosdbaccount_info_module.html#azure-rm-cosmosdbaccount-info-module)
- [azure_rm_deployment – Create or destroy Azure Resource Manager template deployments](https://docs.ansible.com/ansible/latest/modules/azure_rm_deployment_module.html#azure-rm-deployment-module)
- [azure_rm_deployment_info – Get Azure Deployment facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_deployment_info_module.html#azure-rm-deployment-info-module)
- [azure_rm_devtestlab – Manage Azure DevTest Lab instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlab_module.html#azure-rm-devtestlab-module)
- [azure_rm_devtestlab_info – Get Azure DevTest Lab facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlab_info_module.html#azure-rm-devtestlab-info-module)
- [azure_rm_devtestlabarmtemplate_info – Get Azure DevTest Lab ARM Template facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabarmtemplate_info_module.html#azure-rm-devtestlabarmtemplate-info-module)
- [azure_rm_devtestlabartifact_info – Get Azure DevTest Lab Artifact facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabartifact_info_module.html#azure-rm-devtestlabartifact-info-module)
- [azure_rm_devtestlabartifactsource – Manage Azure DevTest Labs Artifacts Source instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabartifactsource_module.html#azure-rm-devtestlabartifactsource-module)
- [azure_rm_devtestlabartifactsource_info – Get Azure DevTest Lab Artifact Source facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabartifactsource_info_module.html#azure-rm-devtestlabartifactsource-info-module)
- [azure_rm_devtestlabcustomimage – Manage Azure DevTest Lab Custom Image instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabcustomimage_module.html#azure-rm-devtestlabcustomimage-module)
- [azure_rm_devtestlabcustomimage_info – Get Azure DevTest Lab Custom Image facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabcustomimage_info_module.html#azure-rm-devtestlabcustomimage-info-module)
- [azure_rm_devtestlabenvironment – Manage Azure DevTest Lab Environment instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabenvironment_module.html#azure-rm-devtestlabenvironment-module)
- [azure_rm_devtestlabenvironment_info – Get Azure Environment facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabenvironment_info_module.html#azure-rm-devtestlabenvironment-info-module)
- [azure_rm_devtestlabpolicy – Manage Azure Policy instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabpolicy_module.html#azure-rm-devtestlabpolicy-module)
- [azure_rm_devtestlabpolicy_info – Get Azure DTL Policy facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabpolicy_info_module.html#azure-rm-devtestlabpolicy-info-module)
- [azure_rm_devtestlabschedule – Manage Azure DevTest Lab Schedule instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabschedule_module.html#azure-rm-devtestlabschedule-module)
- [azure_rm_devtestlabschedule_info – Get Azure Schedule facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabschedule_info_module.html#azure-rm-devtestlabschedule-info-module)
- [azure_rm_devtestlabvirtualmachine – Manage Azure DevTest Lab Virtual Machine instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabvirtualmachine_module.html#azure-rm-devtestlabvirtualmachine-module)
- [azure_rm_devtestlabvirtualmachine_info – Get Azure DevTest Lab Virtual Machine facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabvirtualmachine_info_module.html#azure-rm-devtestlabvirtualmachine-info-module)
- [azure_rm_devtestlabvirtualnetwork – Manage Azure DevTest Lab Virtual Network instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabvirtualnetwork_module.html#azure-rm-devtestlabvirtualnetwork-module)
- [azure_rm_devtestlabvirtualnetwork_info – Get Azure DevTest Lab Virtual Network facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_devtestlabvirtualnetwork_info_module.html#azure-rm-devtestlabvirtualnetwork-info-module)
- [azure_rm_dnsrecordset – Create, delete and update DNS record sets and records](https://docs.ansible.com/ansible/latest/modules/azure_rm_dnsrecordset_module.html#azure-rm-dnsrecordset-module)
- [azure_rm_dnsrecordset_info – Get DNS Record Set facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_dnsrecordset_info_module.html#azure-rm-dnsrecordset-info-module)
- [azure_rm_dnszone – Manage Azure DNS zones](https://docs.ansible.com/ansible/latest/modules/azure_rm_dnszone_module.html#azure-rm-dnszone-module)
- [azure_rm_dnszone_info – Get DNS zone facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_dnszone_info_module.html#azure-rm-dnszone-info-module)
- [azure_rm_functionapp – Manage Azure Function Apps](https://docs.ansible.com/ansible/latest/modules/azure_rm_functionapp_module.html#azure-rm-functionapp-module)
- [azure_rm_functionapp_info – Get Azure Function App facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_functionapp_info_module.html#azure-rm-functionapp-info-module)
- [azure_rm_gallery – Manage Azure Shared Image Gallery instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_gallery_module.html#azure-rm-gallery-module)
- [azure_rm_gallery_info – Get Azure Shared Image Gallery info](https://docs.ansible.com/ansible/latest/modules/azure_rm_gallery_info_module.html#azure-rm-gallery-info-module)
- [azure_rm_galleryimage – Manage Azure SIG Image instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_galleryimage_module.html#azure-rm-galleryimage-module)
- [azure_rm_galleryimage_info – Get Azure SIG Image info](https://docs.ansible.com/ansible/latest/modules/azure_rm_galleryimage_info_module.html#azure-rm-galleryimage-info-module)
- [azure_rm_galleryimageversion – Manage Azure SIG Image Version instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_galleryimageversion_module.html#azure-rm-galleryimageversion-module)
- [azure_rm_galleryimageversion_info – Get Azure SIG Image Version info](https://docs.ansible.com/ansible/latest/modules/azure_rm_galleryimageversion_info_module.html#azure-rm-galleryimageversion-info-module)
- [azure_rm_hdinsightcluster – Manage Azure HDInsight Cluster instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_hdinsightcluster_module.html#azure-rm-hdinsightcluster-module)
- [azure_rm_hdinsightcluster_info – Get Azure HDInsight Cluster facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_hdinsightcluster_info_module.html#azure-rm-hdinsightcluster-info-module)
- [azure_rm_image – Manage Azure image](https://docs.ansible.com/ansible/latest/modules/azure_rm_image_module.html#azure-rm-image-module)
- [azure_rm_image_info – Get facts about azure custom images](https://docs.ansible.com/ansible/latest/modules/azure_rm_image_info_module.html#azure-rm-image-info-module)
- [azure_rm_iotdevice – Manage Azure IoT hub device](https://docs.ansible.com/ansible/latest/modules/azure_rm_iotdevice_module.html#azure-rm-iotdevice-module)
- [azure_rm_iotdevice_info – Facts of Azure IoT hub device](https://docs.ansible.com/ansible/latest/modules/azure_rm_iotdevice_info_module.html#azure-rm-iotdevice-info-module)
- [azure_rm_iotdevicemodule – Manage Azure IoT hub device module](https://docs.ansible.com/ansible/latest/modules/azure_rm_iotdevicemodule_module.html#azure-rm-iotdevicemodule-module)
- [azure_rm_iothub – Manage Azure IoT hub](https://docs.ansible.com/ansible/latest/modules/azure_rm_iothub_module.html#azure-rm-iothub-module)
- [azure_rm_iothub_info – Get IoT Hub facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_iothub_info_module.html#azure-rm-iothub-info-module)
- [azure_rm_iothubconsumergroup – Manage Azure IoT hub](https://docs.ansible.com/ansible/latest/modules/azure_rm_iothubconsumergroup_module.html#azure-rm-iothubconsumergroup-module)
- [azure_rm_keyvault – Manage Key Vault instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_keyvault_module.html#azure-rm-keyvault-module)
- [azure_rm_keyvault_info – Get Azure Key Vault facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_keyvault_info_module.html#azure-rm-keyvault-info-module)
- [azure_rm_keyvaultkey – Use Azure KeyVault keys](https://docs.ansible.com/ansible/latest/modules/azure_rm_keyvaultkey_module.html#azure-rm-keyvaultkey-module)
- [azure_rm_keyvaultkey_info – Get Azure Key Vault key facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_keyvaultkey_info_module.html#azure-rm-keyvaultkey-info-module)
- [azure_rm_keyvaultsecret – Use Azure KeyVault Secrets](https://docs.ansible.com/ansible/latest/modules/azure_rm_keyvaultsecret_module.html#azure-rm-keyvaultsecret-module)
- [azure_rm_loadbalancer – Manage Azure load balancers](https://docs.ansible.com/ansible/latest/modules/azure_rm_loadbalancer_module.html#azure-rm-loadbalancer-module)
- [azure_rm_loadbalancer_info – Get load balancer facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_loadbalancer_info_module.html#azure-rm-loadbalancer-info-module)
- [azure_rm_lock – Manage Azure locks](https://docs.ansible.com/ansible/latest/modules/azure_rm_lock_module.html#azure-rm-lock-module)
- [azure_rm_lock_info – Manage Azure locks](https://docs.ansible.com/ansible/latest/modules/azure_rm_lock_info_module.html#azure-rm-lock-info-module)
- [azure_rm_loganalyticsworkspace – Manage Azure Log Analytics workspaces](https://docs.ansible.com/ansible/latest/modules/azure_rm_loganalyticsworkspace_module.html#azure-rm-loganalyticsworkspace-module)
- [azure_rm_loganalyticsworkspace_info – Get facts of Azure Log Analytics workspaces](https://docs.ansible.com/ansible/latest/modules/azure_rm_loganalyticsworkspace_info_module.html#azure-rm-loganalyticsworkspace-info-module)
- [azure_rm_manageddisk – Manage Azure Manage Disks](https://docs.ansible.com/ansible/latest/modules/azure_rm_manageddisk_module.html#azure-rm-manageddisk-module)
- [azure_rm_manageddisk_info – Get managed disk facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_manageddisk_info_module.html#azure-rm-manageddisk-info-module)
- [azure_rm_mariadbconfiguration – Manage Configuration instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_mariadbconfiguration_module.html#azure-rm-mariadbconfiguration-module)
- [azure_rm_mariadbconfiguration_info – Get Azure MariaDB Configuration facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_mariadbconfiguration_info_module.html#azure-rm-mariadbconfiguration-info-module)
- [azure_rm_mariadbdatabase – Manage MariaDB Database instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_mariadbdatabase_module.html#azure-rm-mariadbdatabase-module)
- [azure_rm_mariadbdatabase_info – Get Azure MariaDB Database facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_mariadbdatabase_info_module.html#azure-rm-mariadbdatabase-info-module)
- [azure_rm_mariadbfirewallrule – Manage MariaDB firewall rule instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_mariadbfirewallrule_module.html#azure-rm-mariadbfirewallrule-module)
- [azure_rm_mariadbfirewallrule_info – Get Azure MariaDB Firewall Rule facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_mariadbfirewallrule_info_module.html#azure-rm-mariadbfirewallrule-info-module)
- [azure_rm_mariadbserver – Manage MariaDB Server instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_mariadbserver_module.html#azure-rm-mariadbserver-module)
- [azure_rm_mariadbserver_info – Get Azure MariaDB Server facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_mariadbserver_info_module.html#azure-rm-mariadbserver-info-module)
- [azure_rm_monitorlogprofile – Manage Azure Monitor log profile](https://docs.ansible.com/ansible/latest/modules/azure_rm_monitorlogprofile_module.html#azure-rm-monitorlogprofile-module)
- [azure_rm_mysqlconfiguration – Manage Configuration instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_mysqlconfiguration_module.html#azure-rm-mysqlconfiguration-module)
- [azure_rm_mysqlconfiguration_info – Get Azure MySQL Configuration facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_mysqlconfiguration_info_module.html#azure-rm-mysqlconfiguration-info-module)
- [azure_rm_mysqldatabase – Manage MySQL Database instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_mysqldatabase_module.html#azure-rm-mysqldatabase-module)
- [azure_rm_mysqldatabase_info – Get Azure MySQL Database facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_mysqldatabase_info_module.html#azure-rm-mysqldatabase-info-module)
- [azure_rm_mysqlfirewallrule – Manage MySQL firewall rule instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_mysqlfirewallrule_module.html#azure-rm-mysqlfirewallrule-module)
- [azure_rm_mysqlfirewallrule_info – Get Azure MySQL Firewall Rule facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_mysqlfirewallrule_info_module.html#azure-rm-mysqlfirewallrule-info-module)
- [azure_rm_mysqlserver – Manage MySQL Server instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_mysqlserver_module.html#azure-rm-mysqlserver-module)
- [azure_rm_mysqlserver_info – Get Azure MySQL Server facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_mysqlserver_info_module.html#azure-rm-mysqlserver-info-module)
- [azure_rm_networkinterface – Manage Azure network interfaces](https://docs.ansible.com/ansible/latest/modules/azure_rm_networkinterface_module.html#azure-rm-networkinterface-module)
- [azure_rm_networkinterface_info – Get network interface facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_networkinterface_info_module.html#azure-rm-networkinterface-info-module)
- [azure_rm_postgresqlconfiguration – Manage Azure PostgreSQL Configuration](https://docs.ansible.com/ansible/latest/modules/azure_rm_postgresqlconfiguration_module.html#azure-rm-postgresqlconfiguration-module)
- [azure_rm_postgresqlconfiguration_info – Get Azure PostgreSQL Configuration facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_postgresqlconfiguration_info_module.html#azure-rm-postgresqlconfiguration-info-module)
- [azure_rm_postgresqldatabase – Manage PostgreSQL Database instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_postgresqldatabase_module.html#azure-rm-postgresqldatabase-module)
- [azure_rm_postgresqldatabase_info – Get Azure PostgreSQL Database facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_postgresqldatabase_info_module.html#azure-rm-postgresqldatabase-info-module)
- [azure_rm_postgresqlfirewallrule – Manage PostgreSQL firewall rule instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_postgresqlfirewallrule_module.html#azure-rm-postgresqlfirewallrule-module)
- [azure_rm_postgresqlfirewallrule_info – Get Azure PostgreSQL Firewall Rule facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_postgresqlfirewallrule_info_module.html#azure-rm-postgresqlfirewallrule-info-module)
- [azure_rm_postgresqlserver – Manage PostgreSQL Server instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_postgresqlserver_module.html#azure-rm-postgresqlserver-module)
- [azure_rm_postgresqlserver_info – Get Azure PostgreSQL Server facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_postgresqlserver_info_module.html#azure-rm-postgresqlserver-info-module)
- [azure_rm_publicipaddress – Manage Azure Public IP Addresses](https://docs.ansible.com/ansible/latest/modules/azure_rm_publicipaddress_module.html#azure-rm-publicipaddress-module)
- [azure_rm_publicipaddress_info – Get public IP facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_publicipaddress_info_module.html#azure-rm-publicipaddress-info-module)
- [azure_rm_rediscache – Manage Azure Cache for Redis instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_rediscache_module.html#azure-rm-rediscache-module)
- [azure_rm_rediscache_info – Get Azure Cache for Redis instance facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_rediscache_info_module.html#azure-rm-rediscache-info-module)
- [azure_rm_rediscachefirewallrule – Manage Azure Cache for Redis Firewall rules](https://docs.ansible.com/ansible/latest/modules/azure_rm_rediscachefirewallrule_module.html#azure-rm-rediscachefirewallrule-module)
- [azure_rm_resource – Create any Azure resource](https://docs.ansible.com/ansible/latest/modules/azure_rm_resource_module.html#azure-rm-resource-module)
- [azure_rm_resource_info – Generic facts of Azure resources](https://docs.ansible.com/ansible/latest/modules/azure_rm_resource_info_module.html#azure-rm-resource-info-module)
- [azure_rm_resourcegroup – Manage Azure resource groups](https://docs.ansible.com/ansible/latest/modules/azure_rm_resourcegroup_module.html#azure-rm-resourcegroup-module)
- [azure_rm_resourcegroup_info – Get resource group facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_resourcegroup_info_module.html#azure-rm-resourcegroup-info-module)
- [azure_rm_roleassignment – Manage Azure Role Assignment](https://docs.ansible.com/ansible/latest/modules/azure_rm_roleassignment_module.html#azure-rm-roleassignment-module)
- [azure_rm_roleassignment_info – Gets Azure Role Assignment facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_roleassignment_info_module.html#azure-rm-roleassignment-info-module)
- [azure_rm_roledefinition – Manage Azure Role Definition](https://docs.ansible.com/ansible/latest/modules/azure_rm_roledefinition_module.html#azure-rm-roledefinition-module)
- [azure_rm_roledefinition_info – Get Azure Role Definition facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_roledefinition_info_module.html#azure-rm-roledefinition-info-module)
- [azure_rm_route – Manage Azure route resource](https://docs.ansible.com/ansible/latest/modules/azure_rm_route_module.html#azure-rm-route-module)
- [azure_rm_routetable – Manage Azure route table resource](https://docs.ansible.com/ansible/latest/modules/azure_rm_routetable_module.html#azure-rm-routetable-module)
- [azure_rm_routetable_info – Get route table facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_routetable_info_module.html#azure-rm-routetable-info-module)
- [azure_rm_securitygroup – Manage Azure network security groups](https://docs.ansible.com/ansible/latest/modules/azure_rm_securitygroup_module.html#azure-rm-securitygroup-module)
- [azure_rm_securitygroup_info – Get security group facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_securitygroup_info_module.html#azure-rm-securitygroup-info-module)
- [azure_rm_servicebus – Manage Azure Service Bus](https://docs.ansible.com/ansible/latest/modules/azure_rm_servicebus_module.html#azure-rm-servicebus-module)
- [azure_rm_servicebus_info – Get servicebus facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_servicebus_info_module.html#azure-rm-servicebus-info-module)
- [azure_rm_servicebusqueue – Manage Azure Service Bus queue](https://docs.ansible.com/ansible/latest/modules/azure_rm_servicebusqueue_module.html#azure-rm-servicebusqueue-module)
- [azure_rm_servicebussaspolicy – Manage Azure Service Bus SAS policy](https://docs.ansible.com/ansible/latest/modules/azure_rm_servicebussaspolicy_module.html#azure-rm-servicebussaspolicy-module)
- [azure_rm_servicebustopic – Manage Azure Service Bus](https://docs.ansible.com/ansible/latest/modules/azure_rm_servicebustopic_module.html#azure-rm-servicebustopic-module)
- [azure_rm_servicebustopicsubscription – Manage Azure Service Bus subscription](https://docs.ansible.com/ansible/latest/modules/azure_rm_servicebustopicsubscription_module.html#azure-rm-servicebustopicsubscription-module)
- [azure_rm_snapshot – Manage Azure Snapshot instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_snapshot_module.html#azure-rm-snapshot-module)
- [azure_rm_sqldatabase – Manage SQL Database instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_sqldatabase_module.html#azure-rm-sqldatabase-module)
- [azure_rm_sqldatabase_info – Get Azure SQL Database facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_sqldatabase_info_module.html#azure-rm-sqldatabase-info-module)
- [azure_rm_sqlfirewallrule – Manage Firewall Rule instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_sqlfirewallrule_module.html#azure-rm-sqlfirewallrule-module)
- [azure_rm_sqlfirewallrule_info – Get Azure SQL Firewall Rule facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_sqlfirewallrule_info_module.html#azure-rm-sqlfirewallrule-info-module)
- [azure_rm_sqlserver – Manage SQL Server instance](https://docs.ansible.com/ansible/latest/modules/azure_rm_sqlserver_module.html#azure-rm-sqlserver-module)
- [azure_rm_sqlserver_info – Get SQL Server facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_sqlserver_info_module.html#azure-rm-sqlserver-info-module)
- [azure_rm_storageaccount – Manage Azure storage accounts](https://docs.ansible.com/ansible/latest/modules/azure_rm_storageaccount_module.html#azure-rm-storageaccount-module)
- [azure_rm_storageaccount_info – Get storage account facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_storageaccount_info_module.html#azure-rm-storageaccount-info-module)
- [azure_rm_storageblob – Manage blob containers and blob objects](https://docs.ansible.com/ansible/latest/modules/azure_rm_storageblob_module.html#azure-rm-storageblob-module)
- [azure_rm_subnet – Manage Azure subnets](https://docs.ansible.com/ansible/latest/modules/azure_rm_subnet_module.html#azure-rm-subnet-module)
- [azure_rm_subnet_info – Get Azure Subnet facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_subnet_info_module.html#azure-rm-subnet-info-module)
- [azure_rm_trafficmanagerendpoint – Manage Azure Traffic Manager endpoint](https://docs.ansible.com/ansible/latest/modules/azure_rm_trafficmanagerendpoint_module.html#azure-rm-trafficmanagerendpoint-module)
- [azure_rm_trafficmanagerendpoint_info – Get Azure Traffic Manager endpoint facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_trafficmanagerendpoint_info_module.html#azure-rm-trafficmanagerendpoint-info-module)
- [azure_rm_trafficmanagerprofile – Manage Azure Traffic Manager profile](https://docs.ansible.com/ansible/latest/modules/azure_rm_trafficmanagerprofile_module.html#azure-rm-trafficmanagerprofile-module)
- [azure_rm_trafficmanagerprofile_info – Get Azure Traffic Manager profile facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_trafficmanagerprofile_info_module.html#azure-rm-trafficmanagerprofile-info-module)
- [azure_rm_virtualmachine – Manage Azure virtual machines](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachine_module.html#azure-rm-virtualmachine-module)
- [azure_rm_virtualmachine_info – Get virtual machine facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachine_info_module.html#azure-rm-virtualmachine-info-module)
- [azure_rm_virtualmachineextension – Managed Azure Virtual Machine extension](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachineextension_module.html#azure-rm-virtualmachineextension-module)
- [azure_rm_virtualmachineextension_info – Get Azure Virtual Machine Extension facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachineextension_info_module.html#azure-rm-virtualmachineextension-info-module)
- [azure_rm_virtualmachineimage_info – Get virtual machine image facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachineimage_info_module.html#azure-rm-virtualmachineimage-info-module)
- [azure_rm_virtualmachinescaleset – Manage Azure virtual machine scale sets](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachinescaleset_module.html#azure-rm-virtualmachinescaleset-module)
- [azure_rm_virtualmachinescaleset_info – Get Virtual Machine Scale Set facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachinescaleset_info_module.html#azure-rm-virtualmachinescaleset-info-module)
- [azure_rm_virtualmachinescalesetextension – Manage Azure Virtual Machine Scale Set (VMSS) extensions](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachinescalesetextension_module.html#azure-rm-virtualmachinescalesetextension-module)
- [azure_rm_virtualmachinescalesetextension_info – Get Azure Virtual Machine Scale Set Extension facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachinescalesetextension_info_module.html#azure-rm-virtualmachinescalesetextension-info-module)
- [azure_rm_virtualmachinescalesetinstance – Get Azure Virtual Machine Scale Set Instance facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachinescalesetinstance_module.html#azure-rm-virtualmachinescalesetinstance-module)
- [azure_rm_virtualmachinescalesetinstance_info – Get Azure Virtual Machine Scale Set Instance facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualmachinescalesetinstance_info_module.html#azure-rm-virtualmachinescalesetinstance-info-module)
- [azure_rm_virtualnetwork – Manage Azure virtual networks](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualnetwork_module.html#azure-rm-virtualnetwork-module)
- [azure_rm_virtualnetwork_info – Get virtual network facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualnetwork_info_module.html#azure-rm-virtualnetwork-info-module)
- [azure_rm_virtualnetworkgateway – Manage Azure virtual network gateways](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualnetworkgateway_module.html#azure-rm-virtualnetworkgateway-module)
- [azure_rm_virtualnetworkpeering – Manage Azure Virtual Network Peering](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualnetworkpeering_module.html#azure-rm-virtualnetworkpeering-module)
- [azure_rm_virtualnetworkpeering_info – Get facts of Azure Virtual Network Peering](https://docs.ansible.com/ansible/latest/modules/azure_rm_virtualnetworkpeering_info_module.html#azure-rm-virtualnetworkpeering-info-module)
- [azure_rm_webapp – Manage Web App instances](https://docs.ansible.com/ansible/latest/modules/azure_rm_webapp_module.html#azure-rm-webapp-module)
- [azure_rm_webapp_info – Get Azure web app facts](https://docs.ansible.com/ansible/latest/modules/azure_rm_webapp_info_module.html#azure-rm-webapp-info-module)
- [azure_rm_webappslot – Manage Azure Web App slot](https://docs.ansible.com/ansible/latest/modules/azure_rm_webappslot_module.html#azure-rm-webappslot-module)



### Centurylink

- [clc_aa_policy – Create or Delete Anti Affinity Policies at CenturyLink Cloud](https://docs.ansible.com/ansible/latest/modules/clc_aa_policy_module.html#clc-aa-policy-module)
- [clc_alert_policy – Create or Delete Alert Policies at CenturyLink Cloud](https://docs.ansible.com/ansible/latest/modules/clc_alert_policy_module.html#clc-alert-policy-module)
- [clc_blueprint_package – deploys a blue print package on a set of servers in CenturyLink Cloud](https://docs.ansible.com/ansible/latest/modules/clc_blueprint_package_module.html#clc-blueprint-package-module)
- [clc_firewall_policy – Create/delete/update firewall policies](https://docs.ansible.com/ansible/latest/modules/clc_firewall_policy_module.html#clc-firewall-policy-module)
- [clc_group – Create/delete Server Groups at Centurylink Cloud](https://docs.ansible.com/ansible/latest/modules/clc_group_module.html#clc-group-module)
- [clc_loadbalancer – Create, Delete shared loadbalancers in CenturyLink Cloud](https://docs.ansible.com/ansible/latest/modules/clc_loadbalancer_module.html#clc-loadbalancer-module)
- [clc_modify_server – modify servers in CenturyLink Cloud](https://docs.ansible.com/ansible/latest/modules/clc_modify_server_module.html#clc-modify-server-module)
- [clc_publicip – Add and Delete public ips on servers in CenturyLink Cloud](https://docs.ansible.com/ansible/latest/modules/clc_publicip_module.html#clc-publicip-module)
- [clc_server – Create, Delete, Start and Stop servers in CenturyLink Cloud](https://docs.ansible.com/ansible/latest/modules/clc_server_module.html#clc-server-module)
- [clc_server_snapshot – Create, Delete and Restore server snapshots in CenturyLink Cloud](https://docs.ansible.com/ansible/latest/modules/clc_server_snapshot_module.html#clc-server-snapshot-module)



### Cloudscale

- [cloudscale_floating_ip – Manages floating IPs on the cloudscale.ch IaaS service](https://docs.ansible.com/ansible/latest/modules/cloudscale_floating_ip_module.html#cloudscale-floating-ip-module)
- [cloudscale_server – Manages servers on the cloudscale.ch IaaS service](https://docs.ansible.com/ansible/latest/modules/cloudscale_server_module.html#cloudscale-server-module)
- [cloudscale_server_group – Manages server groups on the cloudscale.ch IaaS service](https://docs.ansible.com/ansible/latest/modules/cloudscale_server_group_module.html#cloudscale-server-group-module)
- [cloudscale_volume – Manages volumes on the cloudscale.ch IaaS service](https://docs.ansible.com/ansible/latest/modules/cloudscale_volume_module.html#cloudscale-volume-module)



### Cloudstack

- [cs_account – Manages accounts on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_account_module.html#cs-account-module)
- [cs_affinitygroup – Manages affinity groups on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_affinitygroup_module.html#cs-affinitygroup-module)
- [cs_cluster – Manages host clusters on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_cluster_module.html#cs-cluster-module)
- [cs_configuration – Manages configuration on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_configuration_module.html#cs-configuration-module)
- [cs_disk_offering – Manages disk offerings on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_disk_offering_module.html#cs-disk-offering-module)
- [cs_domain – Manages domains on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_domain_module.html#cs-domain-module)
- [cs_facts – Gather facts on instances of Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_facts_module.html#cs-facts-module)
- [cs_firewall – Manages firewall rules on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_firewall_module.html#cs-firewall-module)
- [cs_host – Manages hosts on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_host_module.html#cs-host-module)
- [cs_image_store – Manages CloudStack Image Stores](https://docs.ansible.com/ansible/latest/modules/cs_image_store_module.html#cs-image-store-module)
- [cs_instance – Manages instances and virtual machines on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_instance_module.html#cs-instance-module)
- [cs_instance_facts – Gathering facts from the API of instances from Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_instance_facts_module.html#cs-instance-facts-module) **(D)**
- [cs_instance_info – Gathering information from the API of instances from Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_instance_info_module.html#cs-instance-info-module)
- [cs_instance_nic – Manages NICs of an instance on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_instance_nic_module.html#cs-instance-nic-module)
- [cs_instance_nic_secondaryip – Manages secondary IPs of an instance on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_instance_nic_secondaryip_module.html#cs-instance-nic-secondaryip-module)
- [cs_instance_password_reset – Allows resetting VM the default passwords on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_instance_password_reset_module.html#cs-instance-password-reset-module)
- [cs_instancegroup – Manages instance groups on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_instancegroup_module.html#cs-instancegroup-module)
- [cs_ip_address – Manages public IP address associations on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_ip_address_module.html#cs-ip-address-module)
- [cs_iso – Manages ISO images on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_iso_module.html#cs-iso-module)
- [cs_loadbalancer_rule – Manages load balancer rules on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_loadbalancer_rule_module.html#cs-loadbalancer-rule-module)
- [cs_loadbalancer_rule_member – Manages load balancer rule members on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_loadbalancer_rule_member_module.html#cs-loadbalancer-rule-member-module)
- [cs_network – Manages networks on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_network_module.html#cs-network-module)
- [cs_network_acl – Manages network access control lists (ACL) on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_network_acl_module.html#cs-network-acl-module)
- [cs_network_acl_rule – Manages network access control list (ACL) rules on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_network_acl_rule_module.html#cs-network-acl-rule-module)
- [cs_network_offering – Manages network offerings on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_network_offering_module.html#cs-network-offering-module)
- [cs_physical_network – Manages physical networks on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_physical_network_module.html#cs-physical-network-module)
- [cs_pod – Manages pods on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_pod_module.html#cs-pod-module)
- [cs_portforward – Manages port forwarding rules on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_portforward_module.html#cs-portforward-module)
- [cs_project – Manages projects on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_project_module.html#cs-project-module)
- [cs_region – Manages regions on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_region_module.html#cs-region-module)
- [cs_resourcelimit – Manages resource limits on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_resourcelimit_module.html#cs-resourcelimit-module)
- [cs_role – Manages user roles on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_role_module.html#cs-role-module)
- [cs_role_permission – Manages role permissions on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_role_permission_module.html#cs-role-permission-module)
- [cs_router – Manages routers on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_router_module.html#cs-router-module)
- [cs_securitygroup – Manages security groups on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_securitygroup_module.html#cs-securitygroup-module)
- [cs_securitygroup_rule – Manages security group rules on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_securitygroup_rule_module.html#cs-securitygroup-rule-module)
- [cs_service_offering – Manages service offerings on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_service_offering_module.html#cs-service-offering-module)
- [cs_snapshot_policy – Manages volume snapshot policies on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_snapshot_policy_module.html#cs-snapshot-policy-module)
- [cs_sshkeypair – Manages SSH keys on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_sshkeypair_module.html#cs-sshkeypair-module)
- [cs_staticnat – Manages static NATs on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_staticnat_module.html#cs-staticnat-module)
- [cs_storage_pool – Manages Primary Storage Pools on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_storage_pool_module.html#cs-storage-pool-module)
- [cs_template – Manages templates on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_template_module.html#cs-template-module)
- [cs_traffic_type – Manages traffic types on CloudStack Physical Networks](https://docs.ansible.com/ansible/latest/modules/cs_traffic_type_module.html#cs-traffic-type-module)
- [cs_user – Manages users on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_user_module.html#cs-user-module)
- [cs_vlan_ip_range – Manages VLAN IP ranges on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_vlan_ip_range_module.html#cs-vlan-ip-range-module)
- [cs_vmsnapshot – Manages VM snapshots on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_vmsnapshot_module.html#cs-vmsnapshot-module)
- [cs_volume – Manages volumes on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_volume_module.html#cs-volume-module)
- [cs_vpc – Manages VPCs on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_vpc_module.html#cs-vpc-module)
- [cs_vpc_offering – Manages vpc offerings on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_vpc_offering_module.html#cs-vpc-offering-module)
- [cs_vpn_connection – Manages site-to-site VPN connections on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_vpn_connection_module.html#cs-vpn-connection-module)
- [cs_vpn_customer_gateway – Manages site-to-site VPN customer gateway configurations on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_vpn_customer_gateway_module.html#cs-vpn-customer-gateway-module)
- [cs_vpn_gateway – Manages site-to-site VPN gateways on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_vpn_gateway_module.html#cs-vpn-gateway-module)
- [cs_zone – Manages zones on Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_zone_module.html#cs-zone-module)
- [cs_zone_facts – Gathering facts of zones from Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_zone_facts_module.html#cs-zone-facts-module) **(D)**
- [cs_zone_info – Gathering information about zones from Apache CloudStack based clouds](https://docs.ansible.com/ansible/latest/modules/cs_zone_info_module.html#cs-zone-info-module)



### Digital_Ocean

- [digital_ocean – Create/delete a droplet/SSH_key in DigitalOcean](https://docs.ansible.com/ansible/latest/modules/digital_ocean_module.html#digital-ocean-module) **(D)**
- [digital_ocean_account_info – Gather information about DigitalOcean User account](https://docs.ansible.com/ansible/latest/modules/digital_ocean_account_info_module.html#digital-ocean-account-info-module)
- [digital_ocean_block_storage – Create/destroy or attach/detach Block Storage volumes in DigitalOcean](https://docs.ansible.com/ansible/latest/modules/digital_ocean_block_storage_module.html#digital-ocean-block-storage-module)
- [digital_ocean_certificate – Manage certificates in DigitalOcean](https://docs.ansible.com/ansible/latest/modules/digital_ocean_certificate_module.html#digital-ocean-certificate-module)
- [digital_ocean_certificate_info – Gather information about DigitalOcean certificates](https://docs.ansible.com/ansible/latest/modules/digital_ocean_certificate_info_module.html#digital-ocean-certificate-info-module)
- [digital_ocean_domain – Create/delete a DNS domain in DigitalOcean](https://docs.ansible.com/ansible/latest/modules/digital_ocean_domain_module.html#digital-ocean-domain-module)
- [digital_ocean_domain_info – Gather information about DigitalOcean Domains](https://docs.ansible.com/ansible/latest/modules/digital_ocean_domain_info_module.html#digital-ocean-domain-info-module)
- [digital_ocean_droplet – Create and delete a DigitalOcean droplet](https://docs.ansible.com/ansible/latest/modules/digital_ocean_droplet_module.html#digital-ocean-droplet-module)
- [digital_ocean_firewall_info – Gather information about DigitalOcean firewalls](https://docs.ansible.com/ansible/latest/modules/digital_ocean_firewall_info_module.html#digital-ocean-firewall-info-module)
- [digital_ocean_floating_ip – Manage DigitalOcean Floating IPs](https://docs.ansible.com/ansible/latest/modules/digital_ocean_floating_ip_module.html#digital-ocean-floating-ip-module)
- [digital_ocean_floating_ip_info – DigitalOcean Floating IPs information](https://docs.ansible.com/ansible/latest/modules/digital_ocean_floating_ip_info_module.html#digital-ocean-floating-ip-info-module)
- [digital_ocean_image_info – Gather information about DigitalOcean images](https://docs.ansible.com/ansible/latest/modules/digital_ocean_image_info_module.html#digital-ocean-image-info-module)
- [digital_ocean_load_balancer_info – Gather information about DigitalOcean load balancers](https://docs.ansible.com/ansible/latest/modules/digital_ocean_load_balancer_info_module.html#digital-ocean-load-balancer-info-module)
- [digital_ocean_region_info – Gather information about DigitalOcean regions](https://docs.ansible.com/ansible/latest/modules/digital_ocean_region_info_module.html#digital-ocean-region-info-module)
- [digital_ocean_size_info – Gather information about DigitalOcean Droplet sizes](https://docs.ansible.com/ansible/latest/modules/digital_ocean_size_info_module.html#digital-ocean-size-info-module)
- [digital_ocean_snapshot_info – Gather information about DigitalOcean Snapshot](https://docs.ansible.com/ansible/latest/modules/digital_ocean_snapshot_info_module.html#digital-ocean-snapshot-info-module)
- [digital_ocean_sshkey – Manage DigitalOcean SSH keys](https://docs.ansible.com/ansible/latest/modules/digital_ocean_sshkey_module.html#digital-ocean-sshkey-module)
- [digital_ocean_sshkey_facts – DigitalOcean SSH keys facts](https://docs.ansible.com/ansible/latest/modules/digital_ocean_sshkey_facts_module.html#digital-ocean-sshkey-facts-module) **(D)**
- [digital_ocean_sshkey_info – Gather information about DigitalOcean SSH keys](https://docs.ansible.com/ansible/latest/modules/digital_ocean_sshkey_info_module.html#digital-ocean-sshkey-info-module)
- [digital_ocean_tag – Create and remove tag(s) to DigitalOcean resource](https://docs.ansible.com/ansible/latest/modules/digital_ocean_tag_module.html#digital-ocean-tag-module)
- [digital_ocean_tag_info – Gather information about DigitalOcean tags](https://docs.ansible.com/ansible/latest/modules/digital_ocean_tag_info_module.html#digital-ocean-tag-info-module)
- [digital_ocean_volume_info – Gather information about DigitalOcean volumes](https://docs.ansible.com/ansible/latest/modules/digital_ocean_volume_info_module.html#digital-ocean-volume-info-module)



### Dimensiondata

- [dimensiondata_network – Create, update, and delete MCP 1.0 & 2.0 networks](https://docs.ansible.com/ansible/latest/modules/dimensiondata_network_module.html#dimensiondata-network-module)
- [dimensiondata_vlan – Manage a VLAN in a Cloud Control network domain](https://docs.ansible.com/ansible/latest/modules/dimensiondata_vlan_module.html#dimensiondata-vlan-module)



### Docker

- [docker_compose – Manage multi-container Docker applications with Docker Compose](https://docs.ansible.com/ansible/latest/modules/docker_compose_module.html#docker-compose-module)
- [docker_config – Manage docker configs](https://docs.ansible.com/ansible/latest/modules/docker_config_module.html#docker-config-module)
- [docker_container – manage docker containers](https://docs.ansible.com/ansible/latest/modules/docker_container_module.html#docker-container-module)
- [docker_container_info – Retrieves facts about docker container](https://docs.ansible.com/ansible/latest/modules/docker_container_info_module.html#docker-container-info-module)
- [docker_host_info – Retrieves facts about docker host and lists of objects of the services](https://docs.ansible.com/ansible/latest/modules/docker_host_info_module.html#docker-host-info-module)
- [docker_image – Manage docker images](https://docs.ansible.com/ansible/latest/modules/docker_image_module.html#docker-image-module)
- [docker_image_info – Inspect docker images](https://docs.ansible.com/ansible/latest/modules/docker_image_info_module.html#docker-image-info-module)
- [docker_login – Log into a Docker registry](https://docs.ansible.com/ansible/latest/modules/docker_login_module.html#docker-login-module)
- [docker_network – Manage Docker networks](https://docs.ansible.com/ansible/latest/modules/docker_network_module.html#docker-network-module)
- [docker_network_info – Retrieves facts about docker network](https://docs.ansible.com/ansible/latest/modules/docker_network_info_module.html#docker-network-info-module)
- [docker_node – Manage Docker Swarm node](https://docs.ansible.com/ansible/latest/modules/docker_node_module.html#docker-node-module)
- [docker_node_info – Retrieves facts about docker swarm node from Swarm Manager](https://docs.ansible.com/ansible/latest/modules/docker_node_info_module.html#docker-node-info-module)
- [docker_prune – Allows to prune various docker objects](https://docs.ansible.com/ansible/latest/modules/docker_prune_module.html#docker-prune-module)
- [docker_secret – Manage docker secrets](https://docs.ansible.com/ansible/latest/modules/docker_secret_module.html#docker-secret-module)
- [docker_stack – docker stack module](https://docs.ansible.com/ansible/latest/modules/docker_stack_module.html#docker-stack-module)
- [docker_swarm – Manage Swarm cluster](https://docs.ansible.com/ansible/latest/modules/docker_swarm_module.html#docker-swarm-module)
- [docker_swarm_info – Retrieves facts about Docker Swarm cluster](https://docs.ansible.com/ansible/latest/modules/docker_swarm_info_module.html#docker-swarm-info-module)
- [docker_swarm_service – docker swarm service](https://docs.ansible.com/ansible/latest/modules/docker_swarm_service_module.html#docker-swarm-service-module)
- [docker_swarm_service_info – Retrieves information about docker services from a Swarm Manager](https://docs.ansible.com/ansible/latest/modules/docker_swarm_service_info_module.html#docker-swarm-service-info-module)
- [docker_volume – Manage Docker volumes](https://docs.ansible.com/ansible/latest/modules/docker_volume_module.html#docker-volume-module)
- [docker_volume_info – Retrieve facts about Docker volumes](https://docs.ansible.com/ansible/latest/modules/docker_volume_info_module.html#docker-volume-info-module)



### Google

- [gc_storage – This module manages objects/buckets in Google Cloud Storage](https://docs.ansible.com/ansible/latest/modules/gc_storage_module.html#gc-storage-module)
- [gcdns_record – Creates or removes resource records in Google Cloud DNS](https://docs.ansible.com/ansible/latest/modules/gcdns_record_module.html#gcdns-record-module) **(D)**
- [gcdns_zone – Creates or removes zones in Google Cloud DNS](https://docs.ansible.com/ansible/latest/modules/gcdns_zone_module.html#gcdns-zone-module) **(D)**
- [gce – create or terminate GCE instances](https://docs.ansible.com/ansible/latest/modules/gce_module.html#gce-module) **(D)**
- [gce_eip – Create or Destroy Global or Regional External IP addresses](https://docs.ansible.com/ansible/latest/modules/gce_eip_module.html#gce-eip-module)
- [gce_img – utilize GCE image resources](https://docs.ansible.com/ansible/latest/modules/gce_img_module.html#gce-img-module)
- [gce_instance_template – create or destroy instance templates of Compute Engine of GCP](https://docs.ansible.com/ansible/latest/modules/gce_instance_template_module.html#gce-instance-template-module)
- [gce_labels – Create, Update or Destroy GCE Labels](https://docs.ansible.com/ansible/latest/modules/gce_labels_module.html#gce-labels-module)
- [gce_lb – create/destroy GCE load-balancer resources](https://docs.ansible.com/ansible/latest/modules/gce_lb_module.html#gce-lb-module)
- [gce_mig – Create, Update or Destroy a Managed Instance Group (MIG)](https://docs.ansible.com/ansible/latest/modules/gce_mig_module.html#gce-mig-module)
- [gce_net – create/destroy GCE networks and firewall rules](https://docs.ansible.com/ansible/latest/modules/gce_net_module.html#gce-net-module)
- [gce_pd – utilize GCE persistent disk resources](https://docs.ansible.com/ansible/latest/modules/gce_pd_module.html#gce-pd-module)
- [gce_snapshot – Create or destroy snapshots for GCE storage volumes](https://docs.ansible.com/ansible/latest/modules/gce_snapshot_module.html#gce-snapshot-module)
- [gce_tag – add or remove tag(s) to/from GCE instances](https://docs.ansible.com/ansible/latest/modules/gce_tag_module.html#gce-tag-module)
- [gcp_appengine_firewall_rule – Creates a GCP FirewallRule](https://docs.ansible.com/ansible/latest/modules/gcp_appengine_firewall_rule_module.html#gcp-appengine-firewall-rule-module)
- [gcp_appengine_firewall_rule_info – Gather info for GCP FirewallRule](https://docs.ansible.com/ansible/latest/modules/gcp_appengine_firewall_rule_info_module.html#gcp-appengine-firewall-rule-info-module)
- [gcp_backend_service – Create or Destroy a Backend Service](https://docs.ansible.com/ansible/latest/modules/gcp_backend_service_module.html#gcp-backend-service-module) **(D)**
- [gcp_bigquery_dataset – Creates a GCP Dataset](https://docs.ansible.com/ansible/latest/modules/gcp_bigquery_dataset_module.html#gcp-bigquery-dataset-module)
- [gcp_bigquery_dataset_info – Gather info for GCP Dataset](https://docs.ansible.com/ansible/latest/modules/gcp_bigquery_dataset_info_module.html#gcp-bigquery-dataset-info-module)
- [gcp_bigquery_table – Creates a GCP Table](https://docs.ansible.com/ansible/latest/modules/gcp_bigquery_table_module.html#gcp-bigquery-table-module)
- [gcp_bigquery_table_info – Gather info for GCP Table](https://docs.ansible.com/ansible/latest/modules/gcp_bigquery_table_info_module.html#gcp-bigquery-table-info-module)
- [gcp_cloudbuild_trigger – Creates a GCP Trigger](https://docs.ansible.com/ansible/latest/modules/gcp_cloudbuild_trigger_module.html#gcp-cloudbuild-trigger-module)
- [gcp_cloudbuild_trigger_info – Gather info for GCP Trigger](https://docs.ansible.com/ansible/latest/modules/gcp_cloudbuild_trigger_info_module.html#gcp-cloudbuild-trigger-info-module)
- [gcp_cloudfunctions_cloud_function – Creates a GCP CloudFunction](https://docs.ansible.com/ansible/latest/modules/gcp_cloudfunctions_cloud_function_module.html#gcp-cloudfunctions-cloud-function-module)
- [gcp_cloudfunctions_cloud_function_info – Gather info for GCP CloudFunction](https://docs.ansible.com/ansible/latest/modules/gcp_cloudfunctions_cloud_function_info_module.html#gcp-cloudfunctions-cloud-function-info-module)
- [gcp_cloudscheduler_job – Creates a GCP Job](https://docs.ansible.com/ansible/latest/modules/gcp_cloudscheduler_job_module.html#gcp-cloudscheduler-job-module)
- [gcp_cloudscheduler_job_info – Gather info for GCP Job](https://docs.ansible.com/ansible/latest/modules/gcp_cloudscheduler_job_info_module.html#gcp-cloudscheduler-job-info-module)
- [gcp_cloudtasks_queue – Creates a GCP Queue](https://docs.ansible.com/ansible/latest/modules/gcp_cloudtasks_queue_module.html#gcp-cloudtasks-queue-module)
- [gcp_cloudtasks_queue_info – Gather info for GCP Queue](https://docs.ansible.com/ansible/latest/modules/gcp_cloudtasks_queue_info_module.html#gcp-cloudtasks-queue-info-module)
- [gcp_compute_address – Creates a GCP Address](https://docs.ansible.com/ansible/latest/modules/gcp_compute_address_module.html#gcp-compute-address-module)
- [gcp_compute_address_info – Gather info for GCP Address](https://docs.ansible.com/ansible/latest/modules/gcp_compute_address_info_module.html#gcp-compute-address-info-module)
- [gcp_compute_autoscaler – Creates a GCP Autoscaler](https://docs.ansible.com/ansible/latest/modules/gcp_compute_autoscaler_module.html#gcp-compute-autoscaler-module)
- [gcp_compute_autoscaler_info – Gather info for GCP Autoscaler](https://docs.ansible.com/ansible/latest/modules/gcp_compute_autoscaler_info_module.html#gcp-compute-autoscaler-info-module)
- [gcp_compute_backend_bucket – Creates a GCP BackendBucket](https://docs.ansible.com/ansible/latest/modules/gcp_compute_backend_bucket_module.html#gcp-compute-backend-bucket-module)
- [gcp_compute_backend_bucket_info – Gather info for GCP BackendBucket](https://docs.ansible.com/ansible/latest/modules/gcp_compute_backend_bucket_info_module.html#gcp-compute-backend-bucket-info-module)
- [gcp_compute_backend_service – Creates a GCP BackendService](https://docs.ansible.com/ansible/latest/modules/gcp_compute_backend_service_module.html#gcp-compute-backend-service-module)
- [gcp_compute_backend_service_info – Gather info for GCP BackendService](https://docs.ansible.com/ansible/latest/modules/gcp_compute_backend_service_info_module.html#gcp-compute-backend-service-info-module)
- [gcp_compute_disk – Creates a GCP Disk](https://docs.ansible.com/ansible/latest/modules/gcp_compute_disk_module.html#gcp-compute-disk-module)
- [gcp_compute_disk_info – Gather info for GCP Disk](https://docs.ansible.com/ansible/latest/modules/gcp_compute_disk_info_module.html#gcp-compute-disk-info-module)
- [gcp_compute_firewall – Creates a GCP Firewall](https://docs.ansible.com/ansible/latest/modules/gcp_compute_firewall_module.html#gcp-compute-firewall-module)
- [gcp_compute_firewall_info – Gather info for GCP Firewall](https://docs.ansible.com/ansible/latest/modules/gcp_compute_firewall_info_module.html#gcp-compute-firewall-info-module)
- [gcp_compute_forwarding_rule – Creates a GCP ForwardingRule](https://docs.ansible.com/ansible/latest/modules/gcp_compute_forwarding_rule_module.html#gcp-compute-forwarding-rule-module)
- [gcp_compute_forwarding_rule_info – Gather info for GCP ForwardingRule](https://docs.ansible.com/ansible/latest/modules/gcp_compute_forwarding_rule_info_module.html#gcp-compute-forwarding-rule-info-module)
- [gcp_compute_global_address – Creates a GCP GlobalAddress](https://docs.ansible.com/ansible/latest/modules/gcp_compute_global_address_module.html#gcp-compute-global-address-module)
- [gcp_compute_global_address_info – Gather info for GCP GlobalAddress](https://docs.ansible.com/ansible/latest/modules/gcp_compute_global_address_info_module.html#gcp-compute-global-address-info-module)
- [gcp_compute_global_forwarding_rule – Creates a GCP GlobalForwardingRule](https://docs.ansible.com/ansible/latest/modules/gcp_compute_global_forwarding_rule_module.html#gcp-compute-global-forwarding-rule-module)
- [gcp_compute_global_forwarding_rule_info – Gather info for GCP GlobalForwardingRule](https://docs.ansible.com/ansible/latest/modules/gcp_compute_global_forwarding_rule_info_module.html#gcp-compute-global-forwarding-rule-info-module)
- [gcp_compute_health_check – Creates a GCP HealthCheck](https://docs.ansible.com/ansible/latest/modules/gcp_compute_health_check_module.html#gcp-compute-health-check-module)
- [gcp_compute_health_check_info – Gather info for GCP HealthCheck](https://docs.ansible.com/ansible/latest/modules/gcp_compute_health_check_info_module.html#gcp-compute-health-check-info-module)
- [gcp_compute_http_health_check – Creates a GCP HttpHealthCheck](https://docs.ansible.com/ansible/latest/modules/gcp_compute_http_health_check_module.html#gcp-compute-http-health-check-module)
- [gcp_compute_http_health_check_info – Gather info for GCP HttpHealthCheck](https://docs.ansible.com/ansible/latest/modules/gcp_compute_http_health_check_info_module.html#gcp-compute-http-health-check-info-module)
- [gcp_compute_https_health_check – Creates a GCP HttpsHealthCheck](https://docs.ansible.com/ansible/latest/modules/gcp_compute_https_health_check_module.html#gcp-compute-https-health-check-module)
- [gcp_compute_https_health_check_info – Gather info for GCP HttpsHealthCheck](https://docs.ansible.com/ansible/latest/modules/gcp_compute_https_health_check_info_module.html#gcp-compute-https-health-check-info-module)
- [gcp_compute_image – Creates a GCP Image](https://docs.ansible.com/ansible/latest/modules/gcp_compute_image_module.html#gcp-compute-image-module)
- [gcp_compute_image_info – Gather info for GCP Image](https://docs.ansible.com/ansible/latest/modules/gcp_compute_image_info_module.html#gcp-compute-image-info-module)
- [gcp_compute_instance – Creates a GCP Instance](https://docs.ansible.com/ansible/latest/modules/gcp_compute_instance_module.html#gcp-compute-instance-module)
- [gcp_compute_instance_group – Creates a GCP InstanceGroup](https://docs.ansible.com/ansible/latest/modules/gcp_compute_instance_group_module.html#gcp-compute-instance-group-module)
- [gcp_compute_instance_group_info – Gather info for GCP InstanceGroup](https://docs.ansible.com/ansible/latest/modules/gcp_compute_instance_group_info_module.html#gcp-compute-instance-group-info-module)
- [gcp_compute_instance_group_manager – Creates a GCP InstanceGroupManager](https://docs.ansible.com/ansible/latest/modules/gcp_compute_instance_group_manager_module.html#gcp-compute-instance-group-manager-module)
- [gcp_compute_instance_group_manager_info – Gather info for GCP InstanceGroupManager](https://docs.ansible.com/ansible/latest/modules/gcp_compute_instance_group_manager_info_module.html#gcp-compute-instance-group-manager-info-module)
- [gcp_compute_instance_info – Gather info for GCP Instance](https://docs.ansible.com/ansible/latest/modules/gcp_compute_instance_info_module.html#gcp-compute-instance-info-module)
- [gcp_compute_instance_template – Creates a GCP InstanceTemplate](https://docs.ansible.com/ansible/latest/modules/gcp_compute_instance_template_module.html#gcp-compute-instance-template-module)
- [gcp_compute_instance_template_info – Gather info for GCP InstanceTemplate](https://docs.ansible.com/ansible/latest/modules/gcp_compute_instance_template_info_module.html#gcp-compute-instance-template-info-module)
- [gcp_compute_interconnect_attachment – Creates a GCP InterconnectAttachment](https://docs.ansible.com/ansible/latest/modules/gcp_compute_interconnect_attachment_module.html#gcp-compute-interconnect-attachment-module)
- [gcp_compute_interconnect_attachment_info – Gather info for GCP InterconnectAttachment](https://docs.ansible.com/ansible/latest/modules/gcp_compute_interconnect_attachment_info_module.html#gcp-compute-interconnect-attachment-info-module)
- [gcp_compute_network – Creates a GCP Network](https://docs.ansible.com/ansible/latest/modules/gcp_compute_network_module.html#gcp-compute-network-module)
- [gcp_compute_network_info – Gather info for GCP Network](https://docs.ansible.com/ansible/latest/modules/gcp_compute_network_info_module.html#gcp-compute-network-info-module)
- [gcp_compute_region_disk – Creates a GCP RegionDisk](https://docs.ansible.com/ansible/latest/modules/gcp_compute_region_disk_module.html#gcp-compute-region-disk-module)
- [gcp_compute_region_disk_info – Gather info for GCP RegionDisk](https://docs.ansible.com/ansible/latest/modules/gcp_compute_region_disk_info_module.html#gcp-compute-region-disk-info-module)
- [gcp_compute_route – Creates a GCP Route](https://docs.ansible.com/ansible/latest/modules/gcp_compute_route_module.html#gcp-compute-route-module)
- [gcp_compute_route_info – Gather info for GCP Route](https://docs.ansible.com/ansible/latest/modules/gcp_compute_route_info_module.html#gcp-compute-route-info-module)
- [gcp_compute_router – Creates a GCP Router](https://docs.ansible.com/ansible/latest/modules/gcp_compute_router_module.html#gcp-compute-router-module)
- [gcp_compute_router_info – Gather info for GCP Router](https://docs.ansible.com/ansible/latest/modules/gcp_compute_router_info_module.html#gcp-compute-router-info-module)
- [gcp_compute_snapshot – Creates a GCP Snapshot](https://docs.ansible.com/ansible/latest/modules/gcp_compute_snapshot_module.html#gcp-compute-snapshot-module)
- [gcp_compute_snapshot_info – Gather info for GCP Snapshot](https://docs.ansible.com/ansible/latest/modules/gcp_compute_snapshot_info_module.html#gcp-compute-snapshot-info-module)
- [gcp_compute_ssl_certificate – Creates a GCP SslCertificate](https://docs.ansible.com/ansible/latest/modules/gcp_compute_ssl_certificate_module.html#gcp-compute-ssl-certificate-module)
- [gcp_compute_ssl_certificate_info – Gather info for GCP SslCertificate](https://docs.ansible.com/ansible/latest/modules/gcp_compute_ssl_certificate_info_module.html#gcp-compute-ssl-certificate-info-module)
- [gcp_compute_ssl_policy – Creates a GCP SslPolicy](https://docs.ansible.com/ansible/latest/modules/gcp_compute_ssl_policy_module.html#gcp-compute-ssl-policy-module)
- [gcp_compute_ssl_policy_info – Gather info for GCP SslPolicy](https://docs.ansible.com/ansible/latest/modules/gcp_compute_ssl_policy_info_module.html#gcp-compute-ssl-policy-info-module)
- [gcp_compute_subnetwork – Creates a GCP Subnetwork](https://docs.ansible.com/ansible/latest/modules/gcp_compute_subnetwork_module.html#gcp-compute-subnetwork-module)
- [gcp_compute_subnetwork_info – Gather info for GCP Subnetwork](https://docs.ansible.com/ansible/latest/modules/gcp_compute_subnetwork_info_module.html#gcp-compute-subnetwork-info-module)
- [gcp_compute_target_http_proxy – Creates a GCP TargetHttpProxy](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_http_proxy_module.html#gcp-compute-target-http-proxy-module)
- [gcp_compute_target_http_proxy_info – Gather info for GCP TargetHttpProxy](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_http_proxy_info_module.html#gcp-compute-target-http-proxy-info-module)
- [gcp_compute_target_https_proxy – Creates a GCP TargetHttpsProxy](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_https_proxy_module.html#gcp-compute-target-https-proxy-module)
- [gcp_compute_target_https_proxy_info – Gather info for GCP TargetHttpsProxy](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_https_proxy_info_module.html#gcp-compute-target-https-proxy-info-module)
- [gcp_compute_target_pool – Creates a GCP TargetPool](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_pool_module.html#gcp-compute-target-pool-module)
- [gcp_compute_target_pool_info – Gather info for GCP TargetPool](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_pool_info_module.html#gcp-compute-target-pool-info-module)
- [gcp_compute_target_ssl_proxy – Creates a GCP TargetSslProxy](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_ssl_proxy_module.html#gcp-compute-target-ssl-proxy-module)
- [gcp_compute_target_ssl_proxy_info – Gather info for GCP TargetSslProxy](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_ssl_proxy_info_module.html#gcp-compute-target-ssl-proxy-info-module)
- [gcp_compute_target_tcp_proxy – Creates a GCP TargetTcpProxy](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_tcp_proxy_module.html#gcp-compute-target-tcp-proxy-module)
- [gcp_compute_target_tcp_proxy_info – Gather info for GCP TargetTcpProxy](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_tcp_proxy_info_module.html#gcp-compute-target-tcp-proxy-info-module)
- [gcp_compute_target_vpn_gateway – Creates a GCP TargetVpnGateway](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_vpn_gateway_module.html#gcp-compute-target-vpn-gateway-module)
- [gcp_compute_target_vpn_gateway_info – Gather info for GCP TargetVpnGateway](https://docs.ansible.com/ansible/latest/modules/gcp_compute_target_vpn_gateway_info_module.html#gcp-compute-target-vpn-gateway-info-module)
- [gcp_compute_url_map – Creates a GCP UrlMap](https://docs.ansible.com/ansible/latest/modules/gcp_compute_url_map_module.html#gcp-compute-url-map-module)
- [gcp_compute_url_map_info – Gather info for GCP UrlMap](https://docs.ansible.com/ansible/latest/modules/gcp_compute_url_map_info_module.html#gcp-compute-url-map-info-module)
- [gcp_compute_vpn_tunnel – Creates a GCP VpnTunnel](https://docs.ansible.com/ansible/latest/modules/gcp_compute_vpn_tunnel_module.html#gcp-compute-vpn-tunnel-module)
- [gcp_compute_vpn_tunnel_info – Gather info for GCP VpnTunnel](https://docs.ansible.com/ansible/latest/modules/gcp_compute_vpn_tunnel_info_module.html#gcp-compute-vpn-tunnel-info-module)
- [gcp_container_cluster – Creates a GCP Cluster](https://docs.ansible.com/ansible/latest/modules/gcp_container_cluster_module.html#gcp-container-cluster-module)
- [gcp_container_cluster_info – Gather info for GCP Cluster](https://docs.ansible.com/ansible/latest/modules/gcp_container_cluster_info_module.html#gcp-container-cluster-info-module)
- [gcp_container_node_pool – Creates a GCP NodePool](https://docs.ansible.com/ansible/latest/modules/gcp_container_node_pool_module.html#gcp-container-node-pool-module)
- [gcp_container_node_pool_info – Gather info for GCP NodePool](https://docs.ansible.com/ansible/latest/modules/gcp_container_node_pool_info_module.html#gcp-container-node-pool-info-module)
- [gcp_dns_managed_zone – Creates a GCP ManagedZone](https://docs.ansible.com/ansible/latest/modules/gcp_dns_managed_zone_module.html#gcp-dns-managed-zone-module)
- [gcp_dns_managed_zone_info – Gather info for GCP ManagedZone](https://docs.ansible.com/ansible/latest/modules/gcp_dns_managed_zone_info_module.html#gcp-dns-managed-zone-info-module)
- [gcp_dns_resource_record_set – Creates a GCP ResourceRecordSet](https://docs.ansible.com/ansible/latest/modules/gcp_dns_resource_record_set_module.html#gcp-dns-resource-record-set-module)
- [gcp_dns_resource_record_set_info – Gather info for GCP ResourceRecordSet](https://docs.ansible.com/ansible/latest/modules/gcp_dns_resource_record_set_info_module.html#gcp-dns-resource-record-set-info-module)
- [gcp_filestore_instance – Creates a GCP Instance](https://docs.ansible.com/ansible/latest/modules/gcp_filestore_instance_module.html#gcp-filestore-instance-module)
- [gcp_filestore_instance_info – Gather info for GCP Instance](https://docs.ansible.com/ansible/latest/modules/gcp_filestore_instance_info_module.html#gcp-filestore-instance-info-module)
- [gcp_forwarding_rule – Create, Update or Destroy a Forwarding_Rule](https://docs.ansible.com/ansible/latest/modules/gcp_forwarding_rule_module.html#gcp-forwarding-rule-module) **(D)**
- [gcp_healthcheck – Create, Update or Destroy a Healthcheck](https://docs.ansible.com/ansible/latest/modules/gcp_healthcheck_module.html#gcp-healthcheck-module) **(D)**
- [gcp_iam_role – Creates a GCP Role](https://docs.ansible.com/ansible/latest/modules/gcp_iam_role_module.html#gcp-iam-role-module)
- [gcp_iam_role_info – Gather info for GCP Role](https://docs.ansible.com/ansible/latest/modules/gcp_iam_role_info_module.html#gcp-iam-role-info-module)
- [gcp_iam_service_account – Creates a GCP ServiceAccount](https://docs.ansible.com/ansible/latest/modules/gcp_iam_service_account_module.html#gcp-iam-service-account-module)
- [gcp_iam_service_account_info – Gather info for GCP ServiceAccount](https://docs.ansible.com/ansible/latest/modules/gcp_iam_service_account_info_module.html#gcp-iam-service-account-info-module)
- [gcp_iam_service_account_key – Creates a GCP ServiceAccountKey](https://docs.ansible.com/ansible/latest/modules/gcp_iam_service_account_key_module.html#gcp-iam-service-account-key-module)
- [gcp_kms_crypto_key – Creates a GCP CryptoKey](https://docs.ansible.com/ansible/latest/modules/gcp_kms_crypto_key_module.html#gcp-kms-crypto-key-module)
- [gcp_kms_crypto_key_info – Gather info for GCP CryptoKey](https://docs.ansible.com/ansible/latest/modules/gcp_kms_crypto_key_info_module.html#gcp-kms-crypto-key-info-module)
- [gcp_kms_key_ring – Creates a GCP KeyRing](https://docs.ansible.com/ansible/latest/modules/gcp_kms_key_ring_module.html#gcp-kms-key-ring-module)
- [gcp_kms_key_ring_info – Gather info for GCP KeyRing](https://docs.ansible.com/ansible/latest/modules/gcp_kms_key_ring_info_module.html#gcp-kms-key-ring-info-module)
- [gcp_mlengine_model – Creates a GCP Model](https://docs.ansible.com/ansible/latest/modules/gcp_mlengine_model_module.html#gcp-mlengine-model-module)
- [gcp_mlengine_model_info – Gather info for GCP Model](https://docs.ansible.com/ansible/latest/modules/gcp_mlengine_model_info_module.html#gcp-mlengine-model-info-module)
- [gcp_mlengine_version – Creates a GCP Version](https://docs.ansible.com/ansible/latest/modules/gcp_mlengine_version_module.html#gcp-mlengine-version-module)
- [gcp_mlengine_version_info – Gather info for GCP Version](https://docs.ansible.com/ansible/latest/modules/gcp_mlengine_version_info_module.html#gcp-mlengine-version-info-module)
- [gcp_pubsub_subscription – Creates a GCP Subscription](https://docs.ansible.com/ansible/latest/modules/gcp_pubsub_subscription_module.html#gcp-pubsub-subscription-module)
- [gcp_pubsub_subscription_info – Gather info for GCP Subscription](https://docs.ansible.com/ansible/latest/modules/gcp_pubsub_subscription_info_module.html#gcp-pubsub-subscription-info-module)
- [gcp_pubsub_topic – Creates a GCP Topic](https://docs.ansible.com/ansible/latest/modules/gcp_pubsub_topic_module.html#gcp-pubsub-topic-module)
- [gcp_pubsub_topic_info – Gather info for GCP Topic](https://docs.ansible.com/ansible/latest/modules/gcp_pubsub_topic_info_module.html#gcp-pubsub-topic-info-module)
- [gcp_redis_instance – Creates a GCP Instance](https://docs.ansible.com/ansible/latest/modules/gcp_redis_instance_module.html#gcp-redis-instance-module)
- [gcp_redis_instance_info – Gather info for GCP Instance](https://docs.ansible.com/ansible/latest/modules/gcp_redis_instance_info_module.html#gcp-redis-instance-info-module)
- [gcp_resourcemanager_project – Creates a GCP Project](https://docs.ansible.com/ansible/latest/modules/gcp_resourcemanager_project_module.html#gcp-resourcemanager-project-module)
- [gcp_resourcemanager_project_info – Gather info for GCP Project](https://docs.ansible.com/ansible/latest/modules/gcp_resourcemanager_project_info_module.html#gcp-resourcemanager-project-info-module)
- [gcp_sourcerepo_repository – Creates a GCP Repository](https://docs.ansible.com/ansible/latest/modules/gcp_sourcerepo_repository_module.html#gcp-sourcerepo-repository-module)
- [gcp_sourcerepo_repository_info – Gather info for GCP Repository](https://docs.ansible.com/ansible/latest/modules/gcp_sourcerepo_repository_info_module.html#gcp-sourcerepo-repository-info-module)
- [gcp_spanner_database – Creates a GCP Database](https://docs.ansible.com/ansible/latest/modules/gcp_spanner_database_module.html#gcp-spanner-database-module)
- [gcp_spanner_database_info – Gather info for GCP Database](https://docs.ansible.com/ansible/latest/modules/gcp_spanner_database_info_module.html#gcp-spanner-database-info-module)
- [gcp_spanner_instance – Creates a GCP Instance](https://docs.ansible.com/ansible/latest/modules/gcp_spanner_instance_module.html#gcp-spanner-instance-module)
- [gcp_spanner_instance_info – Gather info for GCP Instance](https://docs.ansible.com/ansible/latest/modules/gcp_spanner_instance_info_module.html#gcp-spanner-instance-info-module)
- [gcp_sql_database – Creates a GCP Database](https://docs.ansible.com/ansible/latest/modules/gcp_sql_database_module.html#gcp-sql-database-module)
- [gcp_sql_database_info – Gather info for GCP Database](https://docs.ansible.com/ansible/latest/modules/gcp_sql_database_info_module.html#gcp-sql-database-info-module)
- [gcp_sql_instance – Creates a GCP Instance](https://docs.ansible.com/ansible/latest/modules/gcp_sql_instance_module.html#gcp-sql-instance-module)
- [gcp_sql_instance_info – Gather info for GCP Instance](https://docs.ansible.com/ansible/latest/modules/gcp_sql_instance_info_module.html#gcp-sql-instance-info-module)
- [gcp_sql_user – Creates a GCP User](https://docs.ansible.com/ansible/latest/modules/gcp_sql_user_module.html#gcp-sql-user-module)
- [gcp_sql_user_info – Gather info for GCP User](https://docs.ansible.com/ansible/latest/modules/gcp_sql_user_info_module.html#gcp-sql-user-info-module)
- [gcp_storage_bucket – Creates a GCP Bucket](https://docs.ansible.com/ansible/latest/modules/gcp_storage_bucket_module.html#gcp-storage-bucket-module)
- [gcp_storage_bucket_access_control – Creates a GCP BucketAccessControl](https://docs.ansible.com/ansible/latest/modules/gcp_storage_bucket_access_control_module.html#gcp-storage-bucket-access-control-module)
- [gcp_storage_object – Creates a GCP Object](https://docs.ansible.com/ansible/latest/modules/gcp_storage_object_module.html#gcp-storage-object-module)
- [gcp_target_proxy – Create, Update or Destroy a Target_Proxy](https://docs.ansible.com/ansible/latest/modules/gcp_target_proxy_module.html#gcp-target-proxy-module) **(D)**
- [gcp_tpu_node – Creates a GCP Node](https://docs.ansible.com/ansible/latest/modules/gcp_tpu_node_module.html#gcp-tpu-node-module)
- [gcp_tpu_node_info – Gather info for GCP Node](https://docs.ansible.com/ansible/latest/modules/gcp_tpu_node_info_module.html#gcp-tpu-node-info-module)
- [gcp_url_map – Create, Update or Destroy a Url_Map](https://docs.ansible.com/ansible/latest/modules/gcp_url_map_module.html#gcp-url-map-module) **(D)**
- [gcpubsub – Create and Delete Topics/Subscriptions, Publish and pull messages on PubSub](https://docs.ansible.com/ansible/latest/modules/gcpubsub_module.html#gcpubsub-module)
- [gcpubsub_info – List Topics/Subscriptions and Messages from Google PubSub](https://docs.ansible.com/ansible/latest/modules/gcpubsub_info_module.html#gcpubsub-info-module)
- [gcspanner – Create and Delete Instances/Databases on Spanner](https://docs.ansible.com/ansible/latest/modules/gcspanner_module.html#gcspanner-module) **(D)**



### Hcloud

- [hcloud_datacenter_info – Gather info about the Hetzner Cloud datacenters](https://docs.ansible.com/ansible/latest/modules/hcloud_datacenter_info_module.html#hcloud-datacenter-info-module)
- [hcloud_floating_ip_info – Gather infos about the Hetzner Cloud Floating IPs](https://docs.ansible.com/ansible/latest/modules/hcloud_floating_ip_info_module.html#hcloud-floating-ip-info-module)
- [hcloud_image_info – Gather infos about your Hetzner Cloud images](https://docs.ansible.com/ansible/latest/modules/hcloud_image_info_module.html#hcloud-image-info-module)
- [hcloud_location_info – Gather infos about your Hetzner Cloud locations](https://docs.ansible.com/ansible/latest/modules/hcloud_location_info_module.html#hcloud-location-info-module)
- [hcloud_network – Create and manage cloud Networks on the Hetzner Cloud](https://docs.ansible.com/ansible/latest/modules/hcloud_network_module.html#hcloud-network-module)
- [hcloud_network_info – Gather info about your Hetzner Cloud networks](https://docs.ansible.com/ansible/latest/modules/hcloud_network_info_module.html#hcloud-network-info-module)
- [hcloud_rdns – Create and manage reverse DNS entries on the Hetzner Cloud](https://docs.ansible.com/ansible/latest/modules/hcloud_rdns_module.html#hcloud-rdns-module)
- [hcloud_route – Create and delete cloud routes on the Hetzner Cloud](https://docs.ansible.com/ansible/latest/modules/hcloud_route_module.html#hcloud-route-module)
- [hcloud_server – Create and manage cloud servers on the Hetzner Cloud](https://docs.ansible.com/ansible/latest/modules/hcloud_server_module.html#hcloud-server-module)
- [hcloud_server_info – Gather infos about your Hetzner Cloud servers](https://docs.ansible.com/ansible/latest/modules/hcloud_server_info_module.html#hcloud-server-info-module)
- [hcloud_server_network – Manage the relationship between Hetzner Cloud Networks and servers](https://docs.ansible.com/ansible/latest/modules/hcloud_server_network_module.html#hcloud-server-network-module)
- [hcloud_server_type_info – Gather infos about the Hetzner Cloud server types](https://docs.ansible.com/ansible/latest/modules/hcloud_server_type_info_module.html#hcloud-server-type-info-module)
- [hcloud_ssh_key – Create and manage ssh keys on the Hetzner Cloud](https://docs.ansible.com/ansible/latest/modules/hcloud_ssh_key_module.html#hcloud-ssh-key-module)
- [hcloud_ssh_key_info – Gather infos about your Hetzner Cloud ssh_keys](https://docs.ansible.com/ansible/latest/modules/hcloud_ssh_key_info_module.html#hcloud-ssh-key-info-module)
- [hcloud_subnetwork – Manage cloud subnetworks on the Hetzner Cloud](https://docs.ansible.com/ansible/latest/modules/hcloud_subnetwork_module.html#hcloud-subnetwork-module)
- [hcloud_volume – Create and manage block volumes on the Hetzner Cloud](https://docs.ansible.com/ansible/latest/modules/hcloud_volume_module.html#hcloud-volume-module)
- [hcloud_volume_info – Gather infos about your Hetzner Cloud volumes](https://docs.ansible.com/ansible/latest/modules/hcloud_volume_info_module.html#hcloud-volume-info-module)



### Heroku

- [heroku_collaborator – Add or delete app collaborators on Heroku](https://docs.ansible.com/ansible/latest/modules/heroku_collaborator_module.html#heroku-collaborator-module)



### Huawei

- [hwc_network_vpc – Creates a Huawei Cloud VPC](https://docs.ansible.com/ansible/latest/modules/hwc_network_vpc_module.html#hwc-network-vpc-module)
- [hwc_smn_topic – Creates a resource of SMNTopic in Huaweicloud Cloud](https://docs.ansible.com/ansible/latest/modules/hwc_smn_topic_module.html#hwc-smn-topic-module)



### Kubevirt

- [kubevirt_cdi_upload – Upload local VM images to CDI Upload Proxy](https://docs.ansible.com/ansible/latest/modules/kubevirt_cdi_upload_module.html#kubevirt-cdi-upload-module)
- [kubevirt_preset – Manage KubeVirt virtual machine presets](https://docs.ansible.com/ansible/latest/modules/kubevirt_preset_module.html#kubevirt-preset-module)
- [kubevirt_pvc – Manage PVCs on Kubernetes](https://docs.ansible.com/ansible/latest/modules/kubevirt_pvc_module.html#kubevirt-pvc-module)
- [kubevirt_rs – Manage KubeVirt virtual machine replica sets](https://docs.ansible.com/ansible/latest/modules/kubevirt_rs_module.html#kubevirt-rs-module)
- [kubevirt_template – Manage KubeVirt templates](https://docs.ansible.com/ansible/latest/modules/kubevirt_template_module.html#kubevirt-template-module)
- [kubevirt_vm – Manage KubeVirt virtual machine](https://docs.ansible.com/ansible/latest/modules/kubevirt_vm_module.html#kubevirt-vm-module)



### Linode

- [linode – Manage instances on the Linode Public Cloud](https://docs.ansible.com/ansible/latest/modules/linode_module.html#linode-module)
- [linode_v4 – Manage instances on the Linode cloud](https://docs.ansible.com/ansible/latest/modules/linode_v4_module.html#linode-v4-module)



### Lxc

- [lxc_container – Manage LXC Containers](https://docs.ansible.com/ansible/latest/modules/lxc_container_module.html#lxc-container-module)



### Lxd

- [lxd_container – Manage LXD Containers](https://docs.ansible.com/ansible/latest/modules/lxd_container_module.html#lxd-container-module)
- [lxd_profile – Manage LXD profiles](https://docs.ansible.com/ansible/latest/modules/lxd_profile_module.html#lxd-profile-module)



### Memset

- [memset_dns_reload – Request reload of Memset’s DNS infrastructure,](https://docs.ansible.com/ansible/latest/modules/memset_dns_reload_module.html#memset-dns-reload-module)
- [memset_memstore_info – Retrieve Memstore product usage information](https://docs.ansible.com/ansible/latest/modules/memset_memstore_info_module.html#memset-memstore-info-module)
- [memset_server_info – Retrieve server information](https://docs.ansible.com/ansible/latest/modules/memset_server_info_module.html#memset-server-info-module)
- [memset_zone – Creates and deletes Memset DNS zones](https://docs.ansible.com/ansible/latest/modules/memset_zone_module.html#memset-zone-module)
- [memset_zone_domain – Create and delete domains in Memset DNS zones](https://docs.ansible.com/ansible/latest/modules/memset_zone_domain_module.html#memset-zone-domain-module)
- [memset_zone_record – Create and delete records in Memset DNS zones](https://docs.ansible.com/ansible/latest/modules/memset_zone_record_module.html#memset-zone-record-module)



### Misc

- [cloud_init_data_facts – Retrieve facts of cloud-init](https://docs.ansible.com/ansible/latest/modules/cloud_init_data_facts_module.html#cloud-init-data-facts-module)
- [helm – Manages Kubernetes packages with the Helm package manager](https://docs.ansible.com/ansible/latest/modules/helm_module.html#helm-module)
- [ovirt – oVirt/RHEV platform management](https://docs.ansible.com/ansible/latest/modules/ovirt_module.html#ovirt-module)
- [proxmox – management of instances in Proxmox VE cluster](https://docs.ansible.com/ansible/latest/modules/proxmox_module.html#proxmox-module)
- [proxmox_kvm – Management of Qemu(KVM) Virtual Machines in Proxmox VE cluster](https://docs.ansible.com/ansible/latest/modules/proxmox_kvm_module.html#proxmox-kvm-module)
- [proxmox_template – management of OS templates in Proxmox VE cluster](https://docs.ansible.com/ansible/latest/modules/proxmox_template_module.html#proxmox-template-module)
- [rhevm – RHEV/oVirt automation](https://docs.ansible.com/ansible/latest/modules/rhevm_module.html#rhevm-module)
- [serverless – Manages a Serverless Framework project](https://docs.ansible.com/ansible/latest/modules/serverless_module.html#serverless-module)
- [terraform – Manages a Terraform deployment (and plans)](https://docs.ansible.com/ansible/latest/modules/terraform_module.html#terraform-module)
- [virt – Manages virtual machines supported by libvirt](https://docs.ansible.com/ansible/latest/modules/virt_module.html#virt-module)
- [virt_net – Manage libvirt network configuration](https://docs.ansible.com/ansible/latest/modules/virt_net_module.html#virt-net-module)
- [virt_pool – Manage libvirt storage pools](https://docs.ansible.com/ansible/latest/modules/virt_pool_module.html#virt-pool-module)
- [xenserver_facts – get facts reported on xenserver](https://docs.ansible.com/ansible/latest/modules/xenserver_facts_module.html#xenserver-facts-module)



### Oneandone

- [oneandone_firewall_policy – Configure 1&1 firewall policy](https://docs.ansible.com/ansible/latest/modules/oneandone_firewall_policy_module.html#oneandone-firewall-policy-module)
- [oneandone_load_balancer – Configure 1&1 load balancer](https://docs.ansible.com/ansible/latest/modules/oneandone_load_balancer_module.html#oneandone-load-balancer-module)
- [oneandone_monitoring_policy – Configure 1&1 monitoring policy](https://docs.ansible.com/ansible/latest/modules/oneandone_monitoring_policy_module.html#oneandone-monitoring-policy-module)
- [oneandone_private_network – Configure 1&1 private networking](https://docs.ansible.com/ansible/latest/modules/oneandone_private_network_module.html#oneandone-private-network-module)
- [oneandone_public_ip – Configure 1&1 public IPs](https://docs.ansible.com/ansible/latest/modules/oneandone_public_ip_module.html#oneandone-public-ip-module)
- [oneandone_server – Create, destroy, start, stop, and reboot a 1&1 Host server](https://docs.ansible.com/ansible/latest/modules/oneandone_server_module.html#oneandone-server-module)



### Online

- [online_server_facts – Gather facts about Online servers](https://docs.ansible.com/ansible/latest/modules/online_server_facts_module.html#online-server-facts-module) **(D)**
- [online_server_info – Gather information about Online servers](https://docs.ansible.com/ansible/latest/modules/online_server_info_module.html#online-server-info-module)
- [online_user_facts – Gather facts about Online user](https://docs.ansible.com/ansible/latest/modules/online_user_facts_module.html#online-user-facts-module) **(D)**
- [online_user_info – Gather information about Online user](https://docs.ansible.com/ansible/latest/modules/online_user_info_module.html#online-user-info-module)



### Opennebula

- [one_host – Manages OpenNebula Hosts](https://docs.ansible.com/ansible/latest/modules/one_host_module.html#one-host-module)
- [one_image – Manages OpenNebula images](https://docs.ansible.com/ansible/latest/modules/one_image_module.html#one-image-module)
- [one_image_info – Gather information on OpenNebula images](https://docs.ansible.com/ansible/latest/modules/one_image_info_module.html#one-image-info-module)
- [one_service – Deploy and manage OpenNebula services](https://docs.ansible.com/ansible/latest/modules/one_service_module.html#one-service-module)
- [one_vm – Creates or terminates OpenNebula instances](https://docs.ansible.com/ansible/latest/modules/one_vm_module.html#one-vm-module)



### Openstack

- [os_auth – Retrieve an auth token](https://docs.ansible.com/ansible/latest/modules/os_auth_module.html#os-auth-module)
- [os_client_config – Get OpenStack Client config](https://docs.ansible.com/ansible/latest/modules/os_client_config_module.html#os-client-config-module)
- [os_coe_cluster – Add/Remove COE cluster from OpenStack Cloud](https://docs.ansible.com/ansible/latest/modules/os_coe_cluster_module.html#os-coe-cluster-module)
- [os_coe_cluster_template – Add/Remove COE cluster template from OpenStack Cloud](https://docs.ansible.com/ansible/latest/modules/os_coe_cluster_template_module.html#os-coe-cluster-template-module)
- [os_flavor_info – Retrieve information about one or more flavors](https://docs.ansible.com/ansible/latest/modules/os_flavor_info_module.html#os-flavor-info-module)
- [os_floating_ip – Add/Remove floating IP from an instance](https://docs.ansible.com/ansible/latest/modules/os_floating_ip_module.html#os-floating-ip-module)
- [os_group – Manage OpenStack Identity Groups](https://docs.ansible.com/ansible/latest/modules/os_group_module.html#os-group-module)
- [os_group_info – Retrieve info about one or more OpenStack groups](https://docs.ansible.com/ansible/latest/modules/os_group_info_module.html#os-group-info-module)
- [os_image – Add/Delete images from OpenStack Cloud](https://docs.ansible.com/ansible/latest/modules/os_image_module.html#os-image-module)
- [os_image_info – Retrieve information about an image within OpenStack](https://docs.ansible.com/ansible/latest/modules/os_image_info_module.html#os-image-info-module)
- [os_ironic – Create/Delete Bare Metal Resources from OpenStack](https://docs.ansible.com/ansible/latest/modules/os_ironic_module.html#os-ironic-module)
- [os_ironic_inspect – Explicitly triggers baremetal node introspection in ironic](https://docs.ansible.com/ansible/latest/modules/os_ironic_inspect_module.html#os-ironic-inspect-module)
- [os_ironic_node – Activate/Deactivate Bare Metal Resources from OpenStack](https://docs.ansible.com/ansible/latest/modules/os_ironic_node_module.html#os-ironic-node-module)
- [os_keypair – Add/Delete a keypair from OpenStack](https://docs.ansible.com/ansible/latest/modules/os_keypair_module.html#os-keypair-module)
- [os_keystone_domain – Manage OpenStack Identity Domains](https://docs.ansible.com/ansible/latest/modules/os_keystone_domain_module.html#os-keystone-domain-module)
- [os_keystone_domain_info – Retrieve information about one or more OpenStack domains](https://docs.ansible.com/ansible/latest/modules/os_keystone_domain_info_module.html#os-keystone-domain-info-module)
- [os_keystone_endpoint – Manage OpenStack Identity service endpoints](https://docs.ansible.com/ansible/latest/modules/os_keystone_endpoint_module.html#os-keystone-endpoint-module)
- [os_keystone_role – Manage OpenStack Identity Roles](https://docs.ansible.com/ansible/latest/modules/os_keystone_role_module.html#os-keystone-role-module)
- [os_keystone_service – Manage OpenStack Identity services](https://docs.ansible.com/ansible/latest/modules/os_keystone_service_module.html#os-keystone-service-module)
- [os_listener – Add/Delete a listener for a load balancer from OpenStack Cloud](https://docs.ansible.com/ansible/latest/modules/os_listener_module.html#os-listener-module)
- [os_loadbalancer – Add/Delete load balancer from OpenStack Cloud](https://docs.ansible.com/ansible/latest/modules/os_loadbalancer_module.html#os-loadbalancer-module)
- [os_member – Add/Delete a member for a pool in load balancer from OpenStack Cloud](https://docs.ansible.com/ansible/latest/modules/os_member_module.html#os-member-module)
- [os_network – Creates/removes networks from OpenStack](https://docs.ansible.com/ansible/latest/modules/os_network_module.html#os-network-module)
- [os_networks_info – Retrieve information about one or more OpenStack networks](https://docs.ansible.com/ansible/latest/modules/os_networks_info_module.html#os-networks-info-module)
- [os_nova_flavor – Manage OpenStack compute flavors](https://docs.ansible.com/ansible/latest/modules/os_nova_flavor_module.html#os-nova-flavor-module)
- [os_nova_host_aggregate – Manage OpenStack host aggregates](https://docs.ansible.com/ansible/latest/modules/os_nova_host_aggregate_module.html#os-nova-host-aggregate-module)
- [os_object – Create or Delete objects and containers from OpenStack](https://docs.ansible.com/ansible/latest/modules/os_object_module.html#os-object-module)
- [os_pool – Add/Delete a pool in the load balancing service from OpenStack Cloud](https://docs.ansible.com/ansible/latest/modules/os_pool_module.html#os-pool-module)
- [os_port – Add/Update/Delete ports from an OpenStack cloud](https://docs.ansible.com/ansible/latest/modules/os_port_module.html#os-port-module)
- [os_port_info – Retrieve information about ports within OpenStack](https://docs.ansible.com/ansible/latest/modules/os_port_info_module.html#os-port-info-module)
- [os_project – Manage OpenStack Projects](https://docs.ansible.com/ansible/latest/modules/os_project_module.html#os-project-module)
- [os_project_access – Manage OpenStack compute flavors access](https://docs.ansible.com/ansible/latest/modules/os_project_access_module.html#os-project-access-module)
- [os_project_info – Retrieve information about one or more OpenStack projects](https://docs.ansible.com/ansible/latest/modules/os_project_info_module.html#os-project-info-module)
- [os_quota – Manage OpenStack Quotas](https://docs.ansible.com/ansible/latest/modules/os_quota_module.html#os-quota-module)
- [os_recordset – Manage OpenStack DNS recordsets](https://docs.ansible.com/ansible/latest/modules/os_recordset_module.html#os-recordset-module)
- [os_router – Create or delete routers from OpenStack](https://docs.ansible.com/ansible/latest/modules/os_router_module.html#os-router-module)
- [os_security_group – Add/Delete security groups from an OpenStack cloud](https://docs.ansible.com/ansible/latest/modules/os_security_group_module.html#os-security-group-module)
- [os_security_group_rule – Add/Delete rule from an existing security group](https://docs.ansible.com/ansible/latest/modules/os_security_group_rule_module.html#os-security-group-rule-module)
- [os_server – Create/Delete Compute Instances from OpenStack](https://docs.ansible.com/ansible/latest/modules/os_server_module.html#os-server-module)
- [os_server_action – Perform actions on Compute Instances from OpenStack](https://docs.ansible.com/ansible/latest/modules/os_server_action_module.html#os-server-action-module)
- [os_server_group – Manage OpenStack server groups](https://docs.ansible.com/ansible/latest/modules/os_server_group_module.html#os-server-group-module)
- [os_server_info – Retrieve information about one or more compute instances](https://docs.ansible.com/ansible/latest/modules/os_server_info_module.html#os-server-info-module)
- [os_server_metadata – Add/Update/Delete Metadata in Compute Instances from OpenStack](https://docs.ansible.com/ansible/latest/modules/os_server_metadata_module.html#os-server-metadata-module)
- [os_server_volume – Attach/Detach Volumes from OpenStack VM’s](https://docs.ansible.com/ansible/latest/modules/os_server_volume_module.html#os-server-volume-module)
- [os_stack – Add/Remove Heat Stack](https://docs.ansible.com/ansible/latest/modules/os_stack_module.html#os-stack-module)
- [os_subnet – Add/Remove subnet to an OpenStack network](https://docs.ansible.com/ansible/latest/modules/os_subnet_module.html#os-subnet-module)
- [os_subnets_info – Retrieve information about one or more OpenStack subnets](https://docs.ansible.com/ansible/latest/modules/os_subnets_info_module.html#os-subnets-info-module)
- [os_user – Manage OpenStack Identity Users](https://docs.ansible.com/ansible/latest/modules/os_user_module.html#os-user-module)
- [os_user_group – Associate OpenStack Identity users and groups](https://docs.ansible.com/ansible/latest/modules/os_user_group_module.html#os-user-group-module)
- [os_user_info – Retrieve information about one or more OpenStack users](https://docs.ansible.com/ansible/latest/modules/os_user_info_module.html#os-user-info-module)
- [os_user_role – Associate OpenStack Identity users and roles](https://docs.ansible.com/ansible/latest/modules/os_user_role_module.html#os-user-role-module)
- [os_volume – Create/Delete Cinder Volumes](https://docs.ansible.com/ansible/latest/modules/os_volume_module.html#os-volume-module)
- [os_volume_snapshot – Create/Delete Cinder Volume Snapshots](https://docs.ansible.com/ansible/latest/modules/os_volume_snapshot_module.html#os-volume-snapshot-module)
- [os_zone – Manage OpenStack DNS zones](https://docs.ansible.com/ansible/latest/modules/os_zone_module.html#os-zone-module)



### Oracle

- [oci_vcn – Manage Virtual Cloud Networks(VCN) in OCI](https://docs.ansible.com/ansible/latest/modules/oci_vcn_module.html#oci-vcn-module)



### Ovh

- [ovh_ip_failover – Manage OVH IP failover address](https://docs.ansible.com/ansible/latest/modules/ovh_ip_failover_module.html#ovh-ip-failover-module)
- [ovh_ip_loadbalancing_backend – Manage OVH IP LoadBalancing backends](https://docs.ansible.com/ansible/latest/modules/ovh_ip_loadbalancing_backend_module.html#ovh-ip-loadbalancing-backend-module)



### Ovirt

- [ovirt_affinity_group – Module to manage affinity groups in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_affinity_group_module.html#ovirt-affinity-group-module)
- [ovirt_affinity_label – Module to manage affinity labels in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_affinity_label_module.html#ovirt-affinity-label-module)
- [ovirt_affinity_label_info – Retrieve information about one or more oVirt/RHV affinity labels](https://docs.ansible.com/ansible/latest/modules/ovirt_affinity_label_info_module.html#ovirt-affinity-label-info-module)
- [ovirt_api_info – Retrieve information about the oVirt/RHV API](https://docs.ansible.com/ansible/latest/modules/ovirt_api_info_module.html#ovirt-api-info-module)
- [ovirt_auth – Module to manage authentication to oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_auth_module.html#ovirt-auth-module)
- [ovirt_cluster – Module to manage clusters in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_cluster_module.html#ovirt-cluster-module)
- [ovirt_cluster_info – Retrieve information about one or more oVirt/RHV clusters](https://docs.ansible.com/ansible/latest/modules/ovirt_cluster_info_module.html#ovirt-cluster-info-module)
- [ovirt_datacenter – Module to manage data centers in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_datacenter_module.html#ovirt-datacenter-module)
- [ovirt_datacenter_info – Retrieve information about one or more oVirt/RHV datacenters](https://docs.ansible.com/ansible/latest/modules/ovirt_datacenter_info_module.html#ovirt-datacenter-info-module)
- [ovirt_disk – Module to manage Virtual Machine and floating disks in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_disk_module.html#ovirt-disk-module)
- [ovirt_disk_info – Retrieve information about one or more oVirt/RHV disks](https://docs.ansible.com/ansible/latest/modules/ovirt_disk_info_module.html#ovirt-disk-info-module)
- [ovirt_event – Create or delete an event in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_event_module.html#ovirt-event-module)
- [ovirt_event_info – This module can be used to retrieve information about one or more oVirt/RHV events](https://docs.ansible.com/ansible/latest/modules/ovirt_event_info_module.html#ovirt-event-info-module)
- [ovirt_external_provider – Module to manage external providers in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_external_provider_module.html#ovirt-external-provider-module)
- [ovirt_external_provider_info – Retrieve information about one or more oVirt/RHV external providers](https://docs.ansible.com/ansible/latest/modules/ovirt_external_provider_info_module.html#ovirt-external-provider-info-module)
- [ovirt_group – Module to manage groups in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_group_module.html#ovirt-group-module)
- [ovirt_group_info – Retrieve information about one or more oVirt/RHV groups](https://docs.ansible.com/ansible/latest/modules/ovirt_group_info_module.html#ovirt-group-info-module)
- [ovirt_host – Module to manage hosts in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_host_module.html#ovirt-host-module)
- [ovirt_host_info – Retrieve information about one or more oVirt/RHV hosts](https://docs.ansible.com/ansible/latest/modules/ovirt_host_info_module.html#ovirt-host-info-module)
- [ovirt_host_network – Module to manage host networks in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_host_network_module.html#ovirt-host-network-module)
- [ovirt_host_pm – Module to manage power management of hosts in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_host_pm_module.html#ovirt-host-pm-module)
- [ovirt_host_storage_info – Retrieve information about one or more oVirt/RHV HostStorages (applicable only for block storage)](https://docs.ansible.com/ansible/latest/modules/ovirt_host_storage_info_module.html#ovirt-host-storage-info-module)
- [ovirt_instance_type – Module to manage Instance Types in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_instance_type_module.html#ovirt-instance-type-module)
- [ovirt_job – Module to manage jobs in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_job_module.html#ovirt-job-module)
- [ovirt_mac_pool – Module to manage MAC pools in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_mac_pool_module.html#ovirt-mac-pool-module)
- [ovirt_network – Module to manage logical networks in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_network_module.html#ovirt-network-module)
- [ovirt_network_info – Retrieve information about one or more oVirt/RHV networks](https://docs.ansible.com/ansible/latest/modules/ovirt_network_info_module.html#ovirt-network-info-module)
- [ovirt_nic – Module to manage network interfaces of Virtual Machines in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_nic_module.html#ovirt-nic-module)
- [ovirt_nic_info – Retrieve information about one or more oVirt/RHV virtual machine network interfaces](https://docs.ansible.com/ansible/latest/modules/ovirt_nic_info_module.html#ovirt-nic-info-module)
- [ovirt_permission – Module to manage permissions of users/groups in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_permission_module.html#ovirt-permission-module)
- [ovirt_permission_info – Retrieve information about one or more oVirt/RHV permissions](https://docs.ansible.com/ansible/latest/modules/ovirt_permission_info_module.html#ovirt-permission-info-module)
- [ovirt_quota – Module to manage datacenter quotas in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_quota_module.html#ovirt-quota-module)
- [ovirt_quota_info – Retrieve information about one or more oVirt/RHV quotas](https://docs.ansible.com/ansible/latest/modules/ovirt_quota_info_module.html#ovirt-quota-info-module)
- [ovirt_role – Module to manage roles in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_role_module.html#ovirt-role-module)
- [ovirt_scheduling_policy_info – Retrieve information about one or more oVirt scheduling policies](https://docs.ansible.com/ansible/latest/modules/ovirt_scheduling_policy_info_module.html#ovirt-scheduling-policy-info-module)
- [ovirt_snapshot – Module to manage Virtual Machine Snapshots in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_snapshot_module.html#ovirt-snapshot-module)
- [ovirt_snapshot_info – Retrieve information about one or more oVirt/RHV virtual machine snapshots](https://docs.ansible.com/ansible/latest/modules/ovirt_snapshot_info_module.html#ovirt-snapshot-info-module)
- [ovirt_storage_connection – Module to manage storage connections in oVirt](https://docs.ansible.com/ansible/latest/modules/ovirt_storage_connection_module.html#ovirt-storage-connection-module)
- [ovirt_storage_domain – Module to manage storage domains in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_storage_domain_module.html#ovirt-storage-domain-module)
- [ovirt_storage_domain_info – Retrieve information about one or more oVirt/RHV storage domains](https://docs.ansible.com/ansible/latest/modules/ovirt_storage_domain_info_module.html#ovirt-storage-domain-info-module)
- [ovirt_storage_template_info – Retrieve information about one or more oVirt/RHV templates relate to a storage domain](https://docs.ansible.com/ansible/latest/modules/ovirt_storage_template_info_module.html#ovirt-storage-template-info-module)
- [ovirt_storage_vm_info – Retrieve information about one or more oVirt/RHV virtual machines relate to a storage domain](https://docs.ansible.com/ansible/latest/modules/ovirt_storage_vm_info_module.html#ovirt-storage-vm-info-module)
- [ovirt_tag – Module to manage tags in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_tag_module.html#ovirt-tag-module)
- [ovirt_tag_info – Retrieve information about one or more oVirt/RHV tags](https://docs.ansible.com/ansible/latest/modules/ovirt_tag_info_module.html#ovirt-tag-info-module)
- [ovirt_template – Module to manage virtual machine templates in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_template_module.html#ovirt-template-module)
- [ovirt_template_info – Retrieve information about one or more oVirt/RHV templates](https://docs.ansible.com/ansible/latest/modules/ovirt_template_info_module.html#ovirt-template-info-module)
- [ovirt_user – Module to manage users in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_user_module.html#ovirt-user-module)
- [ovirt_user_info – Retrieve information about one or more oVirt/RHV users](https://docs.ansible.com/ansible/latest/modules/ovirt_user_info_module.html#ovirt-user-info-module)
- [ovirt_vm – Module to manage Virtual Machines in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_vm_module.html#ovirt-vm-module)
- [ovirt_vm_info – Retrieve information about one or more oVirt/RHV virtual machines](https://docs.ansible.com/ansible/latest/modules/ovirt_vm_info_module.html#ovirt-vm-info-module)
- [ovirt_vmpool – Module to manage VM pools in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_vmpool_module.html#ovirt-vmpool-module)
- [ovirt_vmpool_info – Retrieve information about one or more oVirt/RHV vmpools](https://docs.ansible.com/ansible/latest/modules/ovirt_vmpool_info_module.html#ovirt-vmpool-info-module)
- [ovirt_vnic_profile – Module to manage vNIC profile of network in oVirt/RHV](https://docs.ansible.com/ansible/latest/modules/ovirt_vnic_profile_module.html#ovirt-vnic-profile-module)



### Packet

- [packet_device – Manage a bare metal server in the Packet Host](https://docs.ansible.com/ansible/latest/modules/packet_device_module.html#packet-device-module)
- [packet_sshkey – Create/delete an SSH key in Packet host](https://docs.ansible.com/ansible/latest/modules/packet_sshkey_module.html#packet-sshkey-module)



### Podman

- [podman_image – Pull images for use by podman](https://docs.ansible.com/ansible/latest/modules/podman_image_module.html#podman-image-module)
- [podman_image_info – Gather info about images using podman](https://docs.ansible.com/ansible/latest/modules/podman_image_info_module.html#podman-image-info-module)



### Profitbricks

- [profitbricks – Create, destroy, start, stop, and reboot a ProfitBricks virtual machine](https://docs.ansible.com/ansible/latest/modules/profitbricks_module.html#profitbricks-module)
- [profitbricks_datacenter – Create or destroy a ProfitBricks Virtual Datacenter](https://docs.ansible.com/ansible/latest/modules/profitbricks_datacenter_module.html#profitbricks-datacenter-module)
- [profitbricks_nic – Create or Remove a NIC](https://docs.ansible.com/ansible/latest/modules/profitbricks_nic_module.html#profitbricks-nic-module)
- [profitbricks_volume – Create or destroy a volume](https://docs.ansible.com/ansible/latest/modules/profitbricks_volume_module.html#profitbricks-volume-module)
- [profitbricks_volume_attachments – Attach or detach a volume](https://docs.ansible.com/ansible/latest/modules/profitbricks_volume_attachments_module.html#profitbricks-volume-attachments-module)



### Pubnub

- [pubnub_blocks – PubNub blocks management module](https://docs.ansible.com/ansible/latest/modules/pubnub_blocks_module.html#pubnub-blocks-module)



### Rackspace

- [rax – create / delete an instance in Rackspace Public Cloud](https://docs.ansible.com/ansible/latest/modules/rax_module.html#rax-module)
- [rax_cbs – Manipulate Rackspace Cloud Block Storage Volumes](https://docs.ansible.com/ansible/latest/modules/rax_cbs_module.html#rax-cbs-module)
- [rax_cbs_attachments – Manipulate Rackspace Cloud Block Storage Volume Attachments](https://docs.ansible.com/ansible/latest/modules/rax_cbs_attachments_module.html#rax-cbs-attachments-module)
- [rax_cdb – create/delete or resize a Rackspace Cloud Databases instance](https://docs.ansible.com/ansible/latest/modules/rax_cdb_module.html#rax-cdb-module)
- [rax_cdb_database – create / delete a database in the Cloud Databases](https://docs.ansible.com/ansible/latest/modules/rax_cdb_database_module.html#rax-cdb-database-module)
- [rax_cdb_user – create / delete a Rackspace Cloud Database](https://docs.ansible.com/ansible/latest/modules/rax_cdb_user_module.html#rax-cdb-user-module)
- [rax_clb – create / delete a load balancer in Rackspace Public Cloud](https://docs.ansible.com/ansible/latest/modules/rax_clb_module.html#rax-clb-module)
- [rax_clb_nodes – add, modify and remove nodes from a Rackspace Cloud Load Balancer](https://docs.ansible.com/ansible/latest/modules/rax_clb_nodes_module.html#rax-clb-nodes-module)
- [rax_clb_ssl – Manage SSL termination for a Rackspace Cloud Load Balancer](https://docs.ansible.com/ansible/latest/modules/rax_clb_ssl_module.html#rax-clb-ssl-module)
- [rax_dns – Manage domains on Rackspace Cloud DNS](https://docs.ansible.com/ansible/latest/modules/rax_dns_module.html#rax-dns-module)
- [rax_dns_record – Manage DNS records on Rackspace Cloud DNS](https://docs.ansible.com/ansible/latest/modules/rax_dns_record_module.html#rax-dns-record-module)
- [rax_facts – Gather facts for Rackspace Cloud Servers](https://docs.ansible.com/ansible/latest/modules/rax_facts_module.html#rax-facts-module)
- [rax_files – Manipulate Rackspace Cloud Files Containers](https://docs.ansible.com/ansible/latest/modules/rax_files_module.html#rax-files-module)
- [rax_files_objects – Upload, download, and delete objects in Rackspace Cloud Files](https://docs.ansible.com/ansible/latest/modules/rax_files_objects_module.html#rax-files-objects-module)
- [rax_identity – Load Rackspace Cloud Identity](https://docs.ansible.com/ansible/latest/modules/rax_identity_module.html#rax-identity-module)
- [rax_keypair – Create a keypair for use with Rackspace Cloud Servers](https://docs.ansible.com/ansible/latest/modules/rax_keypair_module.html#rax-keypair-module)
- [rax_meta – Manipulate metadata for Rackspace Cloud Servers](https://docs.ansible.com/ansible/latest/modules/rax_meta_module.html#rax-meta-module)
- [rax_mon_alarm – Create or delete a Rackspace Cloud Monitoring alarm](https://docs.ansible.com/ansible/latest/modules/rax_mon_alarm_module.html#rax-mon-alarm-module)
- [rax_mon_check – Create or delete a Rackspace Cloud Monitoring check for an existing entity](https://docs.ansible.com/ansible/latest/modules/rax_mon_check_module.html#rax-mon-check-module)
- [rax_mon_entity – Create or delete a Rackspace Cloud Monitoring entity](https://docs.ansible.com/ansible/latest/modules/rax_mon_entity_module.html#rax-mon-entity-module)
- [rax_mon_notification – Create or delete a Rackspace Cloud Monitoring notification](https://docs.ansible.com/ansible/latest/modules/rax_mon_notification_module.html#rax-mon-notification-module)
- [rax_mon_notification_plan – Create or delete a Rackspace Cloud Monitoring notification plan](https://docs.ansible.com/ansible/latest/modules/rax_mon_notification_plan_module.html#rax-mon-notification-plan-module)
- [rax_network – create / delete an isolated network in Rackspace Public Cloud](https://docs.ansible.com/ansible/latest/modules/rax_network_module.html#rax-network-module)
- [rax_queue – create / delete a queue in Rackspace Public Cloud](https://docs.ansible.com/ansible/latest/modules/rax_queue_module.html#rax-queue-module)
- [rax_scaling_group – Manipulate Rackspace Cloud Autoscale Groups](https://docs.ansible.com/ansible/latest/modules/rax_scaling_group_module.html#rax-scaling-group-module)
- [rax_scaling_policy – Manipulate Rackspace Cloud Autoscale Scaling Policy](https://docs.ansible.com/ansible/latest/modules/rax_scaling_policy_module.html#rax-scaling-policy-module)



### Scaleway

- [scaleway_compute – Scaleway compute management module](https://docs.ansible.com/ansible/latest/modules/scaleway_compute_module.html#scaleway-compute-module)
- [scaleway_image_facts – Gather facts about the Scaleway images available](https://docs.ansible.com/ansible/latest/modules/scaleway_image_facts_module.html#scaleway-image-facts-module) **(D)**
- [scaleway_image_info – Gather information about the Scaleway images available](https://docs.ansible.com/ansible/latest/modules/scaleway_image_info_module.html#scaleway-image-info-module)
- [scaleway_ip – Scaleway IP management module](https://docs.ansible.com/ansible/latest/modules/scaleway_ip_module.html#scaleway-ip-module)
- [scaleway_ip_facts – Gather facts about the Scaleway ips available](https://docs.ansible.com/ansible/latest/modules/scaleway_ip_facts_module.html#scaleway-ip-facts-module) **(D)**
- [scaleway_ip_info – Gather information about the Scaleway ips available](https://docs.ansible.com/ansible/latest/modules/scaleway_ip_info_module.html#scaleway-ip-info-module)
- [scaleway_lb – Scaleway load-balancer management module](https://docs.ansible.com/ansible/latest/modules/scaleway_lb_module.html#scaleway-lb-module)
- [scaleway_organization_facts – Gather facts about the Scaleway organizations available](https://docs.ansible.com/ansible/latest/modules/scaleway_organization_facts_module.html#scaleway-organization-facts-module) **(D)**
- [scaleway_organization_info – Gather information about the Scaleway organizations available](https://docs.ansible.com/ansible/latest/modules/scaleway_organization_info_module.html#scaleway-organization-info-module)
- [scaleway_security_group – Scaleway Security Group management module](https://docs.ansible.com/ansible/latest/modules/scaleway_security_group_module.html#scaleway-security-group-module)
- [scaleway_security_group_facts – Gather facts about the Scaleway security groups available](https://docs.ansible.com/ansible/latest/modules/scaleway_security_group_facts_module.html#scaleway-security-group-facts-module) **(D)**
- [scaleway_security_group_info – Gather information about the Scaleway security groups available](https://docs.ansible.com/ansible/latest/modules/scaleway_security_group_info_module.html#scaleway-security-group-info-module)
- [scaleway_security_group_rule – Scaleway Security Group Rule management module](https://docs.ansible.com/ansible/latest/modules/scaleway_security_group_rule_module.html#scaleway-security-group-rule-module)
- [scaleway_server_facts – Gather facts about the Scaleway servers available](https://docs.ansible.com/ansible/latest/modules/scaleway_server_facts_module.html#scaleway-server-facts-module) **(D)**
- [scaleway_server_info – Gather information about the Scaleway servers available](https://docs.ansible.com/ansible/latest/modules/scaleway_server_info_module.html#scaleway-server-info-module)
- [scaleway_snapshot_facts – Gather facts about the Scaleway snapshots available](https://docs.ansible.com/ansible/latest/modules/scaleway_snapshot_facts_module.html#scaleway-snapshot-facts-module) **(D)**
- [scaleway_snapshot_info – Gather information about the Scaleway snapshots available](https://docs.ansible.com/ansible/latest/modules/scaleway_snapshot_info_module.html#scaleway-snapshot-info-module)
- [scaleway_sshkey – Scaleway SSH keys management module](https://docs.ansible.com/ansible/latest/modules/scaleway_sshkey_module.html#scaleway-sshkey-module)
- [scaleway_user_data – Scaleway user_data management module](https://docs.ansible.com/ansible/latest/modules/scaleway_user_data_module.html#scaleway-user-data-module)
- [scaleway_volume – Scaleway volumes management module](https://docs.ansible.com/ansible/latest/modules/scaleway_volume_module.html#scaleway-volume-module)
- [scaleway_volume_facts – Gather facts about the Scaleway volumes available](https://docs.ansible.com/ansible/latest/modules/scaleway_volume_facts_module.html#scaleway-volume-facts-module) **(D)**
- [scaleway_volume_info – Gather information about the Scaleway volumes available](https://docs.ansible.com/ansible/latest/modules/scaleway_volume_info_module.html#scaleway-volume-info-module)



### Smartos

- [imgadm – Manage SmartOS images](https://docs.ansible.com/ansible/latest/modules/imgadm_module.html#imgadm-module)
- [nictagadm – Manage nic tags on SmartOS systems](https://docs.ansible.com/ansible/latest/modules/nictagadm_module.html#nictagadm-module)
- [smartos_image_info – Get SmartOS image details](https://docs.ansible.com/ansible/latest/modules/smartos_image_info_module.html#smartos-image-info-module)
- [vmadm – Manage SmartOS virtual machines and zones](https://docs.ansible.com/ansible/latest/modules/vmadm_module.html#vmadm-module)



### Softlayer

- [sl_vm – create or cancel a virtual instance in SoftLayer](https://docs.ansible.com/ansible/latest/modules/sl_vm_module.html#sl-vm-module)



### Spotinst

- [spotinst_aws_elastigroup – Create, update or delete Spotinst AWS Elastigroups](https://docs.ansible.com/ansible/latest/modules/spotinst_aws_elastigroup_module.html#spotinst-aws-elastigroup-module)



### Univention

- [udm_dns_record – Manage dns entries on a univention corporate server](https://docs.ansible.com/ansible/latest/modules/udm_dns_record_module.html#udm-dns-record-module)
- [udm_dns_zone – Manage dns zones on a univention corporate server](https://docs.ansible.com/ansible/latest/modules/udm_dns_zone_module.html#udm-dns-zone-module)
- [udm_group – Manage of the posix group](https://docs.ansible.com/ansible/latest/modules/udm_group_module.html#udm-group-module)
- [udm_share – Manage samba shares on a univention corporate server](https://docs.ansible.com/ansible/latest/modules/udm_share_module.html#udm-share-module)
- [udm_user – Manage posix users on a univention corporate server](https://docs.ansible.com/ansible/latest/modules/udm_user_module.html#udm-user-module)



### Vmware

- [vca_fw – add remove firewall rules in a gateway in a vca](https://docs.ansible.com/ansible/latest/modules/vca_fw_module.html#vca-fw-module)
- [vca_nat – add remove nat rules in a gateway in a vca](https://docs.ansible.com/ansible/latest/modules/vca_nat_module.html#vca-nat-module)
- [vca_vapp – Manages vCloud Air vApp instances](https://docs.ansible.com/ansible/latest/modules/vca_vapp_module.html#vca-vapp-module)
- [vcenter_extension – Register/deregister vCenter Extensions](https://docs.ansible.com/ansible/latest/modules/vcenter_extension_module.html#vcenter-extension-module)
- [vcenter_extension_facts – Gather facts vCenter extensions](https://docs.ansible.com/ansible/latest/modules/vcenter_extension_facts_module.html#vcenter-extension-facts-module) **(D)**
- [vcenter_extension_info – Gather info vCenter extensions](https://docs.ansible.com/ansible/latest/modules/vcenter_extension_info_module.html#vcenter-extension-info-module)
- [vcenter_folder – Manage folders on given datacenter](https://docs.ansible.com/ansible/latest/modules/vcenter_folder_module.html#vcenter-folder-module)
- [vcenter_license – Manage VMware vCenter license keys](https://docs.ansible.com/ansible/latest/modules/vcenter_license_module.html#vcenter-license-module)
- [vmware_about_facts – Provides information about VMware server to which user is connecting to](https://docs.ansible.com/ansible/latest/modules/vmware_about_facts_module.html#vmware-about-facts-module) **(D)**
- [vmware_about_info – Provides information about VMware server to which user is connecting to](https://docs.ansible.com/ansible/latest/modules/vmware_about_info_module.html#vmware-about-info-module)
- [vmware_category – Manage VMware categories](https://docs.ansible.com/ansible/latest/modules/vmware_category_module.html#vmware-category-module)
- [vmware_category_facts – Gather facts about VMware tag categories](https://docs.ansible.com/ansible/latest/modules/vmware_category_facts_module.html#vmware-category-facts-module) **(D)**
- [vmware_category_info – Gather info about VMware tag categories](https://docs.ansible.com/ansible/latest/modules/vmware_category_info_module.html#vmware-category-info-module)
- [vmware_cfg_backup – Backup / Restore / Reset ESXi host configuration](https://docs.ansible.com/ansible/latest/modules/vmware_cfg_backup_module.html#vmware-cfg-backup-module)
- [vmware_cluster – Manage VMware vSphere clusters](https://docs.ansible.com/ansible/latest/modules/vmware_cluster_module.html#vmware-cluster-module)
- [vmware_cluster_drs – Manage Distributed Resource Scheduler (DRS) on VMware vSphere clusters](https://docs.ansible.com/ansible/latest/modules/vmware_cluster_drs_module.html#vmware-cluster-drs-module)
- [vmware_cluster_ha – Manage High Availability (HA) on VMware vSphere clusters](https://docs.ansible.com/ansible/latest/modules/vmware_cluster_ha_module.html#vmware-cluster-ha-module)
- [vmware_cluster_info – Gather info about clusters available in given vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_cluster_info_module.html#vmware-cluster-info-module)
- [vmware_cluster_vsan – Manages virtual storage area network (vSAN) configuration on VMware vSphere clusters](https://docs.ansible.com/ansible/latest/modules/vmware_cluster_vsan_module.html#vmware-cluster-vsan-module)
- [vmware_content_deploy_template – Deploy Virtual Machine from template stored in content library](https://docs.ansible.com/ansible/latest/modules/vmware_content_deploy_template_module.html#vmware-content-deploy-template-module)
- [vmware_content_library_info – Gather information about VMware Content Library](https://docs.ansible.com/ansible/latest/modules/vmware_content_library_info_module.html#vmware-content-library-info-module)
- [vmware_content_library_manager – Create, update and delete VMware content library](https://docs.ansible.com/ansible/latest/modules/vmware_content_library_manager_module.html#vmware-content-library-manager-module)
- [vmware_datacenter – Manage VMware vSphere Datacenters](https://docs.ansible.com/ansible/latest/modules/vmware_datacenter_module.html#vmware-datacenter-module)
- [vmware_datastore_cluster – Manage VMware vSphere datastore clusters](https://docs.ansible.com/ansible/latest/modules/vmware_datastore_cluster_module.html#vmware-datastore-cluster-module)
- [vmware_datastore_info – Gather info about datastores available in given vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_datastore_info_module.html#vmware-datastore-info-module)
- [vmware_datastore_maintenancemode – Place a datastore into maintenance mode](https://docs.ansible.com/ansible/latest/modules/vmware_datastore_maintenancemode_module.html#vmware-datastore-maintenancemode-module)
- [vmware_deploy_ovf – Deploys a VMware virtual machine from an OVF or OVA file](https://docs.ansible.com/ansible/latest/modules/vmware_deploy_ovf_module.html#vmware-deploy-ovf-module)
- [vmware_dns_config – Manage VMware ESXi DNS Configuration](https://docs.ansible.com/ansible/latest/modules/vmware_dns_config_module.html#vmware-dns-config-module)
- [vmware_drs_group – Creates vm/host group in a given cluster](https://docs.ansible.com/ansible/latest/modules/vmware_drs_group_module.html#vmware-drs-group-module)
- [vmware_drs_group_facts – Gathers facts about DRS VM/Host groups on the given cluster](https://docs.ansible.com/ansible/latest/modules/vmware_drs_group_facts_module.html#vmware-drs-group-facts-module) **(D)**
- [vmware_drs_group_info – Gathers info about DRS VM/Host groups on the given cluster](https://docs.ansible.com/ansible/latest/modules/vmware_drs_group_info_module.html#vmware-drs-group-info-module)
- [vmware_drs_rule_facts – Gathers facts about DRS rule on the given cluster](https://docs.ansible.com/ansible/latest/modules/vmware_drs_rule_facts_module.html#vmware-drs-rule-facts-module) **(D)**
- [vmware_drs_rule_info – Gathers info about DRS rule on the given cluster](https://docs.ansible.com/ansible/latest/modules/vmware_drs_rule_info_module.html#vmware-drs-rule-info-module)
- [vmware_dvs_host – Add or remove a host from distributed virtual switch](https://docs.ansible.com/ansible/latest/modules/vmware_dvs_host_module.html#vmware-dvs-host-module)
- [vmware_dvs_portgroup – Create or remove a Distributed vSwitch portgroup](https://docs.ansible.com/ansible/latest/modules/vmware_dvs_portgroup_module.html#vmware-dvs-portgroup-module)
- [vmware_dvs_portgroup_facts – Gathers facts DVS portgroup configurations](https://docs.ansible.com/ansible/latest/modules/vmware_dvs_portgroup_facts_module.html#vmware-dvs-portgroup-facts-module) **(D)**
- [vmware_dvs_portgroup_find – Find portgroup(s) in a VMware environment](https://docs.ansible.com/ansible/latest/modules/vmware_dvs_portgroup_find_module.html#vmware-dvs-portgroup-find-module)
- [vmware_dvs_portgroup_info – Gathers info DVS portgroup configurations](https://docs.ansible.com/ansible/latest/modules/vmware_dvs_portgroup_info_module.html#vmware-dvs-portgroup-info-module)
- [vmware_dvswitch – Create or remove a Distributed Switch](https://docs.ansible.com/ansible/latest/modules/vmware_dvswitch_module.html#vmware-dvswitch-module)
- [vmware_dvswitch_lacp – Manage LACP configuration on a Distributed Switch](https://docs.ansible.com/ansible/latest/modules/vmware_dvswitch_lacp_module.html#vmware-dvswitch-lacp-module)
- [vmware_dvswitch_nioc – Manage distributed switch Network IO Control](https://docs.ansible.com/ansible/latest/modules/vmware_dvswitch_nioc_module.html#vmware-dvswitch-nioc-module)
- [vmware_dvswitch_pvlans – Manage Private VLAN configuration of a Distributed Switch](https://docs.ansible.com/ansible/latest/modules/vmware_dvswitch_pvlans_module.html#vmware-dvswitch-pvlans-module)
- [vmware_dvswitch_uplink_pg – Manage uplink portproup configuration of a Distributed Switch](https://docs.ansible.com/ansible/latest/modules/vmware_dvswitch_uplink_pg_module.html#vmware-dvswitch-uplink-pg-module)
- [vmware_evc_mode – Enable/Disable EVC mode on vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_evc_mode_module.html#vmware-evc-mode-module)
- [vmware_export_ovf – Exports a VMware virtual machine to an OVF file, device files and a manifest file](https://docs.ansible.com/ansible/latest/modules/vmware_export_ovf_module.html#vmware-export-ovf-module)
- [vmware_folder_info – Provides information about folders in a datacenter](https://docs.ansible.com/ansible/latest/modules/vmware_folder_info_module.html#vmware-folder-info-module)
- [vmware_guest – Manages virtual machines in vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_guest_module.html#vmware-guest-module)
- [vmware_guest_boot_facts – Gather facts about boot options for the given virtual machine](https://docs.ansible.com/ansible/latest/modules/vmware_guest_boot_facts_module.html#vmware-guest-boot-facts-module) **(D)**
- [vmware_guest_boot_info – Gather info about boot options for the given virtual machine](https://docs.ansible.com/ansible/latest/modules/vmware_guest_boot_info_module.html#vmware-guest-boot-info-module)
- [vmware_guest_boot_manager – Manage boot options for the given virtual machine](https://docs.ansible.com/ansible/latest/modules/vmware_guest_boot_manager_module.html#vmware-guest-boot-manager-module)
- [vmware_guest_custom_attribute_defs – Manage custom attributes definitions for virtual machine from VMware](https://docs.ansible.com/ansible/latest/modules/vmware_guest_custom_attribute_defs_module.html#vmware-guest-custom-attribute-defs-module)
- [vmware_guest_custom_attributes – Manage custom attributes from VMware for the given virtual machine](https://docs.ansible.com/ansible/latest/modules/vmware_guest_custom_attributes_module.html#vmware-guest-custom-attributes-module)
- [vmware_guest_customization_facts – Gather facts about VM customization specifications](https://docs.ansible.com/ansible/latest/modules/vmware_guest_customization_facts_module.html#vmware-guest-customization-facts-module) **(D)**
- [vmware_guest_customization_info – Gather info about VM customization specifications](https://docs.ansible.com/ansible/latest/modules/vmware_guest_customization_info_module.html#vmware-guest-customization-info-module)
- [vmware_guest_disk – Manage disks related to virtual machine in given vCenter infrastructure](https://docs.ansible.com/ansible/latest/modules/vmware_guest_disk_module.html#vmware-guest-disk-module)
- [vmware_guest_disk_facts – Gather facts about disks of given virtual machine](https://docs.ansible.com/ansible/latest/modules/vmware_guest_disk_facts_module.html#vmware-guest-disk-facts-module) **(D)**
- [vmware_guest_disk_info – Gather info about disks of given virtual machine](https://docs.ansible.com/ansible/latest/modules/vmware_guest_disk_info_module.html#vmware-guest-disk-info-module)
- [vmware_guest_file_operation – Files operation in a VMware guest operating system without network](https://docs.ansible.com/ansible/latest/modules/vmware_guest_file_operation_module.html#vmware-guest-file-operation-module)
- [vmware_guest_find – Find the folder path(s) for a virtual machine by name or UUID](https://docs.ansible.com/ansible/latest/modules/vmware_guest_find_module.html#vmware-guest-find-module)
- [vmware_guest_info – Gather info about a single VM](https://docs.ansible.com/ansible/latest/modules/vmware_guest_info_module.html#vmware-guest-info-module)
- [vmware_guest_move – Moves virtual machines in vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_guest_move_module.html#vmware-guest-move-module)
- [vmware_guest_network – Manage network adapters of specified virtual machine in given vCenter infrastructure](https://docs.ansible.com/ansible/latest/modules/vmware_guest_network_module.html#vmware-guest-network-module)
- [vmware_guest_powerstate – Manages power states of virtual machines in vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_guest_powerstate_module.html#vmware-guest-powerstate-module)
- [vmware_guest_screenshot – Create a screenshot of the Virtual Machine console](https://docs.ansible.com/ansible/latest/modules/vmware_guest_screenshot_module.html#vmware-guest-screenshot-module)
- [vmware_guest_sendkey – Send USB HID codes to the Virtual Machine’s keyboard](https://docs.ansible.com/ansible/latest/modules/vmware_guest_sendkey_module.html#vmware-guest-sendkey-module)
- [vmware_guest_snapshot – Manages virtual machines snapshots in vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_guest_snapshot_module.html#vmware-guest-snapshot-module)
- [vmware_guest_snapshot_info – Gather info about virtual machine’s snapshots in vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_guest_snapshot_info_module.html#vmware-guest-snapshot-info-module)
- [vmware_guest_tools_upgrade – Module to upgrade VMTools](https://docs.ansible.com/ansible/latest/modules/vmware_guest_tools_upgrade_module.html#vmware-guest-tools-upgrade-module)
- [vmware_guest_tools_wait – Wait for VMware tools to become available](https://docs.ansible.com/ansible/latest/modules/vmware_guest_tools_wait_module.html#vmware-guest-tools-wait-module)
- [vmware_guest_video – Modify video card configurations of specified virtual machine in given vCenter infrastructure](https://docs.ansible.com/ansible/latest/modules/vmware_guest_video_module.html#vmware-guest-video-module)
- [vmware_guest_vnc – Manages VNC remote display on virtual machines in vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_guest_vnc_module.html#vmware-guest-vnc-module)
- [vmware_host – Add, remove, or move an ESXi host to, from, or within vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_host_module.html#vmware-host-module)
- [vmware_host_acceptance – Manage the host acceptance level of an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_acceptance_module.html#vmware-host-acceptance-module)
- [vmware_host_active_directory – Joins an ESXi host system to an Active Directory domain or leaves it](https://docs.ansible.com/ansible/latest/modules/vmware_host_active_directory_module.html#vmware-host-active-directory-module)
- [vmware_host_capability_facts – Gathers facts about an ESXi host’s capability information](https://docs.ansible.com/ansible/latest/modules/vmware_host_capability_facts_module.html#vmware-host-capability-facts-module) **(D)**
- [vmware_host_capability_info – Gathers info about an ESXi host’s capability information](https://docs.ansible.com/ansible/latest/modules/vmware_host_capability_info_module.html#vmware-host-capability-info-module)
- [vmware_host_config_facts – Gathers facts about an ESXi host’s advance configuration information](https://docs.ansible.com/ansible/latest/modules/vmware_host_config_facts_module.html#vmware-host-config-facts-module) **(D)**
- [vmware_host_config_info – Gathers info about an ESXi host’s advance configuration information](https://docs.ansible.com/ansible/latest/modules/vmware_host_config_info_module.html#vmware-host-config-info-module)
- [vmware_host_config_manager – Manage advanced system settings of an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_config_manager_module.html#vmware-host-config-manager-module)
- [vmware_host_datastore – Manage a datastore on ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_datastore_module.html#vmware-host-datastore-module)
- [vmware_host_dns_facts – Gathers facts about an ESXi host’s DNS configuration information](https://docs.ansible.com/ansible/latest/modules/vmware_host_dns_facts_module.html#vmware-host-dns-facts-module) **(D)**
- [vmware_host_dns_info – Gathers info about an ESXi host’s DNS configuration information](https://docs.ansible.com/ansible/latest/modules/vmware_host_dns_info_module.html#vmware-host-dns-info-module)
- [vmware_host_facts – Gathers facts about remote ESXi hostsystem](https://docs.ansible.com/ansible/latest/modules/vmware_host_facts_module.html#vmware-host-facts-module)
- [vmware_host_feature_facts – Gathers facts about an ESXi host’s feature capability information](https://docs.ansible.com/ansible/latest/modules/vmware_host_feature_facts_module.html#vmware-host-feature-facts-module) **(D)**
- [vmware_host_feature_info – Gathers info about an ESXi host’s feature capability information](https://docs.ansible.com/ansible/latest/modules/vmware_host_feature_info_module.html#vmware-host-feature-info-module)
- [vmware_host_firewall_facts – Gathers facts about an ESXi host’s firewall configuration information](https://docs.ansible.com/ansible/latest/modules/vmware_host_firewall_facts_module.html#vmware-host-firewall-facts-module) **(D)**
- [vmware_host_firewall_info – Gathers info about an ESXi host’s firewall configuration information](https://docs.ansible.com/ansible/latest/modules/vmware_host_firewall_info_module.html#vmware-host-firewall-info-module)
- [vmware_host_firewall_manager – Manage firewall configurations about an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_firewall_manager_module.html#vmware-host-firewall-manager-module)
- [vmware_host_hyperthreading – Enables/Disables Hyperthreading optimization for an ESXi host system](https://docs.ansible.com/ansible/latest/modules/vmware_host_hyperthreading_module.html#vmware-host-hyperthreading-module)
- [vmware_host_ipv6 – Enables/Disables IPv6 support for an ESXi host system](https://docs.ansible.com/ansible/latest/modules/vmware_host_ipv6_module.html#vmware-host-ipv6-module)
- [vmware_host_kernel_manager – Manage kernel module options on ESXi hosts](https://docs.ansible.com/ansible/latest/modules/vmware_host_kernel_manager_module.html#vmware-host-kernel-manager-module)
- [vmware_host_lockdown – Manage administrator permission for the local administrative account for the ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_lockdown_module.html#vmware-host-lockdown-module)
- [vmware_host_ntp – Manage NTP server configuration of an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_ntp_module.html#vmware-host-ntp-module)
- [vmware_host_ntp_facts – Gathers facts about NTP configuration on an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_ntp_facts_module.html#vmware-host-ntp-facts-module) **(D)**
- [vmware_host_ntp_info – Gathers info about NTP configuration on an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_ntp_info_module.html#vmware-host-ntp-info-module)
- [vmware_host_package_facts – Gathers facts about available packages on an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_package_facts_module.html#vmware-host-package-facts-module) **(D)**
- [vmware_host_package_info – Gathers info about available packages on an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_package_info_module.html#vmware-host-package-info-module)
- [vmware_host_powermgmt_policy – Manages the Power Management Policy of an ESXI host system](https://docs.ansible.com/ansible/latest/modules/vmware_host_powermgmt_policy_module.html#vmware-host-powermgmt-policy-module)
- [vmware_host_powerstate – Manages power states of host systems in vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_host_powerstate_module.html#vmware-host-powerstate-module)
- [vmware_host_scanhba – Rescan host HBA’s and optionally refresh the storage system](https://docs.ansible.com/ansible/latest/modules/vmware_host_scanhba_module.html#vmware-host-scanhba-module)
- [vmware_host_service_facts – Gathers facts about an ESXi host’s services](https://docs.ansible.com/ansible/latest/modules/vmware_host_service_facts_module.html#vmware-host-service-facts-module) **(D)**
- [vmware_host_service_info – Gathers info about an ESXi host’s services](https://docs.ansible.com/ansible/latest/modules/vmware_host_service_info_module.html#vmware-host-service-info-module)
- [vmware_host_service_manager – Manage services on a given ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_service_manager_module.html#vmware-host-service-manager-module)
- [vmware_host_snmp – Configures SNMP on an ESXi host system](https://docs.ansible.com/ansible/latest/modules/vmware_host_snmp_module.html#vmware-host-snmp-module)
- [vmware_host_ssl_facts – Gather facts of ESXi host system about SSL](https://docs.ansible.com/ansible/latest/modules/vmware_host_ssl_facts_module.html#vmware-host-ssl-facts-module) **(D)**
- [vmware_host_ssl_info – Gather info of ESXi host system about SSL](https://docs.ansible.com/ansible/latest/modules/vmware_host_ssl_info_module.html#vmware-host-ssl-info-module)
- [vmware_host_vmhba_facts – Gathers facts about vmhbas available on the given ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_vmhba_facts_module.html#vmware-host-vmhba-facts-module) **(D)**
- [vmware_host_vmhba_info – Gathers info about vmhbas available on the given ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_vmhba_info_module.html#vmware-host-vmhba-info-module)
- [vmware_host_vmnic_facts – Gathers facts about vmnics available on the given ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_vmnic_facts_module.html#vmware-host-vmnic-facts-module) **(D)**
- [vmware_host_vmnic_info – Gathers info about vmnics available on the given ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_host_vmnic_info_module.html#vmware-host-vmnic-info-module)
- [vmware_local_role_facts – Gather facts about local roles on an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_local_role_facts_module.html#vmware-local-role-facts-module) **(D)**
- [vmware_local_role_info – Gather info about local roles on an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_local_role_info_module.html#vmware-local-role-info-module)
- [vmware_local_role_manager – Manage local roles on an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_local_role_manager_module.html#vmware-local-role-manager-module)
- [vmware_local_user_facts – Gather facts about users on the given ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_local_user_facts_module.html#vmware-local-user-facts-module) **(D)**
- [vmware_local_user_info – Gather info about users on the given ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_local_user_info_module.html#vmware-local-user-info-module)
- [vmware_local_user_manager – Manage local users on an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_local_user_manager_module.html#vmware-local-user-manager-module)
- [vmware_maintenancemode – Place a host into maintenance mode](https://docs.ansible.com/ansible/latest/modules/vmware_maintenancemode_module.html#vmware-maintenancemode-module)
- [vmware_migrate_vmk – Migrate a VMK interface from VSS to VDS](https://docs.ansible.com/ansible/latest/modules/vmware_migrate_vmk_module.html#vmware-migrate-vmk-module)
- [vmware_object_role_permission – Manage local roles on an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_object_role_permission_module.html#vmware-object-role-permission-module)
- [vmware_portgroup – Create a VMware portgroup](https://docs.ansible.com/ansible/latest/modules/vmware_portgroup_module.html#vmware-portgroup-module)
- [vmware_portgroup_facts – Gathers facts about an ESXi host’s Port Group configuration](https://docs.ansible.com/ansible/latest/modules/vmware_portgroup_facts_module.html#vmware-portgroup-facts-module) **(D)**
- [vmware_portgroup_info – Gathers info about an ESXi host’s Port Group configuration](https://docs.ansible.com/ansible/latest/modules/vmware_portgroup_info_module.html#vmware-portgroup-info-module)
- [vmware_resource_pool – Add/remove resource pools to/from vCenter](https://docs.ansible.com/ansible/latest/modules/vmware_resource_pool_module.html#vmware-resource-pool-module)
- [vmware_resource_pool_facts – Gathers facts about resource pool information](https://docs.ansible.com/ansible/latest/modules/vmware_resource_pool_facts_module.html#vmware-resource-pool-facts-module) **(D)**
- [vmware_resource_pool_info – Gathers info about resource pool information](https://docs.ansible.com/ansible/latest/modules/vmware_resource_pool_info_module.html#vmware-resource-pool-info-module)
- [vmware_tag – Manage VMware tags](https://docs.ansible.com/ansible/latest/modules/vmware_tag_module.html#vmware-tag-module)
- [vmware_tag_info – Manage VMware tag info](https://docs.ansible.com/ansible/latest/modules/vmware_tag_info_module.html#vmware-tag-info-module)
- [vmware_tag_manager – Manage association of VMware tags with VMware objects](https://docs.ansible.com/ansible/latest/modules/vmware_tag_manager_module.html#vmware-tag-manager-module)
- [vmware_target_canonical_facts – Return canonical (NAA) from an ESXi host system](https://docs.ansible.com/ansible/latest/modules/vmware_target_canonical_facts_module.html#vmware-target-canonical-facts-module) **(D)**
- [vmware_target_canonical_info – Return canonical (NAA) from an ESXi host system](https://docs.ansible.com/ansible/latest/modules/vmware_target_canonical_info_module.html#vmware-target-canonical-info-module)
- [vmware_vcenter_settings – Configures general settings on a vCenter server](https://docs.ansible.com/ansible/latest/modules/vmware_vcenter_settings_module.html#vmware-vcenter-settings-module)
- [vmware_vcenter_statistics – Configures statistics on a vCenter server](https://docs.ansible.com/ansible/latest/modules/vmware_vcenter_statistics_module.html#vmware-vcenter-statistics-module)
- [vmware_vm_host_drs_rule – Creates vm/host group in a given cluster](https://docs.ansible.com/ansible/latest/modules/vmware_vm_host_drs_rule_module.html#vmware-vm-host-drs-rule-module)
- [vmware_vm_info – Return basic info pertaining to a VMware machine guest](https://docs.ansible.com/ansible/latest/modules/vmware_vm_info_module.html#vmware-vm-info-module)
- [vmware_vm_shell – Run commands in a VMware guest operating system](https://docs.ansible.com/ansible/latest/modules/vmware_vm_shell_module.html#vmware-vm-shell-module)
- [vmware_vm_storage_policy_info – Gather information about vSphere storage profile defined storage policy information](https://docs.ansible.com/ansible/latest/modules/vmware_vm_storage_policy_info_module.html#vmware-vm-storage-policy-info-module)
- [vmware_vm_vm_drs_rule – Configure VMware DRS Affinity rule for virtual machine in given cluster](https://docs.ansible.com/ansible/latest/modules/vmware_vm_vm_drs_rule_module.html#vmware-vm-vm-drs-rule-module)
- [vmware_vm_vss_dvs_migrate – Migrates a virtual machine from a standard vswitch to distributed](https://docs.ansible.com/ansible/latest/modules/vmware_vm_vss_dvs_migrate_module.html#vmware-vm-vss-dvs-migrate-module)
- [vmware_vmkernel – Manages a VMware VMkernel Adapter of an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_vmkernel_module.html#vmware-vmkernel-module)
- [vmware_vmkernel_facts – Gathers VMKernel facts about an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_vmkernel_facts_module.html#vmware-vmkernel-facts-module) **(D)**
- [vmware_vmkernel_info – Gathers VMKernel info about an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_vmkernel_info_module.html#vmware-vmkernel-info-module)
- [vmware_vmkernel_ip_config – Configure the VMkernel IP Address](https://docs.ansible.com/ansible/latest/modules/vmware_vmkernel_ip_config_module.html#vmware-vmkernel-ip-config-module)
- [vmware_vmotion – Move a virtual machine using vMotion, and/or its vmdks using storage vMotion](https://docs.ansible.com/ansible/latest/modules/vmware_vmotion_module.html#vmware-vmotion-module)
- [vmware_vsan_cluster – Configure VSAN clustering on an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_vsan_cluster_module.html#vmware-vsan-cluster-module)
- [vmware_vspan_session – Create or remove a Port Mirroring session](https://docs.ansible.com/ansible/latest/modules/vmware_vspan_session_module.html#vmware-vspan-session-module)
- [vmware_vswitch – Manage a VMware Standard Switch to an ESXi host](https://docs.ansible.com/ansible/latest/modules/vmware_vswitch_module.html#vmware-vswitch-module)
- [vmware_vswitch_facts – Gathers facts about an ESXi host’s vswitch configurations](https://docs.ansible.com/ansible/latest/modules/vmware_vswitch_facts_module.html#vmware-vswitch-facts-module) **(D)**
- [vmware_vswitch_info – Gathers info about an ESXi host’s vswitch configurations](https://docs.ansible.com/ansible/latest/modules/vmware_vswitch_info_module.html#vmware-vswitch-info-module)
- [vsphere_copy – Copy a file to a VMware datastore](https://docs.ansible.com/ansible/latest/modules/vsphere_copy_module.html#vsphere-copy-module)
- [vsphere_file – Manage files on a vCenter datastore](https://docs.ansible.com/ansible/latest/modules/vsphere_file_module.html#vsphere-file-module)



### Vultr

- [vultr_account_facts – Gather facts about the Vultr account](https://docs.ansible.com/ansible/latest/modules/vultr_account_facts_module.html#vultr-account-facts-module) **(D)**
- [vultr_account_info – Get information about the Vultr account](https://docs.ansible.com/ansible/latest/modules/vultr_account_info_module.html#vultr-account-info-module)
- [vultr_block_storage – Manages block storage volumes on Vultr](https://docs.ansible.com/ansible/latest/modules/vultr_block_storage_module.html#vultr-block-storage-module)
- [vultr_block_storage_facts – Gather facts about the Vultr block storage volumes available](https://docs.ansible.com/ansible/latest/modules/vultr_block_storage_facts_module.html#vultr-block-storage-facts-module) **(D)**
- [vultr_block_storage_info – Get information about the Vultr block storage volumes available](https://docs.ansible.com/ansible/latest/modules/vultr_block_storage_info_module.html#vultr-block-storage-info-module)
- [vultr_dns_domain – Manages DNS domains on Vultr](https://docs.ansible.com/ansible/latest/modules/vultr_dns_domain_module.html#vultr-dns-domain-module)
- [vultr_dns_domain_facts – Gather facts about the Vultr DNS domains available](https://docs.ansible.com/ansible/latest/modules/vultr_dns_domain_facts_module.html#vultr-dns-domain-facts-module) **(D)**
- [vultr_dns_domain_info – Gather information about the Vultr DNS domains available](https://docs.ansible.com/ansible/latest/modules/vultr_dns_domain_info_module.html#vultr-dns-domain-info-module)
- [vultr_dns_record – Manages DNS records on Vultr](https://docs.ansible.com/ansible/latest/modules/vultr_dns_record_module.html#vultr-dns-record-module)
- [vultr_firewall_group – Manages firewall groups on Vultr](https://docs.ansible.com/ansible/latest/modules/vultr_firewall_group_module.html#vultr-firewall-group-module)
- [vultr_firewall_group_facts – Gather facts about the Vultr firewall groups available](https://docs.ansible.com/ansible/latest/modules/vultr_firewall_group_facts_module.html#vultr-firewall-group-facts-module) **(D)**
- [vultr_firewall_group_info – Gather information about the Vultr firewall groups available](https://docs.ansible.com/ansible/latest/modules/vultr_firewall_group_info_module.html#vultr-firewall-group-info-module)
- [vultr_firewall_rule – Manages firewall rules on Vultr](https://docs.ansible.com/ansible/latest/modules/vultr_firewall_rule_module.html#vultr-firewall-rule-module)
- [vultr_network – Manages networks on Vultr](https://docs.ansible.com/ansible/latest/modules/vultr_network_module.html#vultr-network-module)
- [vultr_network_facts – Gather facts about the Vultr networks available](https://docs.ansible.com/ansible/latest/modules/vultr_network_facts_module.html#vultr-network-facts-module) **(D)**
- [vultr_network_info – Gather information about the Vultr networks available](https://docs.ansible.com/ansible/latest/modules/vultr_network_info_module.html#vultr-network-info-module)
- [vultr_os_facts – Gather facts about the Vultr OSes available](https://docs.ansible.com/ansible/latest/modules/vultr_os_facts_module.html#vultr-os-facts-module) **(D)**
- [vultr_os_info – Get information about the Vultr OSes available](https://docs.ansible.com/ansible/latest/modules/vultr_os_info_module.html#vultr-os-info-module)
- [vultr_plan_facts – Gather facts about the Vultr plans available](https://docs.ansible.com/ansible/latest/modules/vultr_plan_facts_module.html#vultr-plan-facts-module) **(D)**
- [vultr_plan_info – Gather information about the Vultr plans available](https://docs.ansible.com/ansible/latest/modules/vultr_plan_info_module.html#vultr-plan-info-module)
- [vultr_region_facts – Gather facts about the Vultr regions available](https://docs.ansible.com/ansible/latest/modules/vultr_region_facts_module.html#vultr-region-facts-module) **(D)**
- [vultr_region_info – Gather information about the Vultr regions available](https://docs.ansible.com/ansible/latest/modules/vultr_region_info_module.html#vultr-region-info-module)
- [vultr_server – Manages virtual servers on Vultr](https://docs.ansible.com/ansible/latest/modules/vultr_server_module.html#vultr-server-module)
- [vultr_server_facts – Gather facts about the Vultr servers available](https://docs.ansible.com/ansible/latest/modules/vultr_server_facts_module.html#vultr-server-facts-module) **(D)**
- [vultr_server_info – Gather information about the Vultr servers available](https://docs.ansible.com/ansible/latest/modules/vultr_server_info_module.html#vultr-server-info-module)
- [vultr_ssh_key – Manages ssh keys on Vultr](https://docs.ansible.com/ansible/latest/modules/vultr_ssh_key_module.html#vultr-ssh-key-module)
- [vultr_ssh_key_facts – Gather facts about the Vultr SSH keys available](https://docs.ansible.com/ansible/latest/modules/vultr_ssh_key_facts_module.html#vultr-ssh-key-facts-module) **(D)**
- [vultr_ssh_key_info – Get information about the Vultr SSH keys available](https://docs.ansible.com/ansible/latest/modules/vultr_ssh_key_info_module.html#vultr-ssh-key-info-module)
- [vultr_startup_script – Manages startup scripts on Vultr](https://docs.ansible.com/ansible/latest/modules/vultr_startup_script_module.html#vultr-startup-script-module)
- [vultr_startup_script_facts – Gather facts about the Vultr startup scripts available](https://docs.ansible.com/ansible/latest/modules/vultr_startup_script_facts_module.html#vultr-startup-script-facts-module) **(D)**
- [vultr_startup_script_info – Gather information about the Vultr startup scripts available](https://docs.ansible.com/ansible/latest/modules/vultr_startup_script_info_module.html#vultr-startup-script-info-module)
- [vultr_user – Manages users on Vultr](https://docs.ansible.com/ansible/latest/modules/vultr_user_module.html#vultr-user-module)
- [vultr_user_facts – Gather facts about the Vultr user available](https://docs.ansible.com/ansible/latest/modules/vultr_user_facts_module.html#vultr-user-facts-module) **(D)**
- [vultr_user_info – Get information about the Vultr user available](https://docs.ansible.com/ansible/latest/modules/vultr_user_info_module.html#vultr-user-info-module)



### Webfaction

- [webfaction_app – Add or remove applications on a Webfaction host](https://docs.ansible.com/ansible/latest/modules/webfaction_app_module.html#webfaction-app-module)
- [webfaction_db – Add or remove a database on Webfaction](https://docs.ansible.com/ansible/latest/modules/webfaction_db_module.html#webfaction-db-module)
- [webfaction_domain – Add or remove domains and subdomains on Webfaction](https://docs.ansible.com/ansible/latest/modules/webfaction_domain_module.html#webfaction-domain-module)
- [webfaction_mailbox – Add or remove mailboxes on Webfaction](https://docs.ansible.com/ansible/latest/modules/webfaction_mailbox_module.html#webfaction-mailbox-module)
- [webfaction_site – Add or remove a website on a Webfaction host](https://docs.ansible.com/ansible/latest/modules/webfaction_site_module.html#webfaction-site-module)



### Xenserver

- [xenserver_guest – Manages virtual machines running on Citrix Hypervisor/XenServer host or pool](https://docs.ansible.com/ansible/latest/modules/xenserver_guest_module.html#xenserver-guest-module)
- [xenserver_guest_info – Gathers information for virtual machines running on Citrix Hypervisor/XenServer host or pool](https://docs.ansible.com/ansible/latest/modules/xenserver_guest_info_module.html#xenserver-guest-info-module)
- [xenserver_guest_powerstate – Manages power states of virtual machines running on Citrix Hypervisor/XenServer host or pool](https://docs.ansible.com/ansible/latest/modules/xenserver_guest_powerstate_module.html#xenserver-guest-powerstate-module)



## Clustering modules

- [consul – Add, modify & delete services within a consul cluster](https://docs.ansible.com/ansible/latest/modules/consul_module.html#consul-module)
- [consul_acl – Manipulate Consul ACL keys and rules](https://docs.ansible.com/ansible/latest/modules/consul_acl_module.html#consul-acl-module)
- [consul_kv – Manipulate entries in the key/value store of a consul cluster](https://docs.ansible.com/ansible/latest/modules/consul_kv_module.html#consul-kv-module)
- [consul_session – Manipulate consul sessions](https://docs.ansible.com/ansible/latest/modules/consul_session_module.html#consul-session-module)
- [etcd3 – Set or delete key value pairs from an etcd3 cluster](https://docs.ansible.com/ansible/latest/modules/etcd3_module.html#etcd3-module)
- [pacemaker_cluster – Manage pacemaker clusters](https://docs.ansible.com/ansible/latest/modules/pacemaker_cluster_module.html#pacemaker-cluster-module)
- [znode – Create, delete, retrieve, and update znodes using ZooKeeper](https://docs.ansible.com/ansible/latest/modules/znode_module.html#znode-module)



### K8S

- [k8s – Manage Kubernetes (K8s) objects](https://docs.ansible.com/ansible/latest/modules/k8s_module.html#k8s-module)
- [k8s_auth – Authenticate to Kubernetes clusters which require an explicit login step](https://docs.ansible.com/ansible/latest/modules/k8s_auth_module.html#k8s-auth-module)
- [k8s_info – Describe Kubernetes (K8s) objects](https://docs.ansible.com/ansible/latest/modules/k8s_info_module.html#k8s-info-module)
- [k8s_scale – Set a new size for a Deployment, ReplicaSet, Replication Controller, or Job](https://docs.ansible.com/ansible/latest/modules/k8s_scale_module.html#k8s-scale-module)
- [k8s_service – Manage Services on Kubernetes](https://docs.ansible.com/ansible/latest/modules/k8s_service_module.html#k8s-service-module)

## Commands modules

- [command – Execute commands on targets](https://docs.ansible.com/ansible/latest/modules/command_module.html#command-module)
- [expect – Executes a command and responds to prompts](https://docs.ansible.com/ansible/latest/modules/expect_module.html#expect-module)
- [psexec – Runs commands on a remote Windows host based on the PsExec model](https://docs.ansible.com/ansible/latest/modules/psexec_module.html#psexec-module)
- [raw – Executes a low-down and dirty command](https://docs.ansible.com/ansible/latest/modules/raw_module.html#raw-module)
- [script – Runs a local script on a remote node after transferring it](https://docs.ansible.com/ansible/latest/modules/script_module.html#script-module)
- [shell – Execute shell commands on targets](https://docs.ansible.com/ansible/latest/modules/shell_module.html#shell-module)
- [telnet – Executes a low-down and dirty telnet command](https://docs.ansible.com/ansible/latest/modules/telnet_module.html#telnet-module)

## Crypto modules

- [certificate_complete_chain – Complete certificate chain given a set of untrusted and root certificates](https://docs.ansible.com/ansible/latest/modules/certificate_complete_chain_module.html#certificate-complete-chain-module)
- [get_certificate – Get a certificate from a host:port](https://docs.ansible.com/ansible/latest/modules/get_certificate_module.html#get-certificate-module)
- [luks_device – Manage encrypted (LUKS) devices](https://docs.ansible.com/ansible/latest/modules/luks_device_module.html#luks-device-module)
- [openssh_cert – Generate OpenSSH host or user certificates](https://docs.ansible.com/ansible/latest/modules/openssh_cert_module.html#openssh-cert-module)
- [openssh_keypair – Generate OpenSSH private and public keys](https://docs.ansible.com/ansible/latest/modules/openssh_keypair_module.html#openssh-keypair-module)
- [openssl_certificate – Generate and/or check OpenSSL certificates](https://docs.ansible.com/ansible/latest/modules/openssl_certificate_module.html#openssl-certificate-module)
- [openssl_certificate_info – Provide information of OpenSSL X.509 certificates](https://docs.ansible.com/ansible/latest/modules/openssl_certificate_info_module.html#openssl-certificate-info-module)
- [openssl_csr – Generate OpenSSL Certificate Signing Request (CSR)](https://docs.ansible.com/ansible/latest/modules/openssl_csr_module.html#openssl-csr-module)
- [openssl_csr_info – Provide information of OpenSSL Certificate Signing Requests (CSR)](https://docs.ansible.com/ansible/latest/modules/openssl_csr_info_module.html#openssl-csr-info-module)
- [openssl_dhparam – Generate OpenSSL Diffie-Hellman Parameters](https://docs.ansible.com/ansible/latest/modules/openssl_dhparam_module.html#openssl-dhparam-module)
- [openssl_pkcs12 – Generate OpenSSL PKCS#12 archive](https://docs.ansible.com/ansible/latest/modules/openssl_pkcs12_module.html#openssl-pkcs12-module)
- [openssl_privatekey – Generate OpenSSL private keys](https://docs.ansible.com/ansible/latest/modules/openssl_privatekey_module.html#openssl-privatekey-module)
- [openssl_privatekey_info – Provide information for OpenSSL private keys](https://docs.ansible.com/ansible/latest/modules/openssl_privatekey_info_module.html#openssl-privatekey-info-module)
- [openssl_publickey – Generate an OpenSSL public key from its private key](https://docs.ansible.com/ansible/latest/modules/openssl_publickey_module.html#openssl-publickey-module)



### Acme

- [acme_account – Create, modify or delete ACME accounts](https://docs.ansible.com/ansible/latest/modules/acme_account_module.html#acme-account-module)
- [acme_account_info – Retrieves information on ACME accounts](https://docs.ansible.com/ansible/latest/modules/acme_account_info_module.html#acme-account-info-module)
- [acme_certificate – Create SSL/TLS certificates with the ACME protocol](https://docs.ansible.com/ansible/latest/modules/acme_certificate_module.html#acme-certificate-module)
- [acme_certificate_revoke – Revoke certificates with the ACME protocol](https://docs.ansible.com/ansible/latest/modules/acme_certificate_revoke_module.html#acme-certificate-revoke-module)
- [acme_challenge_cert_helper – Prepare certificates required for ACME challenges such as tls-alpn-01](https://docs.ansible.com/ansible/latest/modules/acme_challenge_cert_helper_module.html#acme-challenge-cert-helper-module)
- [acme_inspect – Send direct requests to an ACME server](https://docs.ansible.com/ansible/latest/modules/acme_inspect_module.html#acme-inspect-module)



### Entrust

- [ecs_certificate – Request SSL/TLS certificates with the Entrust Certificate Services (ECS) API](https://docs.ansible.com/ansible/latest/modules/ecs_certificate_module.html#ecs-certificate-module)

## Database modules

### Aerospike

- [aerospike_migrations – Check or wait for migrations between nodes](https://docs.ansible.com/ansible/latest/modules/aerospike_migrations_module.html#aerospike-migrations-module)



### Influxdb

- [influxdb_database – Manage InfluxDB databases](https://docs.ansible.com/ansible/latest/modules/influxdb_database_module.html#influxdb-database-module)
- [influxdb_query – Query data points from InfluxDB](https://docs.ansible.com/ansible/latest/modules/influxdb_query_module.html#influxdb-query-module)
- [influxdb_retention_policy – Manage InfluxDB retention policies](https://docs.ansible.com/ansible/latest/modules/influxdb_retention_policy_module.html#influxdb-retention-policy-module)
- [influxdb_user – Manage InfluxDB users](https://docs.ansible.com/ansible/latest/modules/influxdb_user_module.html#influxdb-user-module)
- [influxdb_write – Write data points into InfluxDB](https://docs.ansible.com/ansible/latest/modules/influxdb_write_module.html#influxdb-write-module)



### Misc

- [elasticsearch_plugin – Manage Elasticsearch plugins](https://docs.ansible.com/ansible/latest/modules/elasticsearch_plugin_module.html#elasticsearch-plugin-module)
- [kibana_plugin – Manage Kibana plugins](https://docs.ansible.com/ansible/latest/modules/kibana_plugin_module.html#kibana-plugin-module)
- [redis – Various redis commands, slave and flush](https://docs.ansible.com/ansible/latest/modules/redis_module.html#redis-module)
- [riak – This module handles some common Riak operations](https://docs.ansible.com/ansible/latest/modules/riak_module.html#riak-module)



### Mongodb

- [mongodb_parameter – Change an administrative parameter on a MongoDB server](https://docs.ansible.com/ansible/latest/modules/mongodb_parameter_module.html#mongodb-parameter-module)
- [mongodb_replicaset – Initialises a MongoDB replicaset](https://docs.ansible.com/ansible/latest/modules/mongodb_replicaset_module.html#mongodb-replicaset-module)
- [mongodb_shard – Add and remove shards from a MongoDB Cluster](https://docs.ansible.com/ansible/latest/modules/mongodb_shard_module.html#mongodb-shard-module)
- [mongodb_user – Adds or removes a user from a MongoDB database](https://docs.ansible.com/ansible/latest/modules/mongodb_user_module.html#mongodb-user-module)



### Mssql

- [mssql_db – Add or remove MSSQL databases from a remote host](https://docs.ansible.com/ansible/latest/modules/mssql_db_module.html#mssql-db-module)



### Mysql

- [mysql_db – Add or remove MySQL databases from a remote host](https://docs.ansible.com/ansible/latest/modules/mysql_db_module.html#mysql-db-module)
- [mysql_info – Gather information about MySQL servers](https://docs.ansible.com/ansible/latest/modules/mysql_info_module.html#mysql-info-module)
- [mysql_replication – Manage MySQL replication](https://docs.ansible.com/ansible/latest/modules/mysql_replication_module.html#mysql-replication-module)
- [mysql_user – Adds or removes a user from a MySQL database](https://docs.ansible.com/ansible/latest/modules/mysql_user_module.html#mysql-user-module)
- [mysql_variables – Manage MySQL global variables](https://docs.ansible.com/ansible/latest/modules/mysql_variables_module.html#mysql-variables-module)



### Postgresql

- [postgresql_copy – Copy data between a file/program and a PostgreSQL table](https://docs.ansible.com/ansible/latest/modules/postgresql_copy_module.html#postgresql-copy-module)
- [postgresql_db – Add or remove PostgreSQL databases from a remote host](https://docs.ansible.com/ansible/latest/modules/postgresql_db_module.html#postgresql-db-module)
- [postgresql_ext – Add or remove PostgreSQL extensions from a database](https://docs.ansible.com/ansible/latest/modules/postgresql_ext_module.html#postgresql-ext-module)
- [postgresql_idx – Create or drop indexes from a PostgreSQL database](https://docs.ansible.com/ansible/latest/modules/postgresql_idx_module.html#postgresql-idx-module)
- [postgresql_info – Gather information about PostgreSQL servers](https://docs.ansible.com/ansible/latest/modules/postgresql_info_module.html#postgresql-info-module)
- [postgresql_lang – Adds, removes or changes procedural languages with a PostgreSQL database](https://docs.ansible.com/ansible/latest/modules/postgresql_lang_module.html#postgresql-lang-module)
- [postgresql_membership – Add or remove PostgreSQL roles from groups](https://docs.ansible.com/ansible/latest/modules/postgresql_membership_module.html#postgresql-membership-module)
- [postgresql_owner – Change an owner of PostgreSQL database object](https://docs.ansible.com/ansible/latest/modules/postgresql_owner_module.html#postgresql-owner-module)
- [postgresql_pg_hba – Add, remove or modify a rule in a pg_hba file](https://docs.ansible.com/ansible/latest/modules/postgresql_pg_hba_module.html#postgresql-pg-hba-module)
- [postgresql_ping – Check remote PostgreSQL server availability](https://docs.ansible.com/ansible/latest/modules/postgresql_ping_module.html#postgresql-ping-module)
- [postgresql_privs – Grant or revoke privileges on PostgreSQL database objects](https://docs.ansible.com/ansible/latest/modules/postgresql_privs_module.html#postgresql-privs-module)
- [postgresql_publication – Add, update, or remove PostgreSQL publication](https://docs.ansible.com/ansible/latest/modules/postgresql_publication_module.html#postgresql-publication-module)
- [postgresql_query – Run PostgreSQL queries](https://docs.ansible.com/ansible/latest/modules/postgresql_query_module.html#postgresql-query-module)
- [postgresql_schema – Add or remove PostgreSQL schema](https://docs.ansible.com/ansible/latest/modules/postgresql_schema_module.html#postgresql-schema-module)
- [postgresql_sequence – Create, drop, or alter a PostgreSQL sequence](https://docs.ansible.com/ansible/latest/modules/postgresql_sequence_module.html#postgresql-sequence-module)
- [postgresql_set – Change a PostgreSQL server configuration parameter](https://docs.ansible.com/ansible/latest/modules/postgresql_set_module.html#postgresql-set-module)
- [postgresql_slot – Add or remove replication slots from a PostgreSQL database](https://docs.ansible.com/ansible/latest/modules/postgresql_slot_module.html#postgresql-slot-module)
- [postgresql_table – Create, drop, or modify a PostgreSQL table](https://docs.ansible.com/ansible/latest/modules/postgresql_table_module.html#postgresql-table-module)
- [postgresql_tablespace – Add or remove PostgreSQL tablespaces from remote hosts](https://docs.ansible.com/ansible/latest/modules/postgresql_tablespace_module.html#postgresql-tablespace-module)
- [postgresql_user – Add or remove a user (role) from a PostgreSQL server instance](https://docs.ansible.com/ansible/latest/modules/postgresql_user_module.html#postgresql-user-module)



### Proxysql

- [proxysql_backend_servers – Adds or removes mysql hosts from proxysql admin interface](https://docs.ansible.com/ansible/latest/modules/proxysql_backend_servers_module.html#proxysql-backend-servers-module)
- [proxysql_global_variables – Gets or sets the proxysql global variables](https://docs.ansible.com/ansible/latest/modules/proxysql_global_variables_module.html#proxysql-global-variables-module)
- [proxysql_manage_config – Writes the proxysql configuration settings between layers](https://docs.ansible.com/ansible/latest/modules/proxysql_manage_config_module.html#proxysql-manage-config-module)
- [proxysql_mysql_users – Adds or removes mysql users from proxysql admin interface](https://docs.ansible.com/ansible/latest/modules/proxysql_mysql_users_module.html#proxysql-mysql-users-module)
- [proxysql_query_rules – Modifies query rules using the proxysql admin interface](https://docs.ansible.com/ansible/latest/modules/proxysql_query_rules_module.html#proxysql-query-rules-module)
- [proxysql_replication_hostgroups – Manages replication hostgroups using the proxysql admin interface](https://docs.ansible.com/ansible/latest/modules/proxysql_replication_hostgroups_module.html#proxysql-replication-hostgroups-module)
- [proxysql_scheduler – Adds or removes schedules from proxysql admin interface](https://docs.ansible.com/ansible/latest/modules/proxysql_scheduler_module.html#proxysql-scheduler-module)



### Vertica

- [vertica_configuration – Updates Vertica configuration parameters](https://docs.ansible.com/ansible/latest/modules/vertica_configuration_module.html#vertica-configuration-module)
- [vertica_info – Gathers Vertica database facts](https://docs.ansible.com/ansible/latest/modules/vertica_info_module.html#vertica-info-module)
- [vertica_role – Adds or removes Vertica database roles and assigns roles to them](https://docs.ansible.com/ansible/latest/modules/vertica_role_module.html#vertica-role-module)
- [vertica_schema – Adds or removes Vertica database schema and roles](https://docs.ansible.com/ansible/latest/modules/vertica_schema_module.html#vertica-schema-module)
- [vertica_user – Adds or removes Vertica database users and assigns roles](https://docs.ansible.com/ansible/latest/modules/vertica_user_module.html#vertica-user-module)

## Files modules

- [acl – Set and retrieve file ACL information](https://docs.ansible.com/ansible/latest/modules/acl_module.html#acl-module)
- [archive – Creates a compressed archive of one or more files or trees](https://docs.ansible.com/ansible/latest/modules/archive_module.html#archive-module)
- [assemble – Assemble configuration files from fragments](https://docs.ansible.com/ansible/latest/modules/assemble_module.html#assemble-module)
- [blockinfile – Insert/update/remove a text block surrounded by marker lines](https://docs.ansible.com/ansible/latest/modules/blockinfile_module.html#blockinfile-module)
- [copy – Copy files to remote locations](https://docs.ansible.com/ansible/latest/modules/copy_module.html#copy-module)
- [fetch – Fetch files from remote nodes](https://docs.ansible.com/ansible/latest/modules/fetch_module.html#fetch-module)
- [file – Manage files and file properties](https://docs.ansible.com/ansible/latest/modules/file_module.html#file-module)
- [find – Return a list of files based on specific criteria](https://docs.ansible.com/ansible/latest/modules/find_module.html#find-module)
- [ini_file – Tweak settings in INI files](https://docs.ansible.com/ansible/latest/modules/ini_file_module.html#ini-file-module)
- [iso_extract – Extract files from an ISO image](https://docs.ansible.com/ansible/latest/modules/iso_extract_module.html#iso-extract-module)
- [lineinfile – Manage lines in text files](https://docs.ansible.com/ansible/latest/modules/lineinfile_module.html#lineinfile-module)
- [patch – Apply patch files using the GNU patch tool](https://docs.ansible.com/ansible/latest/modules/patch_module.html#patch-module)
- [read_csv – Read a CSV file](https://docs.ansible.com/ansible/latest/modules/read_csv_module.html#read-csv-module)
- [replace – Replace all instances of a particular string in a file using a back-referenced regular expression](https://docs.ansible.com/ansible/latest/modules/replace_module.html#replace-module)
- [stat – Retrieve file or file system status](https://docs.ansible.com/ansible/latest/modules/stat_module.html#stat-module)
- [synchronize – A wrapper around rsync to make common tasks in your playbooks quick and easy](https://docs.ansible.com/ansible/latest/modules/synchronize_module.html#synchronize-module)
- [tempfile – Creates temporary files and directories](https://docs.ansible.com/ansible/latest/modules/tempfile_module.html#tempfile-module)
- [template – Template a file out to a remote server](https://docs.ansible.com/ansible/latest/modules/template_module.html#template-module)
- [unarchive – Unpacks an archive after (optionally) copying it from the local machine](https://docs.ansible.com/ansible/latest/modules/unarchive_module.html#unarchive-module)
- [xattr – Manage user defined extended attributes](https://docs.ansible.com/ansible/latest/modules/xattr_module.html#xattr-module)
- [xml – Manage bits and pieces of XML files or strings](https://docs.ansible.com/ansible/latest/modules/xml_module.html#xml-module)

## Identity modules

- [onepassword_info – Gather items from 1Password](https://docs.ansible.com/ansible/latest/modules/onepassword_info_module.html#onepassword-info-module)



### Cyberark

- [cyberark_authentication – Module for CyberArk Vault Authentication using PAS Web Services SDK](https://docs.ansible.com/ansible/latest/modules/cyberark_authentication_module.html#cyberark-authentication-module)
- [cyberark_user – Module for CyberArk User Management using PAS Web Services SDK](https://docs.ansible.com/ansible/latest/modules/cyberark_user_module.html#cyberark-user-module)



### Ipa

- [ipa_config – Manage Global FreeIPA Configuration Settings](https://docs.ansible.com/ansible/latest/modules/ipa_config_module.html#ipa-config-module)
- [ipa_dnsrecord – Manage FreeIPA DNS records](https://docs.ansible.com/ansible/latest/modules/ipa_dnsrecord_module.html#ipa-dnsrecord-module)
- [ipa_dnszone – Manage FreeIPA DNS Zones](https://docs.ansible.com/ansible/latest/modules/ipa_dnszone_module.html#ipa-dnszone-module)
- [ipa_group – Manage FreeIPA group](https://docs.ansible.com/ansible/latest/modules/ipa_group_module.html#ipa-group-module)
- [ipa_hbacrule – Manage FreeIPA HBAC rule](https://docs.ansible.com/ansible/latest/modules/ipa_hbacrule_module.html#ipa-hbacrule-module)
- [ipa_host – Manage FreeIPA host](https://docs.ansible.com/ansible/latest/modules/ipa_host_module.html#ipa-host-module)
- [ipa_hostgroup – Manage FreeIPA host-group](https://docs.ansible.com/ansible/latest/modules/ipa_hostgroup_module.html#ipa-hostgroup-module)
- [ipa_role – Manage FreeIPA role](https://docs.ansible.com/ansible/latest/modules/ipa_role_module.html#ipa-role-module)
- [ipa_service – Manage FreeIPA service](https://docs.ansible.com/ansible/latest/modules/ipa_service_module.html#ipa-service-module)
- [ipa_subca – Manage FreeIPA Lightweight Sub Certificate Authorities](https://docs.ansible.com/ansible/latest/modules/ipa_subca_module.html#ipa-subca-module)
- [ipa_sudocmd – Manage FreeIPA sudo command](https://docs.ansible.com/ansible/latest/modules/ipa_sudocmd_module.html#ipa-sudocmd-module)
- [ipa_sudocmdgroup – Manage FreeIPA sudo command group](https://docs.ansible.com/ansible/latest/modules/ipa_sudocmdgroup_module.html#ipa-sudocmdgroup-module)
- [ipa_sudorule – Manage FreeIPA sudo rule](https://docs.ansible.com/ansible/latest/modules/ipa_sudorule_module.html#ipa-sudorule-module)
- [ipa_user – Manage FreeIPA users](https://docs.ansible.com/ansible/latest/modules/ipa_user_module.html#ipa-user-module)
- [ipa_vault – Manage FreeIPA vaults](https://docs.ansible.com/ansible/latest/modules/ipa_vault_module.html#ipa-vault-module)



### Keycloak

- [keycloak_client – Allows administration of Keycloak clients via Keycloak API](https://docs.ansible.com/ansible/latest/modules/keycloak_client_module.html#keycloak-client-module)
- [keycloak_clienttemplate – Allows administration of Keycloak client templates via Keycloak API](https://docs.ansible.com/ansible/latest/modules/keycloak_clienttemplate_module.html#keycloak-clienttemplate-module)
- [keycloak_group – Allows administration of Keycloak groups via Keycloak API](https://docs.ansible.com/ansible/latest/modules/keycloak_group_module.html#keycloak-group-module)



### Opendj

- [opendj_backendprop – Will update the backend configuration of OpenDJ via the dsconfig set-backend-prop command](https://docs.ansible.com/ansible/latest/modules/opendj_backendprop_module.html#opendj-backendprop-module)

## Inventory modules

- [add_host – Add a host (and alternatively a group) to the ansible-playbook in-memory inventory](https://docs.ansible.com/ansible/latest/modules/add_host_module.html#add-host-module)
- [group_by – Create Ansible groups based on facts](https://docs.ansible.com/ansible/latest/modules/group_by_module.html#group-by-module)

## Messaging modules

### Rabbitmq

- [rabbitmq_binding – Manage rabbitMQ bindings](https://docs.ansible.com/ansible/latest/modules/rabbitmq_binding_module.html#rabbitmq-binding-module)
- [rabbitmq_exchange – Manage rabbitMQ exchanges](https://docs.ansible.com/ansible/latest/modules/rabbitmq_exchange_module.html#rabbitmq-exchange-module)
- [rabbitmq_global_parameter – Manage RabbitMQ global parameters](https://docs.ansible.com/ansible/latest/modules/rabbitmq_global_parameter_module.html#rabbitmq-global-parameter-module)
- [rabbitmq_parameter – Manage RabbitMQ parameters](https://docs.ansible.com/ansible/latest/modules/rabbitmq_parameter_module.html#rabbitmq-parameter-module)
- [rabbitmq_plugin – Manage RabbitMQ plugins](https://docs.ansible.com/ansible/latest/modules/rabbitmq_plugin_module.html#rabbitmq-plugin-module)
- [rabbitmq_policy – Manage the state of policies in RabbitMQ](https://docs.ansible.com/ansible/latest/modules/rabbitmq_policy_module.html#rabbitmq-policy-module)
- [rabbitmq_queue – Manage rabbitMQ queues](https://docs.ansible.com/ansible/latest/modules/rabbitmq_queue_module.html#rabbitmq-queue-module)
- [rabbitmq_user – Manage RabbitMQ users](https://docs.ansible.com/ansible/latest/modules/rabbitmq_user_module.html#rabbitmq-user-module)
- [rabbitmq_vhost – Manage the state of a virtual host in RabbitMQ](https://docs.ansible.com/ansible/latest/modules/rabbitmq_vhost_module.html#rabbitmq-vhost-module)
- [rabbitmq_vhost_limits – Manage the state of virtual host limits in RabbitMQ](https://docs.ansible.com/ansible/latest/modules/rabbitmq_vhost_limits_module.html#rabbitmq-vhost-limits-module)

## Monitoring modules

- [airbrake_deployment – Notify airbrake about app deployments](https://docs.ansible.com/ansible/latest/modules/airbrake_deployment_module.html#airbrake-deployment-module)
- [bigpanda – Notify BigPanda about deployments](https://docs.ansible.com/ansible/latest/modules/bigpanda_module.html#bigpanda-module)
- [circonus_annotation – create an annotation in circonus](https://docs.ansible.com/ansible/latest/modules/circonus_annotation_module.html#circonus-annotation-module)
- [datadog_event – Posts events to Datadog service](https://docs.ansible.com/ansible/latest/modules/datadog_event_module.html#datadog-event-module)
- [datadog_monitor – Manages Datadog monitors](https://docs.ansible.com/ansible/latest/modules/datadog_monitor_module.html#datadog-monitor-module)
- [grafana_dashboard – Manage Grafana dashboards](https://docs.ansible.com/ansible/latest/modules/grafana_dashboard_module.html#grafana-dashboard-module)
- [grafana_datasource – Manage Grafana datasources](https://docs.ansible.com/ansible/latest/modules/grafana_datasource_module.html#grafana-datasource-module)
- [grafana_plugin – Manage Grafana plugins via grafana-cli](https://docs.ansible.com/ansible/latest/modules/grafana_plugin_module.html#grafana-plugin-module)
- [honeybadger_deployment – Notify Honeybadger.io about app deployments](https://docs.ansible.com/ansible/latest/modules/honeybadger_deployment_module.html#honeybadger-deployment-module)
- [icinga2_feature – Manage Icinga2 feature](https://docs.ansible.com/ansible/latest/modules/icinga2_feature_module.html#icinga2-feature-module)
- [icinga2_host – Manage a host in Icinga2](https://docs.ansible.com/ansible/latest/modules/icinga2_host_module.html#icinga2-host-module)
- [librato_annotation – create an annotation in librato](https://docs.ansible.com/ansible/latest/modules/librato_annotation_module.html#librato-annotation-module)
- [logentries – Module for tracking logs via logentries.com](https://docs.ansible.com/ansible/latest/modules/logentries_module.html#logentries-module)
- [logicmonitor – Manage your LogicMonitor account through Ansible Playbooks](https://docs.ansible.com/ansible/latest/modules/logicmonitor_module.html#logicmonitor-module)
- [logicmonitor_facts – Collect facts about LogicMonitor objects](https://docs.ansible.com/ansible/latest/modules/logicmonitor_facts_module.html#logicmonitor-facts-module)
- [logstash_plugin – Manage Logstash plugins](https://docs.ansible.com/ansible/latest/modules/logstash_plugin_module.html#logstash-plugin-module)
- [monit – Manage the state of a program monitored via Monit](https://docs.ansible.com/ansible/latest/modules/monit_module.html#monit-module)
- [nagios – Perform common tasks in Nagios related to downtime and notifications](https://docs.ansible.com/ansible/latest/modules/nagios_module.html#nagios-module)
- [newrelic_deployment – Notify newrelic about app deployments](https://docs.ansible.com/ansible/latest/modules/newrelic_deployment_module.html#newrelic-deployment-module)
- [pagerduty – Create PagerDuty maintenance windows](https://docs.ansible.com/ansible/latest/modules/pagerduty_module.html#pagerduty-module)
- [pagerduty_alert – Trigger, acknowledge or resolve PagerDuty incidents](https://docs.ansible.com/ansible/latest/modules/pagerduty_alert_module.html#pagerduty-alert-module)
- [pingdom – Pause/unpause Pingdom alerts](https://docs.ansible.com/ansible/latest/modules/pingdom_module.html#pingdom-module)
- [rollbar_deployment – Notify Rollbar about app deployments](https://docs.ansible.com/ansible/latest/modules/rollbar_deployment_module.html#rollbar-deployment-module)
- [sensu_check – Manage Sensu checks](https://docs.ansible.com/ansible/latest/modules/sensu_check_module.html#sensu-check-module)
- [sensu_client – Manages Sensu client configuration](https://docs.ansible.com/ansible/latest/modules/sensu_client_module.html#sensu-client-module)
- [sensu_handler – Manages Sensu handler configuration](https://docs.ansible.com/ansible/latest/modules/sensu_handler_module.html#sensu-handler-module)
- [sensu_silence – Manage Sensu silence entries](https://docs.ansible.com/ansible/latest/modules/sensu_silence_module.html#sensu-silence-module)
- [sensu_subscription – Manage Sensu subscriptions](https://docs.ansible.com/ansible/latest/modules/sensu_subscription_module.html#sensu-subscription-module)
- [spectrum_device – Creates/deletes devices in CA Spectrum](https://docs.ansible.com/ansible/latest/modules/spectrum_device_module.html#spectrum-device-module)
- [stackdriver – Send code deploy and annotation events to stackdriver](https://docs.ansible.com/ansible/latest/modules/stackdriver_module.html#stackdriver-module)
- [statusio_maintenance – Create maintenance windows for your status.io dashboard](https://docs.ansible.com/ansible/latest/modules/statusio_maintenance_module.html#statusio-maintenance-module)
- [uptimerobot – Pause and start Uptime Robot monitoring](https://docs.ansible.com/ansible/latest/modules/uptimerobot_module.html#uptimerobot-module)



### Zabbix

- [zabbix_action – Create/Delete/Update Zabbix actions](https://docs.ansible.com/ansible/latest/modules/zabbix_action_module.html#zabbix-action-module)
- [zabbix_group – Create/delete Zabbix host groups](https://docs.ansible.com/ansible/latest/modules/zabbix_group_module.html#zabbix-group-module)
- [zabbix_group_info – Gather information about Zabbix hostgroup](https://docs.ansible.com/ansible/latest/modules/zabbix_group_info_module.html#zabbix-group-info-module)
- [zabbix_host – Create/update/delete Zabbix hosts](https://docs.ansible.com/ansible/latest/modules/zabbix_host_module.html#zabbix-host-module)
- [zabbix_host_info – Gather information about Zabbix host](https://docs.ansible.com/ansible/latest/modules/zabbix_host_info_module.html#zabbix-host-info-module)
- [zabbix_hostmacro – Create/update/delete Zabbix host macros](https://docs.ansible.com/ansible/latest/modules/zabbix_hostmacro_module.html#zabbix-hostmacro-module)
- [zabbix_maintenance – Create Zabbix maintenance windows](https://docs.ansible.com/ansible/latest/modules/zabbix_maintenance_module.html#zabbix-maintenance-module)
- [zabbix_map – Create/update/delete Zabbix maps](https://docs.ansible.com/ansible/latest/modules/zabbix_map_module.html#zabbix-map-module)
- [zabbix_mediatype – Create/Update/Delete Zabbix media types](https://docs.ansible.com/ansible/latest/modules/zabbix_mediatype_module.html#zabbix-mediatype-module)
- [zabbix_proxy – Create/delete/get/update Zabbix proxies](https://docs.ansible.com/ansible/latest/modules/zabbix_proxy_module.html#zabbix-proxy-module)
- [zabbix_screen – Create/update/delete Zabbix screens](https://docs.ansible.com/ansible/latest/modules/zabbix_screen_module.html#zabbix-screen-module)
- [zabbix_template – Create/update/delete/dump Zabbix template](https://docs.ansible.com/ansible/latest/modules/zabbix_template_module.html#zabbix-template-module)

## Net Tools modules

- [cloudflare_dns – Manage Cloudflare DNS records](https://docs.ansible.com/ansible/latest/modules/cloudflare_dns_module.html#cloudflare-dns-module)
- [dnsimple – Interface with dnsimple.com (a DNS hosting service)](https://docs.ansible.com/ansible/latest/modules/dnsimple_module.html#dnsimple-module)
- [dnsmadeeasy – Interface with dnsmadeeasy.com (a DNS hosting service)](https://docs.ansible.com/ansible/latest/modules/dnsmadeeasy_module.html#dnsmadeeasy-module)
- [haproxy – Enable, disable, and set weights for HAProxy backend servers using socket commands](https://docs.ansible.com/ansible/latest/modules/haproxy_module.html#haproxy-module)
- [hetzner_failover_ip – Manage Hetzner’s failover IPs](https://docs.ansible.com/ansible/latest/modules/hetzner_failover_ip_module.html#hetzner-failover-ip-module)
- [hetzner_failover_ip_info – Retrieve information on Hetzner’s failover IPs](https://docs.ansible.com/ansible/latest/modules/hetzner_failover_ip_info_module.html#hetzner-failover-ip-info-module)
- [ip_netns – Manage network namespaces](https://docs.ansible.com/ansible/latest/modules/ip_netns_module.html#ip-netns-module)
- [ipify_facts – Retrieve the public IP of your internet gateway](https://docs.ansible.com/ansible/latest/modules/ipify_facts_module.html#ipify-facts-module)
- [ipinfoio_facts – Retrieve IP geolocation facts of a host’s IP address](https://docs.ansible.com/ansible/latest/modules/ipinfoio_facts_module.html#ipinfoio-facts-module)
- [lldp – get details reported by lldp](https://docs.ansible.com/ansible/latest/modules/lldp_module.html#lldp-module)
- [netcup_dns – manage Netcup DNS records](https://docs.ansible.com/ansible/latest/modules/netcup_dns_module.html#netcup-dns-module)
- [nmcli – Manage Networking](https://docs.ansible.com/ansible/latest/modules/nmcli_module.html#nmcli-module)
- [nsupdate – Manage DNS records](https://docs.ansible.com/ansible/latest/modules/nsupdate_module.html#nsupdate-module)
- [omapi_host – Setup OMAPI hosts](https://docs.ansible.com/ansible/latest/modules/omapi_host_module.html#omapi-host-module)
- [snmp_facts – Retrieve facts for a device using SNMP](https://docs.ansible.com/ansible/latest/modules/snmp_facts_module.html#snmp-facts-module)



### Basics

- [get_url – Downloads files from HTTP, HTTPS, or FTP to node](https://docs.ansible.com/ansible/latest/modules/get_url_module.html#get-url-module)
- [slurp – Slurps a file from remote nodes](https://docs.ansible.com/ansible/latest/modules/slurp_module.html#slurp-module)
- [uri – Interacts with webservices](https://docs.ansible.com/ansible/latest/modules/uri_module.html#uri-module)



### Exoscale

- [exo_dns_domain – Manages domain records on Exoscale DNS API](https://docs.ansible.com/ansible/latest/modules/exo_dns_domain_module.html#exo-dns-domain-module)
- [exo_dns_record – Manages DNS records on Exoscale DNS](https://docs.ansible.com/ansible/latest/modules/exo_dns_record_module.html#exo-dns-record-module)



### Infinity

- [infinity – Manage Infinity IPAM using Rest API](https://docs.ansible.com/ansible/latest/modules/infinity_module.html#infinity-module)



### Ldap

- [ldap_attr – Add or remove LDAP attribute values](https://docs.ansible.com/ansible/latest/modules/ldap_attr_module.html#ldap-attr-module)
- [ldap_entry – Add or remove LDAP entries](https://docs.ansible.com/ansible/latest/modules/ldap_entry_module.html#ldap-entry-module)
- [ldap_passwd – Set passwords in LDAP](https://docs.ansible.com/ansible/latest/modules/ldap_passwd_module.html#ldap-passwd-module)



### Netbox

- [netbox_device – Create, update or delete devices within Netbox](https://docs.ansible.com/ansible/latest/modules/netbox_device_module.html#netbox-device-module)
- [netbox_interface – Creates or removes interfaces from Netbox](https://docs.ansible.com/ansible/latest/modules/netbox_interface_module.html#netbox-interface-module)
- [netbox_ip_address – Creates or removes IP addresses from Netbox](https://docs.ansible.com/ansible/latest/modules/netbox_ip_address_module.html#netbox-ip-address-module)
- [netbox_prefix – Creates or removes prefixes from Netbox](https://docs.ansible.com/ansible/latest/modules/netbox_prefix_module.html#netbox-prefix-module)
- [netbox_site – Creates or removes sites from Netbox](https://docs.ansible.com/ansible/latest/modules/netbox_site_module.html#netbox-site-module)



### Nios

- [nios_a_record – Configure Infoblox NIOS A records](https://docs.ansible.com/ansible/latest/modules/nios_a_record_module.html#nios-a-record-module)
- [nios_aaaa_record – Configure Infoblox NIOS AAAA records](https://docs.ansible.com/ansible/latest/modules/nios_aaaa_record_module.html#nios-aaaa-record-module)
- [nios_cname_record – Configure Infoblox NIOS CNAME records](https://docs.ansible.com/ansible/latest/modules/nios_cname_record_module.html#nios-cname-record-module)
- [nios_dns_view – Configure Infoblox NIOS DNS views](https://docs.ansible.com/ansible/latest/modules/nios_dns_view_module.html#nios-dns-view-module)
- [nios_fixed_address – Configure Infoblox NIOS DHCP Fixed Address](https://docs.ansible.com/ansible/latest/modules/nios_fixed_address_module.html#nios-fixed-address-module)
- [nios_host_record – Configure Infoblox NIOS host records](https://docs.ansible.com/ansible/latest/modules/nios_host_record_module.html#nios-host-record-module)
- [nios_member – Configure Infoblox NIOS members](https://docs.ansible.com/ansible/latest/modules/nios_member_module.html#nios-member-module)
- [nios_mx_record – Configure Infoblox NIOS MX records](https://docs.ansible.com/ansible/latest/modules/nios_mx_record_module.html#nios-mx-record-module)
- [nios_naptr_record – Configure Infoblox NIOS NAPTR records](https://docs.ansible.com/ansible/latest/modules/nios_naptr_record_module.html#nios-naptr-record-module)
- [nios_network – Configure Infoblox NIOS network object](https://docs.ansible.com/ansible/latest/modules/nios_network_module.html#nios-network-module)
- [nios_network_view – Configure Infoblox NIOS network views](https://docs.ansible.com/ansible/latest/modules/nios_network_view_module.html#nios-network-view-module)
- [nios_nsgroup – Configure InfoBlox DNS Nameserver Groups](https://docs.ansible.com/ansible/latest/modules/nios_nsgroup_module.html#nios-nsgroup-module)
- [nios_ptr_record – Configure Infoblox NIOS PTR records](https://docs.ansible.com/ansible/latest/modules/nios_ptr_record_module.html#nios-ptr-record-module)
- [nios_srv_record – Configure Infoblox NIOS SRV records](https://docs.ansible.com/ansible/latest/modules/nios_srv_record_module.html#nios-srv-record-module)
- [nios_txt_record – Configure Infoblox NIOS txt records](https://docs.ansible.com/ansible/latest/modules/nios_txt_record_module.html#nios-txt-record-module)
- [nios_zone – Configure Infoblox NIOS DNS zones](https://docs.ansible.com/ansible/latest/modules/nios_zone_module.html#nios-zone-module)

## Network modules

### A10

- [a10_server – Manage A10 Networks AX/SoftAX/Thunder/vThunder devices’ server object](https://docs.ansible.com/ansible/latest/modules/a10_server_module.html#a10-server-module)
- [a10_server_axapi3 – Manage A10 Networks AX/SoftAX/Thunder/vThunder devices](https://docs.ansible.com/ansible/latest/modules/a10_server_axapi3_module.html#a10-server-axapi3-module)
- [a10_service_group – Manage A10 Networks AX/SoftAX/Thunder/vThunder devices’ service groups](https://docs.ansible.com/ansible/latest/modules/a10_service_group_module.html#a10-service-group-module)
- [a10_virtual_server – Manage A10 Networks AX/SoftAX/Thunder/vThunder devices’ virtual servers](https://docs.ansible.com/ansible/latest/modules/a10_virtual_server_module.html#a10-virtual-server-module)



### Aci

- [aci_aaa_user – Manage AAA users (aaa:User)](https://docs.ansible.com/ansible/latest/modules/aci_aaa_user_module.html#aci-aaa-user-module)
- [aci_aaa_user_certificate – Manage AAA user certificates (aaa:UserCert)](https://docs.ansible.com/ansible/latest/modules/aci_aaa_user_certificate_module.html#aci-aaa-user-certificate-module)
- [aci_access_port_block_to_access_port – Manage port blocks of Fabric interface policy leaf profile interface selectors (infra:HPortS, infra:PortBlk)](https://docs.ansible.com/ansible/latest/modules/aci_access_port_block_to_access_port_module.html#aci-access-port-block-to-access-port-module)
- [aci_access_port_to_interface_policy_leaf_profile – Manage Fabric interface policy leaf profile interface selectors (infra:HPortS, infra:RsAccBaseGrp, infra:PortBlk)](https://docs.ansible.com/ansible/latest/modules/aci_access_port_to_interface_policy_leaf_profile_module.html#aci-access-port-to-interface-policy-leaf-profile-module)
- [aci_access_sub_port_block_to_access_port – Manage sub port blocks of Fabric interface policy leaf profile interface selectors (infra:HPortS, infra:SubPortBlk)](https://docs.ansible.com/ansible/latest/modules/aci_access_sub_port_block_to_access_port_module.html#aci-access-sub-port-block-to-access-port-module)
- [aci_aep – Manage attachable Access Entity Profile (AEP) objects (infra:AttEntityP, infra:ProvAcc)](https://docs.ansible.com/ansible/latest/modules/aci_aep_module.html#aci-aep-module)
- [aci_aep_to_domain – Bind AEPs to Physical or Virtual Domains (infra:RsDomP)](https://docs.ansible.com/ansible/latest/modules/aci_aep_to_domain_module.html#aci-aep-to-domain-module)
- [aci_ap – Manage top level Application Profile (AP) objects (fv:Ap)](https://docs.ansible.com/ansible/latest/modules/aci_ap_module.html#aci-ap-module)
- [aci_bd – Manage Bridge Domains (BD) objects (fv:BD)](https://docs.ansible.com/ansible/latest/modules/aci_bd_module.html#aci-bd-module)
- [aci_bd_subnet – Manage Subnets (fv:Subnet)](https://docs.ansible.com/ansible/latest/modules/aci_bd_subnet_module.html#aci-bd-subnet-module)
- [aci_bd_to_l3out – Bind Bridge Domain to L3 Out (fv:RsBDToOut)](https://docs.ansible.com/ansible/latest/modules/aci_bd_to_l3out_module.html#aci-bd-to-l3out-module)
- [aci_config_rollback – Provides rollback and rollback preview functionality (config:ImportP)](https://docs.ansible.com/ansible/latest/modules/aci_config_rollback_module.html#aci-config-rollback-module)
- [aci_config_snapshot – Manage Config Snapshots (config:Snapshot, config:ExportP)](https://docs.ansible.com/ansible/latest/modules/aci_config_snapshot_module.html#aci-config-snapshot-module)
- [aci_contract – Manage contract resources (vz:BrCP)](https://docs.ansible.com/ansible/latest/modules/aci_contract_module.html#aci-contract-module)
- [aci_contract_subject – Manage initial Contract Subjects (vz:Subj)](https://docs.ansible.com/ansible/latest/modules/aci_contract_subject_module.html#aci-contract-subject-module)
- [aci_contract_subject_to_filter – Bind Contract Subjects to Filters (vz:RsSubjFiltAtt)](https://docs.ansible.com/ansible/latest/modules/aci_contract_subject_to_filter_module.html#aci-contract-subject-to-filter-module)
- [aci_domain – Manage physical, virtual, bridged, routed or FC domain profiles (phys:DomP, vmm:DomP, l2ext:DomP, l3ext:DomP, fc:DomP)](https://docs.ansible.com/ansible/latest/modules/aci_domain_module.html#aci-domain-module)
- [aci_domain_to_encap_pool – Bind Domain to Encap Pools (infra:RsVlanNs)](https://docs.ansible.com/ansible/latest/modules/aci_domain_to_encap_pool_module.html#aci-domain-to-encap-pool-module)
- [aci_domain_to_vlan_pool – Bind Domain to VLAN Pools (infra:RsVlanNs)](https://docs.ansible.com/ansible/latest/modules/aci_domain_to_vlan_pool_module.html#aci-domain-to-vlan-pool-module)
- [aci_encap_pool – Manage encap pools (fvns:VlanInstP, fvns:VxlanInstP, fvns:VsanInstP)](https://docs.ansible.com/ansible/latest/modules/aci_encap_pool_module.html#aci-encap-pool-module)
- [aci_encap_pool_range – Manage encap ranges assigned to pools (fvns:EncapBlk, fvns:VsanEncapBlk)](https://docs.ansible.com/ansible/latest/modules/aci_encap_pool_range_module.html#aci-encap-pool-range-module)
- [aci_epg – Manage End Point Groups (EPG) objects (fv:AEPg)](https://docs.ansible.com/ansible/latest/modules/aci_epg_module.html#aci-epg-module)
- [aci_epg_monitoring_policy – Manage monitoring policies (mon:EPGPol)](https://docs.ansible.com/ansible/latest/modules/aci_epg_monitoring_policy_module.html#aci-epg-monitoring-policy-module)
- [aci_epg_to_contract – Bind EPGs to Contracts (fv:RsCons, fv:RsProv)](https://docs.ansible.com/ansible/latest/modules/aci_epg_to_contract_module.html#aci-epg-to-contract-module)
- [aci_epg_to_domain – Bind EPGs to Domains (fv:RsDomAtt)](https://docs.ansible.com/ansible/latest/modules/aci_epg_to_domain_module.html#aci-epg-to-domain-module)
- [aci_fabric_node – Manage Fabric Node Members (fabric:NodeIdentP)](https://docs.ansible.com/ansible/latest/modules/aci_fabric_node_module.html#aci-fabric-node-module)
- [aci_fabric_scheduler – This modules creates ACI schedulers](https://docs.ansible.com/ansible/latest/modules/aci_fabric_scheduler_module.html#aci-fabric-scheduler-module)
- [aci_filter – Manages top level filter objects (vz:Filter)](https://docs.ansible.com/ansible/latest/modules/aci_filter_module.html#aci-filter-module)
- [aci_filter_entry – Manage filter entries (vz:Entry)](https://docs.ansible.com/ansible/latest/modules/aci_filter_entry_module.html#aci-filter-entry-module)
- [aci_firmware_group – This module creates a firmware group](https://docs.ansible.com/ansible/latest/modules/aci_firmware_group_module.html#aci-firmware-group-module)
- [aci_firmware_group_node – This modules adds and remove nodes from the firmware group](https://docs.ansible.com/ansible/latest/modules/aci_firmware_group_node_module.html#aci-firmware-group-node-module)
- [aci_firmware_policy – This creates a firmware policy](https://docs.ansible.com/ansible/latest/modules/aci_firmware_policy_module.html#aci-firmware-policy-module)
- [aci_firmware_source – Manage firmware image sources (firmware:OSource)](https://docs.ansible.com/ansible/latest/modules/aci_firmware_source_module.html#aci-firmware-source-module)
- [aci_interface_policy_cdp – Manage CDP interface policies (cdp:IfPol)](https://docs.ansible.com/ansible/latest/modules/aci_interface_policy_cdp_module.html#aci-interface-policy-cdp-module)
- [aci_interface_policy_fc – Manage Fibre Channel interface policies (fc:IfPol)](https://docs.ansible.com/ansible/latest/modules/aci_interface_policy_fc_module.html#aci-interface-policy-fc-module)
- [aci_interface_policy_l2 – Manage Layer 2 interface policies (l2:IfPol)](https://docs.ansible.com/ansible/latest/modules/aci_interface_policy_l2_module.html#aci-interface-policy-l2-module)
- [aci_interface_policy_leaf_policy_group – Manage fabric interface policy leaf policy groups (infra:AccBndlGrp, infra:AccPortGrp)](https://docs.ansible.com/ansible/latest/modules/aci_interface_policy_leaf_policy_group_module.html#aci-interface-policy-leaf-policy-group-module)
- [aci_interface_policy_leaf_profile – Manage fabric interface policy leaf profiles (infra:AccPortP)](https://docs.ansible.com/ansible/latest/modules/aci_interface_policy_leaf_profile_module.html#aci-interface-policy-leaf-profile-module)
- [aci_interface_policy_lldp – Manage LLDP interface policies (lldp:IfPol)](https://docs.ansible.com/ansible/latest/modules/aci_interface_policy_lldp_module.html#aci-interface-policy-lldp-module)
- [aci_interface_policy_mcp – Manage MCP interface policies (mcp:IfPol)](https://docs.ansible.com/ansible/latest/modules/aci_interface_policy_mcp_module.html#aci-interface-policy-mcp-module)
- [aci_interface_policy_ospf – Manage OSPF interface policies (ospf:IfPol)](https://docs.ansible.com/ansible/latest/modules/aci_interface_policy_ospf_module.html#aci-interface-policy-ospf-module)
- [aci_interface_policy_port_channel – Manage port channel interface policies (lacp:LagPol)](https://docs.ansible.com/ansible/latest/modules/aci_interface_policy_port_channel_module.html#aci-interface-policy-port-channel-module)
- [aci_interface_policy_port_security – Manage port security (l2:PortSecurityPol)](https://docs.ansible.com/ansible/latest/modules/aci_interface_policy_port_security_module.html#aci-interface-policy-port-security-module)
- [aci_interface_selector_to_switch_policy_leaf_profile – Bind interface selector profiles to switch policy leaf profiles (infra:RsAccPortP)](https://docs.ansible.com/ansible/latest/modules/aci_interface_selector_to_switch_policy_leaf_profile_module.html#aci-interface-selector-to-switch-policy-leaf-profile-module)
- [aci_l3out – Manage Layer 3 Outside (L3Out) objects (l3ext:Out)](https://docs.ansible.com/ansible/latest/modules/aci_l3out_module.html#aci-l3out-module)
- [aci_l3out_extepg – Manage External Network Instance Profile (ExtEpg) objects (l3extInstP:instP)](https://docs.ansible.com/ansible/latest/modules/aci_l3out_extepg_module.html#aci-l3out-extepg-module)
- [aci_l3out_extsubnet – Manage External Subnet objects (l3extSubnet:extsubnet)](https://docs.ansible.com/ansible/latest/modules/aci_l3out_extsubnet_module.html#aci-l3out-extsubnet-module)
- [aci_l3out_route_tag_policy – Manage route tag policies (l3ext:RouteTagPol)](https://docs.ansible.com/ansible/latest/modules/aci_l3out_route_tag_policy_module.html#aci-l3out-route-tag-policy-module)
- [aci_maintenance_group – This creates an ACI maintenance group](https://docs.ansible.com/ansible/latest/modules/aci_maintenance_group_module.html#aci-maintenance-group-module)
- [aci_maintenance_group_node – Manage maintenance group nodes](https://docs.ansible.com/ansible/latest/modules/aci_maintenance_group_node_module.html#aci-maintenance-group-node-module)
- [aci_maintenance_policy – Manage firmware maintenance policies](https://docs.ansible.com/ansible/latest/modules/aci_maintenance_policy_module.html#aci-maintenance-policy-module)
- [aci_rest – Direct access to the Cisco APIC REST API](https://docs.ansible.com/ansible/latest/modules/aci_rest_module.html#aci-rest-module)
- [aci_static_binding_to_epg – Bind static paths to EPGs (fv:RsPathAtt)](https://docs.ansible.com/ansible/latest/modules/aci_static_binding_to_epg_module.html#aci-static-binding-to-epg-module)
- [aci_switch_leaf_selector – Bind leaf selectors to switch policy leaf profiles (infra:LeafS, infra:NodeBlk, infra:RsAccNodePGrep)](https://docs.ansible.com/ansible/latest/modules/aci_switch_leaf_selector_module.html#aci-switch-leaf-selector-module)
- [aci_switch_policy_leaf_profile – Manage switch policy leaf profiles (infra:NodeP)](https://docs.ansible.com/ansible/latest/modules/aci_switch_policy_leaf_profile_module.html#aci-switch-policy-leaf-profile-module)
- [aci_switch_policy_vpc_protection_group – Manage switch policy explicit vPC protection groups (fabric:ExplicitGEp, fabric:NodePEp)](https://docs.ansible.com/ansible/latest/modules/aci_switch_policy_vpc_protection_group_module.html#aci-switch-policy-vpc-protection-group-module)
- [aci_taboo_contract – Manage taboo contracts (vz:BrCP)](https://docs.ansible.com/ansible/latest/modules/aci_taboo_contract_module.html#aci-taboo-contract-module)
- [aci_tenant – Manage tenants (fv:Tenant)](https://docs.ansible.com/ansible/latest/modules/aci_tenant_module.html#aci-tenant-module)
- [aci_tenant_action_rule_profile – Manage action rule profiles (rtctrl:AttrP)](https://docs.ansible.com/ansible/latest/modules/aci_tenant_action_rule_profile_module.html#aci-tenant-action-rule-profile-module)
- [aci_tenant_ep_retention_policy – Manage End Point (EP) retention protocol policies (fv:EpRetPol)](https://docs.ansible.com/ansible/latest/modules/aci_tenant_ep_retention_policy_module.html#aci-tenant-ep-retention-policy-module)
- [aci_tenant_span_dst_group – Manage SPAN destination groups (span:DestGrp)](https://docs.ansible.com/ansible/latest/modules/aci_tenant_span_dst_group_module.html#aci-tenant-span-dst-group-module)
- [aci_tenant_span_src_group – Manage SPAN source groups (span:SrcGrp)](https://docs.ansible.com/ansible/latest/modules/aci_tenant_span_src_group_module.html#aci-tenant-span-src-group-module)
- [aci_tenant_span_src_group_to_dst_group – Bind SPAN source groups to destination groups (span:SpanLbl)](https://docs.ansible.com/ansible/latest/modules/aci_tenant_span_src_group_to_dst_group_module.html#aci-tenant-span-src-group-to-dst-group-module)
- [aci_vlan_pool – Manage VLAN pools (fvns:VlanInstP)](https://docs.ansible.com/ansible/latest/modules/aci_vlan_pool_module.html#aci-vlan-pool-module)
- [aci_vlan_pool_encap_block – Manage encap blocks assigned to VLAN pools (fvns:EncapBlk)](https://docs.ansible.com/ansible/latest/modules/aci_vlan_pool_encap_block_module.html#aci-vlan-pool-encap-block-module)
- [aci_vmm_credential – Manage virtual domain credential profiles (vmm:UsrAccP)](https://docs.ansible.com/ansible/latest/modules/aci_vmm_credential_module.html#aci-vmm-credential-module)
- [aci_vrf – Manage contexts or VRFs (fv:Ctx)](https://docs.ansible.com/ansible/latest/modules/aci_vrf_module.html#aci-vrf-module)
- [mso_label – Manage labels](https://docs.ansible.com/ansible/latest/modules/mso_label_module.html#mso-label-module)
- [mso_role – Manage roles](https://docs.ansible.com/ansible/latest/modules/mso_role_module.html#mso-role-module)
- [mso_schema – Manage schemas](https://docs.ansible.com/ansible/latest/modules/mso_schema_module.html#mso-schema-module)
- [mso_schema_site – Manage sites in schemas](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_module.html#mso-schema-site-module)
- [mso_schema_site_anp – Manage site-local Application Network Profiles (ANPs) in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_anp_module.html#mso-schema-site-anp-module)
- [mso_schema_site_anp_epg – Manage site-local Endpoint Groups (EPGs) in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_anp_epg_module.html#mso-schema-site-anp-epg-module)
- [mso_schema_site_anp_epg_domain – Manage site-local EPG domains in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_anp_epg_domain_module.html#mso-schema-site-anp-epg-domain-module)
- [mso_schema_site_anp_epg_staticleaf – Manage site-local EPG static leafs in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_anp_epg_staticleaf_module.html#mso-schema-site-anp-epg-staticleaf-module)
- [mso_schema_site_anp_epg_staticport – Manage site-local EPG static ports in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_anp_epg_staticport_module.html#mso-schema-site-anp-epg-staticport-module)
- [mso_schema_site_anp_epg_subnet – Manage site-local EPG subnets in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_anp_epg_subnet_module.html#mso-schema-site-anp-epg-subnet-module)
- [mso_schema_site_bd – Manage site-local Bridge Domains (BDs) in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_bd_module.html#mso-schema-site-bd-module)
- [mso_schema_site_bd_l3out – Manage site-local BD l3out’s in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_bd_l3out_module.html#mso-schema-site-bd-l3out-module)
- [mso_schema_site_bd_subnet – Manage site-local BD subnets in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_bd_subnet_module.html#mso-schema-site-bd-subnet-module)
- [mso_schema_site_vrf – Manage site-local VRFs in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_vrf_module.html#mso-schema-site-vrf-module)
- [mso_schema_site_vrf_region – Manage site-local VRF regions in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_vrf_region_module.html#mso-schema-site-vrf-region-module)
- [mso_schema_site_vrf_region_cidr – Manage site-local VRF region CIDRs in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_vrf_region_cidr_module.html#mso-schema-site-vrf-region-cidr-module)
- [mso_schema_site_vrf_region_cidr_subnet – Manage site-local VRF regions in schema template](https://docs.ansible.com/ansible/latest/modules/mso_schema_site_vrf_region_cidr_subnet_module.html#mso-schema-site-vrf-region-cidr-subnet-module)
- [mso_schema_template – Manage templates in schemas](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_module.html#mso-schema-template-module)
- [mso_schema_template_anp – Manage Application Network Profiles (ANPs) in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_anp_module.html#mso-schema-template-anp-module)
- [mso_schema_template_anp_epg – Manage Endpoint Groups (EPGs) in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_anp_epg_module.html#mso-schema-template-anp-epg-module)
- [mso_schema_template_anp_epg_contract – Manage EPG contracts in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_anp_epg_contract_module.html#mso-schema-template-anp-epg-contract-module)
- [mso_schema_template_anp_epg_subnet – Manage EPG subnets in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_anp_epg_subnet_module.html#mso-schema-template-anp-epg-subnet-module)
- [mso_schema_template_bd – Manage Bridge Domains (BDs) in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_bd_module.html#mso-schema-template-bd-module)
- [mso_schema_template_bd_subnet – Manage BD subnets in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_bd_subnet_module.html#mso-schema-template-bd-subnet-module)
- [mso_schema_template_contract_filter – Manage contract filters in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_contract_filter_module.html#mso-schema-template-contract-filter-module)
- [mso_schema_template_deploy – Deploy schema templates to sites](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_deploy_module.html#mso-schema-template-deploy-module)
- [mso_schema_template_externalepg – Manage external EPGs in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_externalepg_module.html#mso-schema-template-externalepg-module)
- [mso_schema_template_filter_entry – Manage filter entries in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_filter_entry_module.html#mso-schema-template-filter-entry-module)
- [mso_schema_template_l3out – Manage l3outs in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_l3out_module.html#mso-schema-template-l3out-module)
- [mso_schema_template_vrf – Manage VRFs in schema templates](https://docs.ansible.com/ansible/latest/modules/mso_schema_template_vrf_module.html#mso-schema-template-vrf-module)
- [mso_site – Manage sites](https://docs.ansible.com/ansible/latest/modules/mso_site_module.html#mso-site-module)
- [mso_tenant – Manage tenants](https://docs.ansible.com/ansible/latest/modules/mso_tenant_module.html#mso-tenant-module)
- [mso_user – Manage users](https://docs.ansible.com/ansible/latest/modules/mso_user_module.html#mso-user-module)



### Aireos

- [aireos_command – Run commands on remote devices running Cisco WLC](https://docs.ansible.com/ansible/latest/modules/aireos_command_module.html#aireos-command-module)
- [aireos_config – Manage Cisco WLC configurations](https://docs.ansible.com/ansible/latest/modules/aireos_config_module.html#aireos-config-module)



### Aruba

- [aruba_command – Run commands on remote devices running Aruba Mobility Controller](https://docs.ansible.com/ansible/latest/modules/aruba_command_module.html#aruba-command-module)
- [aruba_config – Manage Aruba configuration sections](https://docs.ansible.com/ansible/latest/modules/aruba_config_module.html#aruba-config-module)



### Asa

- [asa_acl – Manage access-lists on a Cisco ASA](https://docs.ansible.com/ansible/latest/modules/asa_acl_module.html#asa-acl-module)
- [asa_command – Run arbitrary commands on Cisco ASA devices](https://docs.ansible.com/ansible/latest/modules/asa_command_module.html#asa-command-module)
- [asa_config – Manage configuration sections on Cisco ASA devices](https://docs.ansible.com/ansible/latest/modules/asa_config_module.html#asa-config-module)
- [asa_og – Manage object groups on a Cisco ASA](https://docs.ansible.com/ansible/latest/modules/asa_og_module.html#asa-og-module)



### Avi

- [avi_actiongroupconfig – Module for setup of ActionGroupConfig Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_actiongroupconfig_module.html#avi-actiongroupconfig-module)
- [avi_alertconfig – Module for setup of AlertConfig Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_alertconfig_module.html#avi-alertconfig-module)
- [avi_alertemailconfig – Module for setup of AlertEmailConfig Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_alertemailconfig_module.html#avi-alertemailconfig-module)
- [avi_alertscriptconfig – Module for setup of AlertScriptConfig Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_alertscriptconfig_module.html#avi-alertscriptconfig-module)
- [avi_alertsyslogconfig – Module for setup of AlertSyslogConfig Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_alertsyslogconfig_module.html#avi-alertsyslogconfig-module)
- [avi_analyticsprofile – Module for setup of AnalyticsProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_analyticsprofile_module.html#avi-analyticsprofile-module)
- [avi_api_session – Avi API Module](https://docs.ansible.com/ansible/latest/modules/avi_api_session_module.html#avi-api-session-module)
- [avi_api_version – Avi API Version Module](https://docs.ansible.com/ansible/latest/modules/avi_api_version_module.html#avi-api-version-module)
- [avi_applicationpersistenceprofile – Module for setup of ApplicationPersistenceProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_applicationpersistenceprofile_module.html#avi-applicationpersistenceprofile-module)
- [avi_applicationprofile – Module for setup of ApplicationProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_applicationprofile_module.html#avi-applicationprofile-module)
- [avi_authprofile – Module for setup of AuthProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_authprofile_module.html#avi-authprofile-module)
- [avi_autoscalelaunchconfig – Module for setup of AutoScaleLaunchConfig Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_autoscalelaunchconfig_module.html#avi-autoscalelaunchconfig-module)
- [avi_backup – Module for setup of Backup Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_backup_module.html#avi-backup-module)
- [avi_backupconfiguration – Module for setup of BackupConfiguration Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_backupconfiguration_module.html#avi-backupconfiguration-module)
- [avi_certificatemanagementprofile – Module for setup of CertificateManagementProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_certificatemanagementprofile_module.html#avi-certificatemanagementprofile-module)
- [avi_cloud – Module for setup of Cloud Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_cloud_module.html#avi-cloud-module)
- [avi_cloudconnectoruser – Module for setup of CloudConnectorUser Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_cloudconnectoruser_module.html#avi-cloudconnectoruser-module)
- [avi_cloudproperties – Module for setup of CloudProperties Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_cloudproperties_module.html#avi-cloudproperties-module)
- [avi_cluster – Module for setup of Cluster Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_cluster_module.html#avi-cluster-module)
- [avi_clusterclouddetails – Module for setup of ClusterCloudDetails Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_clusterclouddetails_module.html#avi-clusterclouddetails-module)
- [avi_controllerproperties – Module for setup of ControllerProperties Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_controllerproperties_module.html#avi-controllerproperties-module)
- [avi_customipamdnsprofile – Module for setup of CustomIpamDnsProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_customipamdnsprofile_module.html#avi-customipamdnsprofile-module)
- [avi_dnspolicy – Module for setup of DnsPolicy Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_dnspolicy_module.html#avi-dnspolicy-module)
- [avi_errorpagebody – Module for setup of ErrorPageBody Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_errorpagebody_module.html#avi-errorpagebody-module)
- [avi_errorpageprofile – Module for setup of ErrorPageProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_errorpageprofile_module.html#avi-errorpageprofile-module)
- [avi_gslb – Module for setup of Gslb Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_gslb_module.html#avi-gslb-module)
- [avi_gslbgeodbprofile – Module for setup of GslbGeoDbProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_gslbgeodbprofile_module.html#avi-gslbgeodbprofile-module)
- [avi_gslbservice – Module for setup of GslbService Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_gslbservice_module.html#avi-gslbservice-module)
- [avi_gslbservice_patch_member – Avi API Module](https://docs.ansible.com/ansible/latest/modules/avi_gslbservice_patch_member_module.html#avi-gslbservice-patch-member-module)
- [avi_hardwaresecuritymodulegroup – Module for setup of HardwareSecurityModuleGroup Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_hardwaresecuritymodulegroup_module.html#avi-hardwaresecuritymodulegroup-module)
- [avi_healthmonitor – Module for setup of HealthMonitor Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_healthmonitor_module.html#avi-healthmonitor-module)
- [avi_httppolicyset – Module for setup of HTTPPolicySet Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_httppolicyset_module.html#avi-httppolicyset-module)
- [avi_ipaddrgroup – Module for setup of IpAddrGroup Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_ipaddrgroup_module.html#avi-ipaddrgroup-module)
- [avi_ipamdnsproviderprofile – Module for setup of IpamDnsProviderProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_ipamdnsproviderprofile_module.html#avi-ipamdnsproviderprofile-module)
- [avi_l4policyset – Module for setup of L4PolicySet Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_l4policyset_module.html#avi-l4policyset-module)
- [avi_microservicegroup – Module for setup of MicroServiceGroup Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_microservicegroup_module.html#avi-microservicegroup-module)
- [avi_network – Module for setup of Network Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_network_module.html#avi-network-module)
- [avi_networkprofile – Module for setup of NetworkProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_networkprofile_module.html#avi-networkprofile-module)
- [avi_networksecuritypolicy – Module for setup of NetworkSecurityPolicy Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_networksecuritypolicy_module.html#avi-networksecuritypolicy-module)
- [avi_pkiprofile – Module for setup of PKIProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_pkiprofile_module.html#avi-pkiprofile-module)
- [avi_pool – Module for setup of Pool Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_pool_module.html#avi-pool-module)
- [avi_poolgroup – Module for setup of PoolGroup Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_poolgroup_module.html#avi-poolgroup-module)
- [avi_poolgroupdeploymentpolicy – Module for setup of PoolGroupDeploymentPolicy Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_poolgroupdeploymentpolicy_module.html#avi-poolgroupdeploymentpolicy-module)
- [avi_prioritylabels – Module for setup of PriorityLabels Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_prioritylabels_module.html#avi-prioritylabels-module)
- [avi_role – Module for setup of Role Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_role_module.html#avi-role-module)
- [avi_scheduler – Module for setup of Scheduler Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_scheduler_module.html#avi-scheduler-module)
- [avi_seproperties – Module for setup of SeProperties Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_seproperties_module.html#avi-seproperties-module)
- [avi_serverautoscalepolicy – Module for setup of ServerAutoScalePolicy Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_serverautoscalepolicy_module.html#avi-serverautoscalepolicy-module)
- [avi_serviceengine – Module for setup of ServiceEngine Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_serviceengine_module.html#avi-serviceengine-module)
- [avi_serviceenginegroup – Module for setup of ServiceEngineGroup Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_serviceenginegroup_module.html#avi-serviceenginegroup-module)
- [avi_snmptrapprofile – Module for setup of SnmpTrapProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_snmptrapprofile_module.html#avi-snmptrapprofile-module)
- [avi_sslkeyandcertificate – Module for setup of SSLKeyAndCertificate Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_sslkeyandcertificate_module.html#avi-sslkeyandcertificate-module)
- [avi_sslprofile – Module for setup of SSLProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_sslprofile_module.html#avi-sslprofile-module)
- [avi_stringgroup – Module for setup of StringGroup Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_stringgroup_module.html#avi-stringgroup-module)
- [avi_systemconfiguration – Module for setup of SystemConfiguration Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_systemconfiguration_module.html#avi-systemconfiguration-module)
- [avi_tenant – Module for setup of Tenant Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_tenant_module.html#avi-tenant-module)
- [avi_trafficcloneprofile – Module for setup of TrafficCloneProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_trafficcloneprofile_module.html#avi-trafficcloneprofile-module)
- [avi_user – Avi User Module](https://docs.ansible.com/ansible/latest/modules/avi_user_module.html#avi-user-module)
- [avi_useraccount – Avi UserAccount Module](https://docs.ansible.com/ansible/latest/modules/avi_useraccount_module.html#avi-useraccount-module)
- [avi_useraccountprofile – Module for setup of UserAccountProfile Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_useraccountprofile_module.html#avi-useraccountprofile-module)
- [avi_virtualservice – Module for setup of VirtualService Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_virtualservice_module.html#avi-virtualservice-module)
- [avi_vrfcontext – Module for setup of VrfContext Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_vrfcontext_module.html#avi-vrfcontext-module)
- [avi_vsdatascriptset – Module for setup of VSDataScriptSet Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_vsdatascriptset_module.html#avi-vsdatascriptset-module)
- [avi_vsvip – Module for setup of VsVip Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_vsvip_module.html#avi-vsvip-module)
- [avi_webhook – Module for setup of Webhook Avi RESTful Object](https://docs.ansible.com/ansible/latest/modules/avi_webhook_module.html#avi-webhook-module)



### Bigswitch

- [bcf_switch – Create and remove a bcf switch](https://docs.ansible.com/ansible/latest/modules/bcf_switch_module.html#bcf-switch-module)
- [bigmon_chain – Create and remove a bigmon inline service chain](https://docs.ansible.com/ansible/latest/modules/bigmon_chain_module.html#bigmon-chain-module)
- [bigmon_policy – Create and remove a bigmon out-of-band policy](https://docs.ansible.com/ansible/latest/modules/bigmon_policy_module.html#bigmon-policy-module)



### Check_Point

- [checkpoint_access_layer_facts – Get access layer facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/checkpoint_access_layer_facts_module.html#checkpoint-access-layer-facts-module)
- [checkpoint_access_rule – Manages access rules on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/checkpoint_access_rule_module.html#checkpoint-access-rule-module)
- [checkpoint_access_rule_facts – Get access rules objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/checkpoint_access_rule_facts_module.html#checkpoint-access-rule-facts-module)
- [checkpoint_host – Manages host objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/checkpoint_host_module.html#checkpoint-host-module)
- [checkpoint_host_facts – Get host objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/checkpoint_host_facts_module.html#checkpoint-host-facts-module)
- [checkpoint_object_facts – Get object facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/checkpoint_object_facts_module.html#checkpoint-object-facts-module)
- [checkpoint_run_script – Run scripts on Check Point devices over Web Services API](https://docs.ansible.com/ansible/latest/modules/checkpoint_run_script_module.html#checkpoint-run-script-module)
- [checkpoint_session – Manages session objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/checkpoint_session_module.html#checkpoint-session-module)
- [checkpoint_task_facts – Get task objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/checkpoint_task_facts_module.html#checkpoint-task-facts-module)
- [cp_mgmt_access_layer – Manages access-layer objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_access_layer_module.html#cp-mgmt-access-layer-module)
- [cp_mgmt_access_layer_facts – Get access-layer objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_access_layer_facts_module.html#cp-mgmt-access-layer-facts-module)
- [cp_mgmt_access_role – Manages access-role objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_access_role_module.html#cp-mgmt-access-role-module)
- [cp_mgmt_access_role_facts – Get access-role objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_access_role_facts_module.html#cp-mgmt-access-role-facts-module)
- [cp_mgmt_access_rule – Manages access-rule objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_access_rule_module.html#cp-mgmt-access-rule-module)
- [cp_mgmt_access_rule_facts – Get access-rule objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_access_rule_facts_module.html#cp-mgmt-access-rule-facts-module)
- [cp_mgmt_address_range – Manages address-range objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_address_range_module.html#cp-mgmt-address-range-module)
- [cp_mgmt_address_range_facts – Get address-range objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_address_range_facts_module.html#cp-mgmt-address-range-facts-module)
- [cp_mgmt_administrator – Manages administrator objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_administrator_module.html#cp-mgmt-administrator-module)
- [cp_mgmt_administrator_facts – Get administrator objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_administrator_facts_module.html#cp-mgmt-administrator-facts-module)
- [cp_mgmt_application_site – Manages application-site objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_application_site_module.html#cp-mgmt-application-site-module)
- [cp_mgmt_application_site_category – Manages application-site-category objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_application_site_category_module.html#cp-mgmt-application-site-category-module)
- [cp_mgmt_application_site_category_facts – Get application-site-category objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_application_site_category_facts_module.html#cp-mgmt-application-site-category-facts-module)
- [cp_mgmt_application_site_facts – Get application-site objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_application_site_facts_module.html#cp-mgmt-application-site-facts-module)
- [cp_mgmt_application_site_group – Manages application-site-group objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_application_site_group_module.html#cp-mgmt-application-site-group-module)
- [cp_mgmt_application_site_group_facts – Get application-site-group objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_application_site_group_facts_module.html#cp-mgmt-application-site-group-facts-module)
- [cp_mgmt_assign_global_assignment – assign global assignment on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_assign_global_assignment_module.html#cp-mgmt-assign-global-assignment-module)
- [cp_mgmt_discard – All changes done by user are discarded and removed from database](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_discard_module.html#cp-mgmt-discard-module)
- [cp_mgmt_dns_domain – Manages dns-domain objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_dns_domain_module.html#cp-mgmt-dns-domain-module)
- [cp_mgmt_dns_domain_facts – Get dns-domain objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_dns_domain_facts_module.html#cp-mgmt-dns-domain-facts-module)
- [cp_mgmt_dynamic_object – Manages dynamic-object objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_dynamic_object_module.html#cp-mgmt-dynamic-object-module)
- [cp_mgmt_dynamic_object_facts – Get dynamic-object objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_dynamic_object_facts_module.html#cp-mgmt-dynamic-object-facts-module)
- [cp_mgmt_exception_group – Manages exception-group objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_exception_group_module.html#cp-mgmt-exception-group-module)
- [cp_mgmt_exception_group_facts – Get exception-group objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_exception_group_facts_module.html#cp-mgmt-exception-group-facts-module)
- [cp_mgmt_global_assignment – Manages global-assignment objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_global_assignment_module.html#cp-mgmt-global-assignment-module)
- [cp_mgmt_global_assignment_facts – Get global-assignment objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_global_assignment_facts_module.html#cp-mgmt-global-assignment-facts-module)
- [cp_mgmt_group – Manages group objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_group_module.html#cp-mgmt-group-module)
- [cp_mgmt_group_facts – Get group objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_group_facts_module.html#cp-mgmt-group-facts-module)
- [cp_mgmt_group_with_exclusion – Manages group-with-exclusion objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_group_with_exclusion_module.html#cp-mgmt-group-with-exclusion-module)
- [cp_mgmt_group_with_exclusion_facts – Get group-with-exclusion objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_group_with_exclusion_facts_module.html#cp-mgmt-group-with-exclusion-facts-module)
- [cp_mgmt_host – Manages host objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_host_module.html#cp-mgmt-host-module)
- [cp_mgmt_host_facts – Get host objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_host_facts_module.html#cp-mgmt-host-facts-module)
- [cp_mgmt_install_policy – install policy on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_install_policy_module.html#cp-mgmt-install-policy-module)
- [cp_mgmt_mds_facts – Get Multi-Domain Server (mds) objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_mds_facts_module.html#cp-mgmt-mds-facts-module)
- [cp_mgmt_multicast_address_range – Manages multicast-address-range objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_multicast_address_range_module.html#cp-mgmt-multicast-address-range-module)
- [cp_mgmt_multicast_address_range_facts – Get multicast-address-range objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_multicast_address_range_facts_module.html#cp-mgmt-multicast-address-range-facts-module)
- [cp_mgmt_network – Manages network objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_network_module.html#cp-mgmt-network-module)
- [cp_mgmt_network_facts – Get network objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_network_facts_module.html#cp-mgmt-network-facts-module)
- [cp_mgmt_package – Manages package objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_package_module.html#cp-mgmt-package-module)
- [cp_mgmt_package_facts – Get package objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_package_facts_module.html#cp-mgmt-package-facts-module)
- [cp_mgmt_publish – All the changes done by this user will be seen by all users only after publish is called](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_publish_module.html#cp-mgmt-publish-module)
- [cp_mgmt_put_file – put file on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_put_file_module.html#cp-mgmt-put-file-module)
- [cp_mgmt_run_ips_update – Runs IPS database update. If “package-path” is not provided server will try to get the latest package from the User Center](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_run_ips_update_module.html#cp-mgmt-run-ips-update-module)
- [cp_mgmt_run_script – Executes the script on a given list of targets](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_run_script_module.html#cp-mgmt-run-script-module)
- [cp_mgmt_security_zone – Manages security-zone objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_security_zone_module.html#cp-mgmt-security-zone-module)
- [cp_mgmt_security_zone_facts – Get security-zone objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_security_zone_facts_module.html#cp-mgmt-security-zone-facts-module)
- [cp_mgmt_service_dce_rpc – Manages service-dce-rpc objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_dce_rpc_module.html#cp-mgmt-service-dce-rpc-module)
- [cp_mgmt_service_dce_rpc_facts – Get service-dce-rpc objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_dce_rpc_facts_module.html#cp-mgmt-service-dce-rpc-facts-module)
- [cp_mgmt_service_group – Manages service-group objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_group_module.html#cp-mgmt-service-group-module)
- [cp_mgmt_service_group_facts – Get service-group objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_group_facts_module.html#cp-mgmt-service-group-facts-module)
- [cp_mgmt_service_icmp – Manages service-icmp objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_icmp_module.html#cp-mgmt-service-icmp-module)
- [cp_mgmt_service_icmp6 – Manages service-icmp6 objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_icmp6_module.html#cp-mgmt-service-icmp6-module)
- [cp_mgmt_service_icmp6_facts – Get service-icmp6 objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_icmp6_facts_module.html#cp-mgmt-service-icmp6-facts-module)
- [cp_mgmt_service_icmp_facts – Get service-icmp objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_icmp_facts_module.html#cp-mgmt-service-icmp-facts-module)
- [cp_mgmt_service_other – Manages service-other objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_other_module.html#cp-mgmt-service-other-module)
- [cp_mgmt_service_other_facts – Get service-other objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_other_facts_module.html#cp-mgmt-service-other-facts-module)
- [cp_mgmt_service_rpc – Manages service-rpc objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_rpc_module.html#cp-mgmt-service-rpc-module)
- [cp_mgmt_service_rpc_facts – Get service-rpc objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_rpc_facts_module.html#cp-mgmt-service-rpc-facts-module)
- [cp_mgmt_service_sctp – Manages service-sctp objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_sctp_module.html#cp-mgmt-service-sctp-module)
- [cp_mgmt_service_sctp_facts – Get service-sctp objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_sctp_facts_module.html#cp-mgmt-service-sctp-facts-module)
- [cp_mgmt_service_tcp – Manages service-tcp objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_tcp_module.html#cp-mgmt-service-tcp-module)
- [cp_mgmt_service_tcp_facts – Get service-tcp objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_tcp_facts_module.html#cp-mgmt-service-tcp-facts-module)
- [cp_mgmt_service_udp – Manages service-udp objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_udp_module.html#cp-mgmt-service-udp-module)
- [cp_mgmt_service_udp_facts – Get service-udp objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_service_udp_facts_module.html#cp-mgmt-service-udp-facts-module)
- [cp_mgmt_session_facts – Get session objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_session_facts_module.html#cp-mgmt-session-facts-module)
- [cp_mgmt_simple_gateway – Manages simple-gateway objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_simple_gateway_module.html#cp-mgmt-simple-gateway-module)
- [cp_mgmt_simple_gateway_facts – Get simple-gateway objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_simple_gateway_facts_module.html#cp-mgmt-simple-gateway-facts-module)
- [cp_mgmt_tag – Manages tag objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_tag_module.html#cp-mgmt-tag-module)
- [cp_mgmt_tag_facts – Get tag objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_tag_facts_module.html#cp-mgmt-tag-facts-module)
- [cp_mgmt_threat_exception – Manages threat-exception objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_exception_module.html#cp-mgmt-threat-exception-module)
- [cp_mgmt_threat_exception_facts – Get threat-exception objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_exception_facts_module.html#cp-mgmt-threat-exception-facts-module)
- [cp_mgmt_threat_indicator – Manages threat-indicator objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_indicator_module.html#cp-mgmt-threat-indicator-module)
- [cp_mgmt_threat_indicator_facts – Get threat-indicator objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_indicator_facts_module.html#cp-mgmt-threat-indicator-facts-module)
- [cp_mgmt_threat_layer – Manages threat-layer objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_layer_module.html#cp-mgmt-threat-layer-module)
- [cp_mgmt_threat_layer_facts – Get threat-layer objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_layer_facts_module.html#cp-mgmt-threat-layer-facts-module)
- [cp_mgmt_threat_profile – Manages threat-profile objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_profile_module.html#cp-mgmt-threat-profile-module)
- [cp_mgmt_threat_profile_facts – Get threat-profile objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_profile_facts_module.html#cp-mgmt-threat-profile-facts-module)
- [cp_mgmt_threat_protection_override – Edit existing object using object name or uid](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_protection_override_module.html#cp-mgmt-threat-protection-override-module)
- [cp_mgmt_threat_rule – Manages threat-rule objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_rule_module.html#cp-mgmt-threat-rule-module)
- [cp_mgmt_threat_rule_facts – Get threat-rule objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_threat_rule_facts_module.html#cp-mgmt-threat-rule-facts-module)
- [cp_mgmt_time – Manages time objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_time_module.html#cp-mgmt-time-module)
- [cp_mgmt_time_facts – Get time objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_time_facts_module.html#cp-mgmt-time-facts-module)
- [cp_mgmt_verify_policy – Verifies the policy of the selected package](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_verify_policy_module.html#cp-mgmt-verify-policy-module)
- [cp_mgmt_vpn_community_meshed – Manages vpn-community-meshed objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_vpn_community_meshed_module.html#cp-mgmt-vpn-community-meshed-module)
- [cp_mgmt_vpn_community_meshed_facts – Get vpn-community-meshed objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_vpn_community_meshed_facts_module.html#cp-mgmt-vpn-community-meshed-facts-module)
- [cp_mgmt_vpn_community_star – Manages vpn-community-star objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_vpn_community_star_module.html#cp-mgmt-vpn-community-star-module)
- [cp_mgmt_vpn_community_star_facts – Get vpn-community-star objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_vpn_community_star_facts_module.html#cp-mgmt-vpn-community-star-facts-module)
- [cp_mgmt_wildcard – Manages wildcard objects on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_wildcard_module.html#cp-mgmt-wildcard-module)
- [cp_mgmt_wildcard_facts – Get wildcard objects facts on Check Point over Web Services API](https://docs.ansible.com/ansible/latest/modules/cp_mgmt_wildcard_facts_module.html#cp-mgmt-wildcard-facts-module)
- [cp_publish – All the changes done by this user will be seen by all users only after publish is called](https://docs.ansible.com/ansible/latest/modules/cp_publish_module.html#cp-publish-module)



### Cli

- [cli_command – Run a cli command on cli-based network devices](https://docs.ansible.com/ansible/latest/modules/cli_command_module.html#cli-command-module)
- [cli_config – Push text based configuration to network devices over network_cli](https://docs.ansible.com/ansible/latest/modules/cli_config_module.html#cli-config-module)



### Cloudengine

- [ce_aaa_server – Manages AAA server global configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_aaa_server_module.html#ce-aaa-server-module)
- [ce_aaa_server_host – Manages AAA server host configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_aaa_server_host_module.html#ce-aaa-server-host-module)
- [ce_acl – Manages base ACL configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_acl_module.html#ce-acl-module)
- [ce_acl_advance – Manages advanced ACL configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_acl_advance_module.html#ce-acl-advance-module)
- [ce_acl_interface – Manages applying ACLs to interfaces on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_acl_interface_module.html#ce-acl-interface-module)
- [ce_bfd_global – Manages BFD global configuration on HUAWEI CloudEngine devices](https://docs.ansible.com/ansible/latest/modules/ce_bfd_global_module.html#ce-bfd-global-module)
- [ce_bfd_session – Manages BFD session configuration on HUAWEI CloudEngine devices](https://docs.ansible.com/ansible/latest/modules/ce_bfd_session_module.html#ce-bfd-session-module)
- [ce_bfd_view – Manages BFD session view configuration on HUAWEI CloudEngine devices](https://docs.ansible.com/ansible/latest/modules/ce_bfd_view_module.html#ce-bfd-view-module)
- [ce_bgp – Manages BGP configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_bgp_module.html#ce-bgp-module)
- [ce_bgp_af – Manages BGP Address-family configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_bgp_af_module.html#ce-bgp-af-module)
- [ce_bgp_neighbor – Manages BGP peer configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_bgp_neighbor_module.html#ce-bgp-neighbor-module)
- [ce_bgp_neighbor_af – Manages BGP neighbor Address-family configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_bgp_neighbor_af_module.html#ce-bgp-neighbor-af-module)
- [ce_command – Run arbitrary command on HUAWEI CloudEngine devices](https://docs.ansible.com/ansible/latest/modules/ce_command_module.html#ce-command-module)
- [ce_config – Manage Huawei CloudEngine configuration sections](https://docs.ansible.com/ansible/latest/modules/ce_config_module.html#ce-config-module)
- [ce_dldp – Manages global DLDP configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_dldp_module.html#ce-dldp-module)
- [ce_dldp_interface – Manages interface DLDP configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_dldp_interface_module.html#ce-dldp-interface-module)
- [ce_eth_trunk – Manages Eth-Trunk interfaces on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_eth_trunk_module.html#ce-eth-trunk-module)
- [ce_evpn_bd_vni – Manages EVPN VXLAN Network Identifier (VNI) on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_evpn_bd_vni_module.html#ce-evpn-bd-vni-module)
- [ce_evpn_bgp – Manages BGP EVPN configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_evpn_bgp_module.html#ce-evpn-bgp-module)
- [ce_evpn_bgp_rr – Manages RR for the VXLAN Network on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_evpn_bgp_rr_module.html#ce-evpn-bgp-rr-module)
- [ce_evpn_global – Manages global configuration of EVPN on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_evpn_global_module.html#ce-evpn-global-module)
- [ce_facts – Gets facts about HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_facts_module.html#ce-facts-module)
- [ce_file_copy – Copy a file to a remote cloudengine device over SCP on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_file_copy_module.html#ce-file-copy-module)
- [ce_info_center_debug – Manages information center debug configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_info_center_debug_module.html#ce-info-center-debug-module)
- [ce_info_center_global – Manages outputting logs on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_info_center_global_module.html#ce-info-center-global-module)
- [ce_info_center_log – Manages information center log configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_info_center_log_module.html#ce-info-center-log-module)
- [ce_info_center_trap – Manages information center trap configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_info_center_trap_module.html#ce-info-center-trap-module)
- [ce_interface – Manages physical attributes of interfaces on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_interface_module.html#ce-interface-module)
- [ce_interface_ospf – Manages configuration of an OSPF interface instanceon HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_interface_ospf_module.html#ce-interface-ospf-module)
- [ce_ip_interface – Manages L3 attributes for IPv4 and IPv6 interfaces on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_ip_interface_module.html#ce-ip-interface-module)
- [ce_link_status – Get interface link status on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_link_status_module.html#ce-link-status-module)
- [ce_mlag_config – Manages MLAG configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_mlag_config_module.html#ce-mlag-config-module)
- [ce_mlag_interface – Manages MLAG interfaces on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_mlag_interface_module.html#ce-mlag-interface-module)
- [ce_mtu – Manages MTU settings on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_mtu_module.html#ce-mtu-module)
- [ce_netconf – Run an arbitrary netconf command on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_netconf_module.html#ce-netconf-module)
- [ce_netstream_aging – Manages timeout mode of NetStream on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_netstream_aging_module.html#ce-netstream-aging-module)
- [ce_netstream_export – Manages netstream export on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_netstream_export_module.html#ce-netstream-export-module)
- [ce_netstream_global – Manages global parameters of NetStream on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_netstream_global_module.html#ce-netstream-global-module)
- [ce_netstream_template – Manages NetStream template configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_netstream_template_module.html#ce-netstream-template-module)
- [ce_ntp – Manages core NTP configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_ntp_module.html#ce-ntp-module)
- [ce_ntp_auth – Manages NTP authentication configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_ntp_auth_module.html#ce-ntp-auth-module)
- [ce_ospf – Manages configuration of an OSPF instance on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_ospf_module.html#ce-ospf-module)
- [ce_ospf_vrf – Manages configuration of an OSPF VPN instance on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_ospf_vrf_module.html#ce-ospf-vrf-module)
- [ce_reboot – Reboot a HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_reboot_module.html#ce-reboot-module)
- [ce_rollback – Set a checkpoint or rollback to a checkpoint on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_rollback_module.html#ce-rollback-module)
- [ce_sflow – Manages sFlow configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_sflow_module.html#ce-sflow-module)
- [ce_snmp_community – Manages SNMP community configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_snmp_community_module.html#ce-snmp-community-module)
- [ce_snmp_contact – Manages SNMP contact configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_snmp_contact_module.html#ce-snmp-contact-module)
- [ce_snmp_location – Manages SNMP location configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_snmp_location_module.html#ce-snmp-location-module)
- [ce_snmp_target_host – Manages SNMP target host configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_snmp_target_host_module.html#ce-snmp-target-host-module)
- [ce_snmp_traps – Manages SNMP traps configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_snmp_traps_module.html#ce-snmp-traps-module)
- [ce_snmp_user – Manages SNMP user configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_snmp_user_module.html#ce-snmp-user-module)
- [ce_startup – Manages a system startup information on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_startup_module.html#ce-startup-module)
- [ce_static_route – Manages static route configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_static_route_module.html#ce-static-route-module)
- [ce_stp – Manages STP configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_stp_module.html#ce-stp-module)
- [ce_switchport – Manages Layer 2 switchport interfaces on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_switchport_module.html#ce-switchport-module)
- [ce_vlan – Manages VLAN resources and attributes on Huawei CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_vlan_module.html#ce-vlan-module)
- [ce_vrf – Manages VPN instance on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_vrf_module.html#ce-vrf-module)
- [ce_vrf_af – Manages VPN instance address family on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_vrf_af_module.html#ce-vrf-af-module)
- [ce_vrf_interface – Manages interface specific VPN configuration on HUAWEI CloudEngine switches](https://docs.ansible.com/ansible/latest/modules/ce_vrf_interface_module.html#ce-vrf-interface-module)
- [ce_vrrp – Manages VRRP interfaces on HUAWEI CloudEngine devices](https://docs.ansible.com/ansible/latest/modules/ce_vrrp_module.html#ce-vrrp-module)
- [ce_vxlan_arp – Manages ARP attributes of VXLAN on HUAWEI CloudEngine devices](https://docs.ansible.com/ansible/latest/modules/ce_vxlan_arp_module.html#ce-vxlan-arp-module)
- [ce_vxlan_gateway – Manages gateway for the VXLAN network on HUAWEI CloudEngine devices](https://docs.ansible.com/ansible/latest/modules/ce_vxlan_gateway_module.html#ce-vxlan-gateway-module)
- [ce_vxlan_global – Manages global attributes of VXLAN and bridge domain on HUAWEI CloudEngine devices](https://docs.ansible.com/ansible/latest/modules/ce_vxlan_global_module.html#ce-vxlan-global-module)
- [ce_vxlan_tunnel – Manages VXLAN tunnel configuration on HUAWEI CloudEngine devices](https://docs.ansible.com/ansible/latest/modules/ce_vxlan_tunnel_module.html#ce-vxlan-tunnel-module)
- [ce_vxlan_vap – Manages VXLAN virtual access point on HUAWEI CloudEngine Devices](https://docs.ansible.com/ansible/latest/modules/ce_vxlan_vap_module.html#ce-vxlan-vap-module)



### Cloudvision

- [cv_server_provision – Provision server port by applying or removing template configuration to an Arista CloudVision Portal configlet that is applied to a switch](https://docs.ansible.com/ansible/latest/modules/cv_server_provision_module.html#cv-server-provision-module)



### Cnos

- [cnos_backup – Backup the current running or startup configuration to a remote server on devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_backup_module.html#cnos-backup-module)
- [cnos_banner – Manage multiline banners on Lenovo CNOS devices](https://docs.ansible.com/ansible/latest/modules/cnos_banner_module.html#cnos-banner-module)
- [cnos_bgp – Manage BGP resources and attributes on devices running CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_bgp_module.html#cnos-bgp-module)
- [cnos_command – Run arbitrary commands on Lenovo CNOS devices](https://docs.ansible.com/ansible/latest/modules/cnos_command_module.html#cnos-command-module)
- [cnos_conditional_command – Execute a single command based on condition on devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_conditional_command_module.html#cnos-conditional-command-module)
- [cnos_conditional_template – Manage switch configuration using templates based on condition on devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_conditional_template_module.html#cnos-conditional-template-module)
- [cnos_config – Manage Lenovo CNOS configuration sections](https://docs.ansible.com/ansible/latest/modules/cnos_config_module.html#cnos-config-module)
- [cnos_factory – Reset the switch startup configuration to default (factory) on devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_factory_module.html#cnos-factory-module)
- [cnos_facts – Collect facts from remote devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_facts_module.html#cnos-facts-module)
- [cnos_image – Perform firmware upgrade/download from a remote server on devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_image_module.html#cnos-image-module)
- [cnos_interface – Manage Interface on Lenovo CNOS network devices](https://docs.ansible.com/ansible/latest/modules/cnos_interface_module.html#cnos-interface-module)
- [cnos_l2_interface – Manage Layer-2 interface on Lenovo CNOS devices](https://docs.ansible.com/ansible/latest/modules/cnos_l2_interface_module.html#cnos-l2-interface-module)
- [cnos_l3_interface – Manage Layer-3 interfaces on Lenovo CNOS network devices](https://docs.ansible.com/ansible/latest/modules/cnos_l3_interface_module.html#cnos-l3-interface-module)
- [cnos_linkagg – Manage link aggregation groups on Lenovo CNOS devices](https://docs.ansible.com/ansible/latest/modules/cnos_linkagg_module.html#cnos-linkagg-module)
- [cnos_lldp – Manage LLDP configuration on Lenovo CNOS network devices](https://docs.ansible.com/ansible/latest/modules/cnos_lldp_module.html#cnos-lldp-module)
- [cnos_logging – Manage logging on network devices](https://docs.ansible.com/ansible/latest/modules/cnos_logging_module.html#cnos-logging-module)
- [cnos_reload – Perform switch restart on devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_reload_module.html#cnos-reload-module)
- [cnos_rollback – Roll back the running or startup configuration from a remote server on devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_rollback_module.html#cnos-rollback-module)
- [cnos_save – Save the running configuration as the startup configuration on devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_save_module.html#cnos-save-module)
- [cnos_showrun – Collect the current running configuration on devices running on CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_showrun_module.html#cnos-showrun-module)
- [cnos_static_route – Manage static IP routes on Lenovo CNOS network devices](https://docs.ansible.com/ansible/latest/modules/cnos_static_route_module.html#cnos-static-route-module)
- [cnos_system – Manage the system attributes on Lenovo CNOS devices](https://docs.ansible.com/ansible/latest/modules/cnos_system_module.html#cnos-system-module)
- [cnos_template – Manage switch configuration using templates on devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_template_module.html#cnos-template-module)
- [cnos_user – Manage the collection of local users on Lenovo CNOS devices](https://docs.ansible.com/ansible/latest/modules/cnos_user_module.html#cnos-user-module)
- [cnos_vlag – Manage VLAG resources and attributes on devices running Lenovo CNOS](https://docs.ansible.com/ansible/latest/modules/cnos_vlag_module.html#cnos-vlag-module)
- [cnos_vlan – Manage VLANs on CNOS network devices](https://docs.ansible.com/ansible/latest/modules/cnos_vlan_module.html#cnos-vlan-module)
- [cnos_vrf – Manage VRFs on Lenovo CNOS network devices](https://docs.ansible.com/ansible/latest/modules/cnos_vrf_module.html#cnos-vrf-module)



### Cumulus

- [nclu – Configure network interfaces using NCLU](https://docs.ansible.com/ansible/latest/modules/nclu_module.html#nclu-module)



### Dellos10

- [dellos10_command – Run commands on remote devices running Dell OS10](https://docs.ansible.com/ansible/latest/modules/dellos10_command_module.html#dellos10-command-module)
- [dellos10_config – Manage Dell EMC Networking OS10 configuration sections](https://docs.ansible.com/ansible/latest/modules/dellos10_config_module.html#dellos10-config-module)
- [dellos10_facts – Collect facts from remote devices running Dell EMC Networking OS10](https://docs.ansible.com/ansible/latest/modules/dellos10_facts_module.html#dellos10-facts-module)



### Dellos6

- [dellos6_command – Run commands on remote devices running Dell OS6](https://docs.ansible.com/ansible/latest/modules/dellos6_command_module.html#dellos6-command-module)
- [dellos6_config – Manage Dell EMC Networking OS6 configuration sections](https://docs.ansible.com/ansible/latest/modules/dellos6_config_module.html#dellos6-config-module)
- [dellos6_facts – Collect facts from remote devices running Dell EMC Networking OS6](https://docs.ansible.com/ansible/latest/modules/dellos6_facts_module.html#dellos6-facts-module)



### Dellos9

- [dellos9_command – Run commands on remote devices running Dell OS9](https://docs.ansible.com/ansible/latest/modules/dellos9_command_module.html#dellos9-command-module)
- [dellos9_config – Manage Dell EMC Networking OS9 configuration sections](https://docs.ansible.com/ansible/latest/modules/dellos9_config_module.html#dellos9-config-module)
- [dellos9_facts – Collect facts from remote devices running Dell EMC Networking OS9](https://docs.ansible.com/ansible/latest/modules/dellos9_facts_module.html#dellos9-facts-module)



### Edgeos

- [edgeos_command – Run one or more commands on EdgeOS devices](https://docs.ansible.com/ansible/latest/modules/edgeos_command_module.html#edgeos-command-module)
- [edgeos_config – Manage EdgeOS configuration on remote device](https://docs.ansible.com/ansible/latest/modules/edgeos_config_module.html#edgeos-config-module)
- [edgeos_facts – Collect facts from remote devices running EdgeOS](https://docs.ansible.com/ansible/latest/modules/edgeos_facts_module.html#edgeos-facts-module)



### Edgeswitch

- [edgeswitch_facts – Collect facts from remote devices running Edgeswitch](https://docs.ansible.com/ansible/latest/modules/edgeswitch_facts_module.html#edgeswitch-facts-module)
- [edgeswitch_vlan – Manage VLANs on Ubiquiti Edgeswitch network devices](https://docs.ansible.com/ansible/latest/modules/edgeswitch_vlan_module.html#edgeswitch-vlan-module)



### Enos

- [enos_command – Run arbitrary commands on Lenovo ENOS devices](https://docs.ansible.com/ansible/latest/modules/enos_command_module.html#enos-command-module)
- [enos_config – Manage Lenovo ENOS configuration sections](https://docs.ansible.com/ansible/latest/modules/enos_config_module.html#enos-config-module)
- [enos_facts – Collect facts from remote devices running Lenovo ENOS](https://docs.ansible.com/ansible/latest/modules/enos_facts_module.html#enos-facts-module)



### Eos

- [eos_banner – Manage multiline banners on Arista EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_banner_module.html#eos-banner-module)
- [eos_bgp – Configure global BGP protocol settings on Arista EOS](https://docs.ansible.com/ansible/latest/modules/eos_bgp_module.html#eos-bgp-module)
- [eos_command – Run arbitrary commands on an Arista EOS device](https://docs.ansible.com/ansible/latest/modules/eos_command_module.html#eos-command-module)
- [eos_config – Manage Arista EOS configuration sections](https://docs.ansible.com/ansible/latest/modules/eos_config_module.html#eos-config-module)
- [eos_eapi – Manage and configure Arista EOS eAPI](https://docs.ansible.com/ansible/latest/modules/eos_eapi_module.html#eos-eapi-module)
- [eos_facts – Collect facts from remote devices running Arista EOS](https://docs.ansible.com/ansible/latest/modules/eos_facts_module.html#eos-facts-module)
- [eos_interface – Manage Interface on Arista EOS network devices](https://docs.ansible.com/ansible/latest/modules/eos_interface_module.html#eos-interface-module) **(D)**
- [eos_interfaces – Manages interface attributes of Arista EOS interfaces](https://docs.ansible.com/ansible/latest/modules/eos_interfaces_module.html#eos-interfaces-module)
- [eos_l2_interface – Manage L2 interfaces on Arista EOS network devices](https://docs.ansible.com/ansible/latest/modules/eos_l2_interface_module.html#eos-l2-interface-module) **(D)**
- [eos_l2_interfaces – Manages Layer-2 interface attributes of Arista EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_l2_interfaces_module.html#eos-l2-interfaces-module)
- [eos_l3_interface – Manage L3 interfaces on Arista EOS network devices](https://docs.ansible.com/ansible/latest/modules/eos_l3_interface_module.html#eos-l3-interface-module) **(D)**
- [eos_l3_interfaces – Manages L3 interface attributes of Arista EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_l3_interfaces_module.html#eos-l3-interfaces-module)
- [eos_lacp – Manage Global Link Aggregation Control Protocol (LACP) on Arista EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_lacp_module.html#eos-lacp-module)
- [eos_lacp_interfaces – Manage Link Aggregation Control Protocol (LACP) attributes of interfaces on Arista EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_lacp_interfaces_module.html#eos-lacp-interfaces-module)
- [eos_lag_interfaces – Manages link aggregation groups on Arista EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_lag_interfaces_module.html#eos-lag-interfaces-module)
- [eos_linkagg – Manage link aggregation groups on Arista EOS network devices](https://docs.ansible.com/ansible/latest/modules/eos_linkagg_module.html#eos-linkagg-module) **(D)**
- [eos_lldp – Manage LLDP configuration on Arista EOS network devices](https://docs.ansible.com/ansible/latest/modules/eos_lldp_module.html#eos-lldp-module)
- [eos_lldp_global – Manage Global Link Layer Discovery Protocol (LLDP) settings on Arista EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_lldp_global_module.html#eos-lldp-global-module)
- [eos_lldp_interfaces – Manage Link Layer Discovery Protocol (LLDP) attributes of interfaces on Arista EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_lldp_interfaces_module.html#eos-lldp-interfaces-module)
- [eos_logging – Manage logging on network devices](https://docs.ansible.com/ansible/latest/modules/eos_logging_module.html#eos-logging-module)
- [eos_static_route – Manage static IP routes on Arista EOS network devices](https://docs.ansible.com/ansible/latest/modules/eos_static_route_module.html#eos-static-route-module)
- [eos_system – Manage the system attributes on Arista EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_system_module.html#eos-system-module)
- [eos_user – Manage the collection of local users on EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_user_module.html#eos-user-module)
- [eos_vlan – Manage VLANs on Arista EOS network devices](https://docs.ansible.com/ansible/latest/modules/eos_vlan_module.html#eos-vlan-module) **(D)**
- [eos_vlans – Manage VLANs on Arista EOS devices](https://docs.ansible.com/ansible/latest/modules/eos_vlans_module.html#eos-vlans-module)
- [eos_vrf – Manage VRFs on Arista EOS network devices](https://docs.ansible.com/ansible/latest/modules/eos_vrf_module.html#eos-vrf-module)



### Eric_Eccli

- [eric_eccli_command – Run commands on remote devices running ERICSSON ECCLI](https://docs.ansible.com/ansible/latest/modules/eric_eccli_command_module.html#eric-eccli-command-module)



### Exos

- [exos_command – Run commands on remote devices running Extreme EXOS](https://docs.ansible.com/ansible/latest/modules/exos_command_module.html#exos-command-module)
- [exos_config – Manage Extreme Networks EXOS configuration sections](https://docs.ansible.com/ansible/latest/modules/exos_config_module.html#exos-config-module)
- [exos_facts – Collect facts from devices running Extreme EXOS](https://docs.ansible.com/ansible/latest/modules/exos_facts_module.html#exos-facts-module)
- [exos_lldp_global – Configure and manage Link Layer Discovery Protocol(LLDP) attributes on EXOS platforms](https://docs.ansible.com/ansible/latest/modules/exos_lldp_global_module.html#exos-lldp-global-module)



### F5

- [bigip_apm_acl – Manage user-defined APM ACLs](https://docs.ansible.com/ansible/latest/modules/bigip_apm_acl_module.html#bigip-apm-acl-module)
- [bigip_apm_network_access – Manage APM Network Access resource](https://docs.ansible.com/ansible/latest/modules/bigip_apm_network_access_module.html#bigip-apm-network-access-module)
- [bigip_apm_policy_fetch – Exports the APM policy or APM access profile from remote nodes](https://docs.ansible.com/ansible/latest/modules/bigip_apm_policy_fetch_module.html#bigip-apm-policy-fetch-module)
- [bigip_apm_policy_import – Manage BIG-IP APM policy or APM access profile imports](https://docs.ansible.com/ansible/latest/modules/bigip_apm_policy_import_module.html#bigip-apm-policy-import-module)
- [bigip_appsvcs_extension – Manage application service deployments](https://docs.ansible.com/ansible/latest/modules/bigip_appsvcs_extension_module.html#bigip-appsvcs-extension-module)
- [bigip_asm_dos_application – Manage application settings for DOS profile](https://docs.ansible.com/ansible/latest/modules/bigip_asm_dos_application_module.html#bigip-asm-dos-application-module)
- [bigip_asm_policy – Manage BIG-IP ASM policies](https://docs.ansible.com/ansible/latest/modules/bigip_asm_policy_module.html#bigip-asm-policy-module) **(D)**
- [bigip_asm_policy_fetch – Exports the asm policy from remote nodes](https://docs.ansible.com/ansible/latest/modules/bigip_asm_policy_fetch_module.html#bigip-asm-policy-fetch-module)
- [bigip_asm_policy_import – Manage BIG-IP ASM policy imports](https://docs.ansible.com/ansible/latest/modules/bigip_asm_policy_import_module.html#bigip-asm-policy-import-module)
- [bigip_asm_policy_manage – Manage BIG-IP ASM policies](https://docs.ansible.com/ansible/latest/modules/bigip_asm_policy_manage_module.html#bigip-asm-policy-manage-module)
- [bigip_asm_policy_server_technology – Manages Server Technology on ASM policy](https://docs.ansible.com/ansible/latest/modules/bigip_asm_policy_server_technology_module.html#bigip-asm-policy-server-technology-module)
- [bigip_asm_policy_signature_set – Manages Signature Sets on ASM policy](https://docs.ansible.com/ansible/latest/modules/bigip_asm_policy_signature_set_module.html#bigip-asm-policy-signature-set-module)
- [bigip_cli_alias – Manage CLI aliases on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_cli_alias_module.html#bigip-cli-alias-module)
- [bigip_cli_script – Manage CLI scripts on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_cli_script_module.html#bigip-cli-script-module)
- [bigip_command – Run TMSH and BASH commands on F5 devices](https://docs.ansible.com/ansible/latest/modules/bigip_command_module.html#bigip-command-module)
- [bigip_config – Manage BIG-IP configuration sections](https://docs.ansible.com/ansible/latest/modules/bigip_config_module.html#bigip-config-module)
- [bigip_configsync_action – Perform different actions related to config-sync](https://docs.ansible.com/ansible/latest/modules/bigip_configsync_action_module.html#bigip-configsync-action-module)
- [bigip_data_group – Manage data groups on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_data_group_module.html#bigip-data-group-module)
- [bigip_device_auth – Manage system authentication on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_device_auth_module.html#bigip-device-auth-module)
- [bigip_device_auth_ldap – Manage LDAP device authentication settings on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_device_auth_ldap_module.html#bigip-device-auth-ldap-module)
- [bigip_device_certificate – Manage self-signed device certificates](https://docs.ansible.com/ansible/latest/modules/bigip_device_certificate_module.html#bigip-device-certificate-module)
- [bigip_device_connectivity – Manages device IP configuration settings for HA on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_device_connectivity_module.html#bigip-device-connectivity-module)
- [bigip_device_dns – Manage BIG-IP device DNS settings](https://docs.ansible.com/ansible/latest/modules/bigip_device_dns_module.html#bigip-device-dns-module)
- [bigip_device_group – Manage device groups on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_device_group_module.html#bigip-device-group-module)
- [bigip_device_group_member – Manages members in a device group](https://docs.ansible.com/ansible/latest/modules/bigip_device_group_member_module.html#bigip-device-group-member-module)
- [bigip_device_ha_group – Manage HA group settings on a BIG-IP system](https://docs.ansible.com/ansible/latest/modules/bigip_device_ha_group_module.html#bigip-device-ha-group-module)
- [bigip_device_httpd – Manage HTTPD related settings on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_device_httpd_module.html#bigip-device-httpd-module)
- [bigip_device_info – Collect information from F5 BIG-IP devices](https://docs.ansible.com/ansible/latest/modules/bigip_device_info_module.html#bigip-device-info-module)
- [bigip_device_license – Manage license installation and activation on BIG-IP devices](https://docs.ansible.com/ansible/latest/modules/bigip_device_license_module.html#bigip-device-license-module)
- [bigip_device_ntp – Manage NTP servers on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_device_ntp_module.html#bigip-device-ntp-module)
- [bigip_device_sshd – Manage the SSHD settings of a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_device_sshd_module.html#bigip-device-sshd-module)
- [bigip_device_syslog – Manage system-level syslog settings on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_device_syslog_module.html#bigip-device-syslog-module)
- [bigip_device_traffic_group – Manages traffic groups on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_device_traffic_group_module.html#bigip-device-traffic-group-module)
- [bigip_device_trust – Manage the trust relationships between BIG-IPs](https://docs.ansible.com/ansible/latest/modules/bigip_device_trust_module.html#bigip-device-trust-module)
- [bigip_dns_cache_resolver – Manage DNS resolver cache configurations on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_dns_cache_resolver_module.html#bigip-dns-cache-resolver-module)
- [bigip_dns_nameserver – Manage LTM DNS nameservers on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_dns_nameserver_module.html#bigip-dns-nameserver-module)
- [bigip_dns_resolver – Manage DNS resolvers on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_dns_resolver_module.html#bigip-dns-resolver-module)
- [bigip_dns_zone – Manage DNS zones on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_dns_zone_module.html#bigip-dns-zone-module)
- [bigip_facts – Collect facts from F5 BIG-IP devices](https://docs.ansible.com/ansible/latest/modules/bigip_facts_module.html#bigip-facts-module) **(D)**
- [bigip_file_copy – Manage files in datastores on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_file_copy_module.html#bigip-file-copy-module)
- [bigip_firewall_address_list – Manage address lists on BIG-IP AFM](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_address_list_module.html#bigip-firewall-address-list-module)
- [bigip_firewall_dos_profile – Manage AFM DoS profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_dos_profile_module.html#bigip-firewall-dos-profile-module)
- [bigip_firewall_dos_vector – Manage attack vector configuration in an AFM DoS profile](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_dos_vector_module.html#bigip-firewall-dos-vector-module)
- [bigip_firewall_global_rules – Manage AFM global rule settings on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_global_rules_module.html#bigip-firewall-global-rules-module)
- [bigip_firewall_log_profile – Manages AFM logging profiles configured in the system](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_log_profile_module.html#bigip-firewall-log-profile-module)
- [bigip_firewall_log_profile_network – Configures Network Firewall related settings of the log profile](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_log_profile_network_module.html#bigip-firewall-log-profile-network-module)
- [bigip_firewall_policy – Manage AFM security firewall policies on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_policy_module.html#bigip-firewall-policy-module)
- [bigip_firewall_port_list – Manage port lists on BIG-IP AFM](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_port_list_module.html#bigip-firewall-port-list-module)
- [bigip_firewall_rule – Manage AFM Firewall rules](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_rule_module.html#bigip-firewall-rule-module)
- [bigip_firewall_rule_list – Manage AFM security firewall policies on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_rule_list_module.html#bigip-firewall-rule-list-module)
- [bigip_firewall_schedule – Manage BIG-IP AFM schedule configurations](https://docs.ansible.com/ansible/latest/modules/bigip_firewall_schedule_module.html#bigip-firewall-schedule-module)
- [bigip_gtm_datacenter – Manage Datacenter configuration in BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_datacenter_module.html#bigip-gtm-datacenter-module)
- [bigip_gtm_facts – Collect facts from F5 BIG-IP GTM devices](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_facts_module.html#bigip-gtm-facts-module) **(D)**
- [bigip_gtm_global – Manages global GTM settings](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_global_module.html#bigip-gtm-global-module)
- [bigip_gtm_monitor_bigip – Manages F5 BIG-IP GTM BIG-IP monitors](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_monitor_bigip_module.html#bigip-gtm-monitor-bigip-module)
- [bigip_gtm_monitor_external – Manages external GTM monitors on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_monitor_external_module.html#bigip-gtm-monitor-external-module)
- [bigip_gtm_monitor_firepass – Manages F5 BIG-IP GTM FirePass monitors](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_monitor_firepass_module.html#bigip-gtm-monitor-firepass-module)
- [bigip_gtm_monitor_http – Manages F5 BIG-IP GTM http monitors](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_monitor_http_module.html#bigip-gtm-monitor-http-module)
- [bigip_gtm_monitor_https – Manages F5 BIG-IP GTM https monitors](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_monitor_https_module.html#bigip-gtm-monitor-https-module)
- [bigip_gtm_monitor_tcp – Manages F5 BIG-IP GTM tcp monitors](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_monitor_tcp_module.html#bigip-gtm-monitor-tcp-module)
- [bigip_gtm_monitor_tcp_half_open – Manages F5 BIG-IP GTM tcp half-open monitors](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_monitor_tcp_half_open_module.html#bigip-gtm-monitor-tcp-half-open-module)
- [bigip_gtm_pool – Manages F5 BIG-IP GTM pools](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_pool_module.html#bigip-gtm-pool-module)
- [bigip_gtm_pool_member – Manage GTM pool member settings](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_pool_member_module.html#bigip-gtm-pool-member-module)
- [bigip_gtm_server – Manages F5 BIG-IP GTM servers](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_server_module.html#bigip-gtm-server-module)
- [bigip_gtm_topology_record – Manages GTM Topology Records](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_topology_record_module.html#bigip-gtm-topology-record-module)
- [bigip_gtm_topology_region – Manages GTM Topology Regions](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_topology_region_module.html#bigip-gtm-topology-region-module)
- [bigip_gtm_virtual_server – Manages F5 BIG-IP GTM virtual servers](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_virtual_server_module.html#bigip-gtm-virtual-server-module)
- [bigip_gtm_wide_ip – Manages F5 BIG-IP GTM wide ip](https://docs.ansible.com/ansible/latest/modules/bigip_gtm_wide_ip_module.html#bigip-gtm-wide-ip-module)
- [bigip_hostname – Manage the hostname of a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_hostname_module.html#bigip-hostname-module)
- [bigip_iapp_service – Manages TCL iApp services on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_iapp_service_module.html#bigip-iapp-service-module)
- [bigip_iapp_template – Manages TCL iApp templates on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_iapp_template_module.html#bigip-iapp-template-module)
- [bigip_ike_peer – Manage IPSec IKE Peer configuration on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_ike_peer_module.html#bigip-ike-peer-module)
- [bigip_imish_config – Manage BIG-IP advanced routing configuration sections](https://docs.ansible.com/ansible/latest/modules/bigip_imish_config_module.html#bigip-imish-config-module)
- [bigip_ipsec_policy – Manage IPSec policies on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_ipsec_policy_module.html#bigip-ipsec-policy-module)
- [bigip_irule – Manage iRules across different modules on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_irule_module.html#bigip-irule-module)
- [bigip_log_destination – Manages log destinations on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_log_destination_module.html#bigip-log-destination-module)
- [bigip_log_publisher – Manages log publishers on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_log_publisher_module.html#bigip-log-publisher-module)
- [bigip_lx_package – Manages Javascript LX packages on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_lx_package_module.html#bigip-lx-package-module)
- [bigip_management_route – Manage system management routes on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_management_route_module.html#bigip-management-route-module)
- [bigip_message_routing_peer – Manage peers for routing generic message protocol messages](https://docs.ansible.com/ansible/latest/modules/bigip_message_routing_peer_module.html#bigip-message-routing-peer-module)
- [bigip_message_routing_protocol – Manage generic message parser profile](https://docs.ansible.com/ansible/latest/modules/bigip_message_routing_protocol_module.html#bigip-message-routing-protocol-module)
- [bigip_message_routing_route – Manages static routes for routing message protocol messages](https://docs.ansible.com/ansible/latest/modules/bigip_message_routing_route_module.html#bigip-message-routing-route-module)
- [bigip_message_routing_router – Manages router profiles for message-routing protocols](https://docs.ansible.com/ansible/latest/modules/bigip_message_routing_router_module.html#bigip-message-routing-router-module)
- [bigip_message_routing_transport_config – Manages configuration for an outgoing connection](https://docs.ansible.com/ansible/latest/modules/bigip_message_routing_transport_config_module.html#bigip-message-routing-transport-config-module)
- [bigip_monitor_dns – Manage DNS monitors on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_dns_module.html#bigip-monitor-dns-module)
- [bigip_monitor_external – Manages external LTM monitors on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_external_module.html#bigip-monitor-external-module)
- [bigip_monitor_gateway_icmp – Manages F5 BIG-IP LTM gateway ICMP monitors](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_gateway_icmp_module.html#bigip-monitor-gateway-icmp-module)
- [bigip_monitor_http – Manages F5 BIG-IP LTM http monitors](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_http_module.html#bigip-monitor-http-module)
- [bigip_monitor_https – Manages F5 BIG-IP LTM https monitors](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_https_module.html#bigip-monitor-https-module)
- [bigip_monitor_ldap – Manages BIG-IP LDAP monitors](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_ldap_module.html#bigip-monitor-ldap-module)
- [bigip_monitor_snmp_dca – Manages BIG-IP SNMP data collecting agent (DCA) monitors](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_snmp_dca_module.html#bigip-monitor-snmp-dca-module)
- [bigip_monitor_tcp – Manages F5 BIG-IP LTM tcp monitors](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_tcp_module.html#bigip-monitor-tcp-module)
- [bigip_monitor_tcp_echo – Manages F5 BIG-IP LTM tcp echo monitors](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_tcp_echo_module.html#bigip-monitor-tcp-echo-module)
- [bigip_monitor_tcp_half_open – Manages F5 BIG-IP LTM tcp half-open monitors](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_tcp_half_open_module.html#bigip-monitor-tcp-half-open-module)
- [bigip_monitor_udp – Manages F5 BIG-IP LTM udp monitors](https://docs.ansible.com/ansible/latest/modules/bigip_monitor_udp_module.html#bigip-monitor-udp-module)
- [bigip_node – Manages F5 BIG-IP LTM nodes](https://docs.ansible.com/ansible/latest/modules/bigip_node_module.html#bigip-node-module)
- [bigip_partition – Manage BIG-IP partitions](https://docs.ansible.com/ansible/latest/modules/bigip_partition_module.html#bigip-partition-module)
- [bigip_password_policy – Manages the authentication password policy on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_password_policy_module.html#bigip-password-policy-module)
- [bigip_policy – Manage general policy configuration on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_policy_module.html#bigip-policy-module)
- [bigip_policy_rule – Manage LTM policy rules on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_policy_rule_module.html#bigip-policy-rule-module)
- [bigip_pool – Manages F5 BIG-IP LTM pools](https://docs.ansible.com/ansible/latest/modules/bigip_pool_module.html#bigip-pool-module)
- [bigip_pool_member – Manages F5 BIG-IP LTM pool members](https://docs.ansible.com/ansible/latest/modules/bigip_pool_member_module.html#bigip-pool-member-module)
- [bigip_profile_analytics – Manage HTTP analytics profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_analytics_module.html#bigip-profile-analytics-module)
- [bigip_profile_client_ssl – Manages client SSL profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_client_ssl_module.html#bigip-profile-client-ssl-module)
- [bigip_profile_dns – Manage DNS profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_dns_module.html#bigip-profile-dns-module)
- [bigip_profile_fastl4 – Manages Fast L4 profiles](https://docs.ansible.com/ansible/latest/modules/bigip_profile_fastl4_module.html#bigip-profile-fastl4-module)
- [bigip_profile_http – Manage HTTP profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_http_module.html#bigip-profile-http-module)
- [bigip_profile_http2 – Manage HTTP2 profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_http2_module.html#bigip-profile-http2-module)
- [bigip_profile_http_compression – Manage HTTP compression profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_http_compression_module.html#bigip-profile-http-compression-module)
- [bigip_profile_oneconnect – Manage OneConnect profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_oneconnect_module.html#bigip-profile-oneconnect-module)
- [bigip_profile_persistence_cookie – Manage cookie persistence profiles on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_persistence_cookie_module.html#bigip-profile-persistence-cookie-module)
- [bigip_profile_persistence_src_addr – Manage source address persistence profiles](https://docs.ansible.com/ansible/latest/modules/bigip_profile_persistence_src_addr_module.html#bigip-profile-persistence-src-addr-module)
- [bigip_profile_server_ssl – Manages server SSL profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_server_ssl_module.html#bigip-profile-server-ssl-module)
- [bigip_profile_tcp – Manage TCP profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_tcp_module.html#bigip-profile-tcp-module)
- [bigip_profile_udp – Manage UDP profiles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_profile_udp_module.html#bigip-profile-udp-module)
- [bigip_provision – Manage BIG-IP module provisioning](https://docs.ansible.com/ansible/latest/modules/bigip_provision_module.html#bigip-provision-module)
- [bigip_qkview – Manage qkviews on the device](https://docs.ansible.com/ansible/latest/modules/bigip_qkview_module.html#bigip-qkview-module)
- [bigip_remote_role – Manage remote roles on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_remote_role_module.html#bigip-remote-role-module)
- [bigip_remote_syslog – Manipulate remote syslog settings on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_remote_syslog_module.html#bigip-remote-syslog-module)
- [bigip_remote_user – Manages default settings for remote user accounts on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_remote_user_module.html#bigip-remote-user-module)
- [bigip_routedomain – Manage route domains on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_routedomain_module.html#bigip-routedomain-module)
- [bigip_selfip – Manage Self-IPs on a BIG-IP system](https://docs.ansible.com/ansible/latest/modules/bigip_selfip_module.html#bigip-selfip-module)
- [bigip_service_policy – Manages service policies on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_service_policy_module.html#bigip-service-policy-module)
- [bigip_smtp – Manages SMTP settings on the BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_smtp_module.html#bigip-smtp-module)
- [bigip_snat_pool – Manage SNAT pools on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_snat_pool_module.html#bigip-snat-pool-module)
- [bigip_snat_translation – Manage SNAT Translations on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_snat_translation_module.html#bigip-snat-translation-module)
- [bigip_snmp – Manipulate general SNMP settings on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_snmp_module.html#bigip-snmp-module)
- [bigip_snmp_community – Manages SNMP communities on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_snmp_community_module.html#bigip-snmp-community-module)
- [bigip_snmp_trap – Manipulate SNMP trap information on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_snmp_trap_module.html#bigip-snmp-trap-module)
- [bigip_software_image – Manage software images on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_software_image_module.html#bigip-software-image-module)
- [bigip_software_install – Install software images on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_software_install_module.html#bigip-software-install-module)
- [bigip_software_update – Manage the software update settings of a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_software_update_module.html#bigip-software-update-module)
- [bigip_ssl_certificate – Import/Delete certificates from BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_ssl_certificate_module.html#bigip-ssl-certificate-module)
- [bigip_ssl_key – Import/Delete SSL keys from BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_ssl_key_module.html#bigip-ssl-key-module)
- [bigip_ssl_ocsp – Manage OCSP configurations on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_ssl_ocsp_module.html#bigip-ssl-ocsp-module)
- [bigip_static_route – Manipulate static routes on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_static_route_module.html#bigip-static-route-module)
- [bigip_sys_daemon_log_tmm – Manage BIG-IP tmm daemon log settings](https://docs.ansible.com/ansible/latest/modules/bigip_sys_daemon_log_tmm_module.html#bigip-sys-daemon-log-tmm-module)
- [bigip_sys_db – Manage BIG-IP system database variables](https://docs.ansible.com/ansible/latest/modules/bigip_sys_db_module.html#bigip-sys-db-module)
- [bigip_sys_global – Manage BIG-IP global settings](https://docs.ansible.com/ansible/latest/modules/bigip_sys_global_module.html#bigip-sys-global-module)
- [bigip_timer_policy – Manage timer policies on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_timer_policy_module.html#bigip-timer-policy-module)
- [bigip_traffic_selector – Manage IPSec Traffic Selectors on BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_traffic_selector_module.html#bigip-traffic-selector-module)
- [bigip_trunk – Manage trunks on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_trunk_module.html#bigip-trunk-module)
- [bigip_tunnel – Manage tunnels on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_tunnel_module.html#bigip-tunnel-module)
- [bigip_ucs – Manage upload, installation and removal of UCS files](https://docs.ansible.com/ansible/latest/modules/bigip_ucs_module.html#bigip-ucs-module)
- [bigip_ucs_fetch – Fetches a UCS file from remote nodes](https://docs.ansible.com/ansible/latest/modules/bigip_ucs_fetch_module.html#bigip-ucs-fetch-module)
- [bigip_user – Manage user accounts and user attributes on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_user_module.html#bigip-user-module)
- [bigip_vcmp_guest – Manages vCMP guests on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_vcmp_guest_module.html#bigip-vcmp-guest-module)
- [bigip_virtual_address – Manage LTM virtual addresses on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_virtual_address_module.html#bigip-virtual-address-module)
- [bigip_virtual_server – Manage LTM virtual servers on a BIG-IP](https://docs.ansible.com/ansible/latest/modules/bigip_virtual_server_module.html#bigip-virtual-server-module)
- [bigip_vlan – Manage VLANs on a BIG-IP system](https://docs.ansible.com/ansible/latest/modules/bigip_vlan_module.html#bigip-vlan-module)
- [bigip_wait – Wait for a BIG-IP condition before continuing](https://docs.ansible.com/ansible/latest/modules/bigip_wait_module.html#bigip-wait-module)
- [bigiq_application_fasthttp – Manages BIG-IQ FastHTTP applications](https://docs.ansible.com/ansible/latest/modules/bigiq_application_fasthttp_module.html#bigiq-application-fasthttp-module)
- [bigiq_application_fastl4_tcp – Manages BIG-IQ FastL4 TCP applications](https://docs.ansible.com/ansible/latest/modules/bigiq_application_fastl4_tcp_module.html#bigiq-application-fastl4-tcp-module)
- [bigiq_application_fastl4_udp – Manages BIG-IQ FastL4 UDP applications](https://docs.ansible.com/ansible/latest/modules/bigiq_application_fastl4_udp_module.html#bigiq-application-fastl4-udp-module)
- [bigiq_application_http – Manages BIG-IQ HTTP applications](https://docs.ansible.com/ansible/latest/modules/bigiq_application_http_module.html#bigiq-application-http-module)
- [bigiq_application_https_offload – Manages BIG-IQ HTTPS offload applications](https://docs.ansible.com/ansible/latest/modules/bigiq_application_https_offload_module.html#bigiq-application-https-offload-module)
- [bigiq_application_https_waf – Manages BIG-IQ HTTPS WAF applications](https://docs.ansible.com/ansible/latest/modules/bigiq_application_https_waf_module.html#bigiq-application-https-waf-module)
- [bigiq_device_discovery – Manage BIG-IP devices through BIG-IQ](https://docs.ansible.com/ansible/latest/modules/bigiq_device_discovery_module.html#bigiq-device-discovery-module)
- [bigiq_device_info – Collect information from F5 BIG-IQ devices](https://docs.ansible.com/ansible/latest/modules/bigiq_device_info_module.html#bigiq-device-info-module)
- [bigiq_regkey_license – Manages licenses in a BIG-IQ registration key pool](https://docs.ansible.com/ansible/latest/modules/bigiq_regkey_license_module.html#bigiq-regkey-license-module)
- [bigiq_regkey_license_assignment – Manage regkey license assignment on BIG-IPs from a BIG-IQ](https://docs.ansible.com/ansible/latest/modules/bigiq_regkey_license_assignment_module.html#bigiq-regkey-license-assignment-module)
- [bigiq_regkey_pool – Manages registration key pools on BIG-IQ](https://docs.ansible.com/ansible/latest/modules/bigiq_regkey_pool_module.html#bigiq-regkey-pool-module)
- [bigiq_utility_license – Manage utility licenses on a BIG-IQ](https://docs.ansible.com/ansible/latest/modules/bigiq_utility_license_module.html#bigiq-utility-license-module)
- [bigiq_utility_license_assignment – Manage utility license assignment on BIG-IPs from a BIG-IQ](https://docs.ansible.com/ansible/latest/modules/bigiq_utility_license_assignment_module.html#bigiq-utility-license-assignment-module)



### Files

- [net_get – Copy a file from a network device to Ansible Controller](https://docs.ansible.com/ansible/latest/modules/net_get_module.html#net-get-module)
- [net_put – Copy a file from Ansible Controller to a network device](https://docs.ansible.com/ansible/latest/modules/net_put_module.html#net-put-module)



### Fortianalyzer

- [faz_device – Add or remove device](https://docs.ansible.com/ansible/latest/modules/faz_device_module.html#faz-device-module)



### Fortimanager

- [fmgr_device – Add or remove device from FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_device_module.html#fmgr-device-module)
- [fmgr_device_config – Edit device configurations](https://docs.ansible.com/ansible/latest/modules/fmgr_device_config_module.html#fmgr-device-config-module)
- [fmgr_device_group – Alter FortiManager device groups](https://docs.ansible.com/ansible/latest/modules/fmgr_device_group_module.html#fmgr-device-group-module)
- [fmgr_device_provision_template – Manages Device Provisioning Templates in FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_device_provision_template_module.html#fmgr-device-provision-template-module)
- [fmgr_fwobj_address – Allows the management of firewall objects in FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_fwobj_address_module.html#fmgr-fwobj-address-module)
- [fmgr_fwobj_ippool – Allows the editing of IP Pool Objects within FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_fwobj_ippool_module.html#fmgr-fwobj-ippool-module)
- [fmgr_fwobj_ippool6 – Allows the editing of IP Pool Objects within FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_fwobj_ippool6_module.html#fmgr-fwobj-ippool6-module)
- [fmgr_fwobj_service – Manages FortiManager Firewall Service Objects](https://docs.ansible.com/ansible/latest/modules/fmgr_fwobj_service_module.html#fmgr-fwobj-service-module)
- [fmgr_fwobj_vip – Manages Virtual IPs objects in FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_fwobj_vip_module.html#fmgr-fwobj-vip-module)
- [fmgr_fwpol_ipv4 – Allows the add/delete of Firewall Policies on Packages in FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_fwpol_ipv4_module.html#fmgr-fwpol-ipv4-module)
- [fmgr_fwpol_package – Manages FortiManager Firewall Policies Packages](https://docs.ansible.com/ansible/latest/modules/fmgr_fwpol_package_module.html#fmgr-fwpol-package-module)
- [fmgr_ha – Manages the High-Availability State of FortiManager Clusters and Nodes](https://docs.ansible.com/ansible/latest/modules/fmgr_ha_module.html#fmgr-ha-module)
- [fmgr_provisioning – Provision devices via FortiMananger](https://docs.ansible.com/ansible/latest/modules/fmgr_provisioning_module.html#fmgr-provisioning-module)
- [fmgr_query – Query FortiManager data objects for use in Ansible workflows](https://docs.ansible.com/ansible/latest/modules/fmgr_query_module.html#fmgr-query-module)
- [fmgr_script – Add/Edit/Delete and execute scripts](https://docs.ansible.com/ansible/latest/modules/fmgr_script_module.html#fmgr-script-module)
- [fmgr_secprof_appctrl – Manage application control security profiles](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_appctrl_module.html#fmgr-secprof-appctrl-module)
- [fmgr_secprof_av – Manage security profile](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_av_module.html#fmgr-secprof-av-module)
- [fmgr_secprof_dns – Manage DNS security profiles in FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_dns_module.html#fmgr-secprof-dns-module)
- [fmgr_secprof_ips – Managing IPS security profiles in FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_ips_module.html#fmgr-secprof-ips-module)
- [fmgr_secprof_profile_group – Manage security profiles within FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_profile_group_module.html#fmgr-secprof-profile-group-module)
- [fmgr_secprof_proxy – Manage proxy security profiles in FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_proxy_module.html#fmgr-secprof-proxy-module)
- [fmgr_secprof_spam – spam filter profile for FMG](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_spam_module.html#fmgr-secprof-spam-module)
- [fmgr_secprof_ssl_ssh – Manage SSL and SSH security profiles in FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_ssl_ssh_module.html#fmgr-secprof-ssl-ssh-module)
- [fmgr_secprof_voip – VOIP security profiles in FMG](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_voip_module.html#fmgr-secprof-voip-module)
- [fmgr_secprof_waf – FortiManager web application firewall security profile](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_waf_module.html#fmgr-secprof-waf-module)
- [fmgr_secprof_wanopt – WAN optimization](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_wanopt_module.html#fmgr-secprof-wanopt-module)
- [fmgr_secprof_web – Manage web filter security profiles in FortiManager](https://docs.ansible.com/ansible/latest/modules/fmgr_secprof_web_module.html#fmgr-secprof-web-module)



### Fortios

- [fortios_address – Manage fortios firewall address objects](https://docs.ansible.com/ansible/latest/modules/fortios_address_module.html#fortios-address-module)
- [fortios_alertemail_setting – Configure alert email settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_alertemail_setting_module.html#fortios-alertemail-setting-module)
- [fortios_antivirus_heuristic – Configure global heuristic options in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_antivirus_heuristic_module.html#fortios-antivirus-heuristic-module)
- [fortios_antivirus_profile – Configure AntiVirus profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_antivirus_profile_module.html#fortios-antivirus-profile-module)
- [fortios_antivirus_quarantine – Configure quarantine options in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_antivirus_quarantine_module.html#fortios-antivirus-quarantine-module)
- [fortios_antivirus_settings – Configure AntiVirus settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_antivirus_settings_module.html#fortios-antivirus-settings-module)
- [fortios_application_custom – Configure custom application signatures in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_application_custom_module.html#fortios-application-custom-module)
- [fortios_application_group – Configure firewall application groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_application_group_module.html#fortios-application-group-module)
- [fortios_application_list – Configure application control lists in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_application_list_module.html#fortios-application-list-module)
- [fortios_application_name – Configure application signatures in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_application_name_module.html#fortios-application-name-module)
- [fortios_application_rule_settings – Configure application rule settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_application_rule_settings_module.html#fortios-application-rule-settings-module)
- [fortios_authentication_rule – Configure Authentication Rules in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_authentication_rule_module.html#fortios-authentication-rule-module)
- [fortios_authentication_scheme – Configure Authentication Schemes in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_authentication_scheme_module.html#fortios-authentication-scheme-module)
- [fortios_authentication_setting – Configure authentication setting in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_authentication_setting_module.html#fortios-authentication-setting-module)
- [fortios_config – Manage config on Fortinet FortiOS firewall devices](https://docs.ansible.com/ansible/latest/modules/fortios_config_module.html#fortios-config-module)
- [fortios_dlp_filepattern – Configure file patterns used by DLP blocking in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_dlp_filepattern_module.html#fortios-dlp-filepattern-module)
- [fortios_dlp_fp_doc_source – Create a DLP fingerprint database by allowing the FortiGate to access a file server containing files from which to create fingerprints in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_dlp_fp_doc_source_module.html#fortios-dlp-fp-doc-source-module)
- [fortios_dlp_fp_sensitivity – Create self-explanatory DLP sensitivity levels to be used when setting sensitivity under config fp-doc-source in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_dlp_fp_sensitivity_module.html#fortios-dlp-fp-sensitivity-module)
- [fortios_dlp_sensor – Configure DLP sensors in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_dlp_sensor_module.html#fortios-dlp-sensor-module)
- [fortios_dlp_settings – Designate logical storage for DLP fingerprint database in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_dlp_settings_module.html#fortios-dlp-settings-module)
- [fortios_dnsfilter_domain_filter – Configure DNS domain filters in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_dnsfilter_domain_filter_module.html#fortios-dnsfilter-domain-filter-module)
- [fortios_dnsfilter_profile – Configure DNS domain filter profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_dnsfilter_profile_module.html#fortios-dnsfilter-profile-module)
- [fortios_endpoint_control_client – Configure endpoint control client lists in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_endpoint_control_client_module.html#fortios-endpoint-control-client-module)
- [fortios_endpoint_control_forticlient_ems – Configure FortiClient Enterprise Management Server (EMS) entries in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_endpoint_control_forticlient_ems_module.html#fortios-endpoint-control-forticlient-ems-module)
- [fortios_endpoint_control_forticlient_registration_sync – Configure FortiClient registration synchronization settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_endpoint_control_forticlient_registration_sync_module.html#fortios-endpoint-control-forticlient-registration-sync-module)
- [fortios_endpoint_control_profile – Configure FortiClient endpoint control profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_endpoint_control_profile_module.html#fortios-endpoint-control-profile-module)
- [fortios_endpoint_control_settings – Configure endpoint control settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_endpoint_control_settings_module.html#fortios-endpoint-control-settings-module)
- [fortios_extender_controller_extender – Extender controller configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_extender_controller_extender_module.html#fortios-extender-controller-extender-module)
- [fortios_facts – Get facts about fortios devices](https://docs.ansible.com/ansible/latest/modules/fortios_facts_module.html#fortios-facts-module)
- [fortios_firewall_address – Configure IPv4 addresses in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_address_module.html#fortios-firewall-address-module)
- [fortios_firewall_address6 – Configure IPv6 firewall addresses in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_address6_module.html#fortios-firewall-address6-module)
- [fortios_firewall_address6_template – Configure IPv6 address templates in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_address6_template_module.html#fortios-firewall-address6-template-module)
- [fortios_firewall_addrgrp – Configure IPv4 address groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_addrgrp_module.html#fortios-firewall-addrgrp-module)
- [fortios_firewall_addrgrp6 – Configure IPv6 address groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_addrgrp6_module.html#fortios-firewall-addrgrp6-module)
- [fortios_firewall_auth_portal – Configure firewall authentication portals in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_auth_portal_module.html#fortios-firewall-auth-portal-module)
- [fortios_firewall_central_snat_map – Configure central SNAT policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_central_snat_map_module.html#fortios-firewall-central-snat-map-module)
- [fortios_firewall_dnstranslation – Configure DNS translation in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_dnstranslation_module.html#fortios-firewall-dnstranslation-module)
- [fortios_firewall_DoS_policy – Configure IPv4 DoS policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_DoS_policy_module.html#fortios-firewall-dos-policy-module)
- [fortios_firewall_DoS_policy6 – Configure IPv6 DoS policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_DoS_policy6_module.html#fortios-firewall-dos-policy6-module)
- [fortios_firewall_identity_based_route – Configure identity based routing in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_identity_based_route_module.html#fortios-firewall-identity-based-route-module)
- [fortios_firewall_interface_policy – Configure IPv4 interface policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_interface_policy_module.html#fortios-firewall-interface-policy-module)
- [fortios_firewall_interface_policy6 – Configure IPv6 interface policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_interface_policy6_module.html#fortios-firewall-interface-policy6-module)
- [fortios_firewall_internet_service – Show Internet Service application in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_internet_service_module.html#fortios-firewall-internet-service-module)
- [fortios_firewall_internet_service_custom – Configure custom Internet Services in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_internet_service_custom_module.html#fortios-firewall-internet-service-custom-module)
- [fortios_firewall_internet_service_group – Configure group of Internet Service in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_internet_service_group_module.html#fortios-firewall-internet-service-group-module)
- [fortios_firewall_ip_translation – Configure firewall IP-translation in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ip_translation_module.html#fortios-firewall-ip-translation-module)
- [fortios_firewall_ipmacbinding_setting – Configure IP to MAC binding settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ipmacbinding_setting_module.html#fortios-firewall-ipmacbinding-setting-module)
- [fortios_firewall_ipmacbinding_table – Configure IP to MAC address pairs in the IP/MAC binding table in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ipmacbinding_table_module.html#fortios-firewall-ipmacbinding-table-module)
- [fortios_firewall_ippool – Configure IPv4 IP pools in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ippool_module.html#fortios-firewall-ippool-module)
- [fortios_firewall_ippool6 – Configure IPv6 IP pools in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ippool6_module.html#fortios-firewall-ippool6-module)
- [fortios_firewall_ipv6_eh_filter – Configure IPv6 extension header filter in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ipv6_eh_filter_module.html#fortios-firewall-ipv6-eh-filter-module)
- [fortios_firewall_ldb_monitor – Configure server load balancing health monitors in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ldb_monitor_module.html#fortios-firewall-ldb-monitor-module)
- [fortios_firewall_local_in_policy – Configure user defined IPv4 local-in policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_local_in_policy_module.html#fortios-firewall-local-in-policy-module)
- [fortios_firewall_local_in_policy6 – Configure user defined IPv6 local-in policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_local_in_policy6_module.html#fortios-firewall-local-in-policy6-module)
- [fortios_firewall_multicast_address – Configure multicast addresses in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_multicast_address_module.html#fortios-firewall-multicast-address-module)
- [fortios_firewall_multicast_address6 – Configure IPv6 multicast address in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_multicast_address6_module.html#fortios-firewall-multicast-address6-module)
- [fortios_firewall_multicast_policy – Configure multicast NAT policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_multicast_policy_module.html#fortios-firewall-multicast-policy-module)
- [fortios_firewall_multicast_policy6 – Configure IPv6 multicast NAT policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_multicast_policy6_module.html#fortios-firewall-multicast-policy6-module)
- [fortios_firewall_policy – Configure IPv4 policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_policy_module.html#fortios-firewall-policy-module)
- [fortios_firewall_policy46 – Configure IPv4 to IPv6 policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_policy46_module.html#fortios-firewall-policy46-module)
- [fortios_firewall_policy6 – Configure IPv6 policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_policy6_module.html#fortios-firewall-policy6-module)
- [fortios_firewall_policy64 – Configure IPv6 to IPv4 policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_policy64_module.html#fortios-firewall-policy64-module)
- [fortios_firewall_profile_group – Configure profile groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_profile_group_module.html#fortios-firewall-profile-group-module)
- [fortios_firewall_profile_protocol_options – Configure protocol options in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_profile_protocol_options_module.html#fortios-firewall-profile-protocol-options-module)
- [fortios_firewall_proxy_address – Web proxy address configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_proxy_address_module.html#fortios-firewall-proxy-address-module)
- [fortios_firewall_proxy_addrgrp – Web proxy address group configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_proxy_addrgrp_module.html#fortios-firewall-proxy-addrgrp-module)
- [fortios_firewall_proxy_policy – Configure proxy policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_proxy_policy_module.html#fortios-firewall-proxy-policy-module)
- [fortios_firewall_schedule_group – Schedule group configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_schedule_group_module.html#fortios-firewall-schedule-group-module)
- [fortios_firewall_schedule_onetime – Onetime schedule configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_schedule_onetime_module.html#fortios-firewall-schedule-onetime-module)
- [fortios_firewall_schedule_recurring – Recurring schedule configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_schedule_recurring_module.html#fortios-firewall-schedule-recurring-module)
- [fortios_firewall_service_category – Configure service categories in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_service_category_module.html#fortios-firewall-service-category-module)
- [fortios_firewall_service_custom – Configure custom services in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_service_custom_module.html#fortios-firewall-service-custom-module)
- [fortios_firewall_service_group – Configure service groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_service_group_module.html#fortios-firewall-service-group-module)
- [fortios_firewall_shaper_per_ip_shaper – Configure per-IP traffic shaper in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_shaper_per_ip_shaper_module.html#fortios-firewall-shaper-per-ip-shaper-module)
- [fortios_firewall_shaper_traffic_shaper – Configure shared traffic shaper in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_shaper_traffic_shaper_module.html#fortios-firewall-shaper-traffic-shaper-module)
- [fortios_firewall_shaping_policy – Configure shaping policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_shaping_policy_module.html#fortios-firewall-shaping-policy-module)
- [fortios_firewall_shaping_profile – Configure shaping profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_shaping_profile_module.html#fortios-firewall-shaping-profile-module)
- [fortios_firewall_sniffer – Configure sniffer in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_sniffer_module.html#fortios-firewall-sniffer-module)
- [fortios_firewall_ssh_host_key – SSH proxy host public keys in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ssh_host_key_module.html#fortios-firewall-ssh-host-key-module)
- [fortios_firewall_ssh_local_ca – SSH proxy local CA in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ssh_local_ca_module.html#fortios-firewall-ssh-local-ca-module)
- [fortios_firewall_ssh_local_key – SSH proxy local keys in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ssh_local_key_module.html#fortios-firewall-ssh-local-key-module)
- [fortios_firewall_ssh_setting – SSH proxy settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ssh_setting_module.html#fortios-firewall-ssh-setting-module)
- [fortios_firewall_ssl_server – Configure SSL servers in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ssl_server_module.html#fortios-firewall-ssl-server-module)
- [fortios_firewall_ssl_setting – SSL proxy settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ssl_setting_module.html#fortios-firewall-ssl-setting-module)
- [fortios_firewall_ssl_ssh_profile – Configure SSL/SSH protocol options in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ssl_ssh_profile_module.html#fortios-firewall-ssl-ssh-profile-module)
- [fortios_firewall_ttl_policy – Configure TTL policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_ttl_policy_module.html#fortios-firewall-ttl-policy-module)
- [fortios_firewall_vip – Configure virtual IP for IPv4 in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_vip_module.html#fortios-firewall-vip-module)
- [fortios_firewall_vip46 – Configure IPv4 to IPv6 virtual IPs in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_vip46_module.html#fortios-firewall-vip46-module)
- [fortios_firewall_vip6 – Configure virtual IP for IPv6 in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_vip6_module.html#fortios-firewall-vip6-module)
- [fortios_firewall_vip64 – Configure IPv6 to IPv4 virtual IPs in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_vip64_module.html#fortios-firewall-vip64-module)
- [fortios_firewall_vipgrp – Configure IPv4 virtual IP groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_vipgrp_module.html#fortios-firewall-vipgrp-module)
- [fortios_firewall_vipgrp46 – Configure IPv4 to IPv6 virtual IP groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_vipgrp46_module.html#fortios-firewall-vipgrp46-module)
- [fortios_firewall_vipgrp6 – Configure IPv6 virtual IP groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_vipgrp6_module.html#fortios-firewall-vipgrp6-module)
- [fortios_firewall_vipgrp64 – Configure IPv6 to IPv4 virtual IP groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_vipgrp64_module.html#fortios-firewall-vipgrp64-module)
- [fortios_firewall_wildcard_fqdn_custom – Config global/VDOM Wildcard FQDN address in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_wildcard_fqdn_custom_module.html#fortios-firewall-wildcard-fqdn-custom-module)
- [fortios_firewall_wildcard_fqdn_group – Config global Wildcard FQDN address groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_firewall_wildcard_fqdn_group_module.html#fortios-firewall-wildcard-fqdn-group-module)
- [fortios_ftp_proxy_explicit – Configure explicit FTP proxy settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_ftp_proxy_explicit_module.html#fortios-ftp-proxy-explicit-module)
- [fortios_icap_profile – Configure ICAP profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_icap_profile_module.html#fortios-icap-profile-module)
- [fortios_icap_server – Configure ICAP servers in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_icap_server_module.html#fortios-icap-server-module)
- [fortios_ips_custom – Configure IPS custom signature in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_ips_custom_module.html#fortios-ips-custom-module)
- [fortios_ips_decoder – Configure IPS decoder in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_ips_decoder_module.html#fortios-ips-decoder-module)
- [fortios_ips_global – Configure IPS global parameter in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_ips_global_module.html#fortios-ips-global-module)
- [fortios_ips_rule – Configure IPS rules in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_ips_rule_module.html#fortios-ips-rule-module)
- [fortios_ips_rule_settings – Configure IPS rule setting in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_ips_rule_settings_module.html#fortios-ips-rule-settings-module)
- [fortios_ips_sensor – Configure IPS sensor in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_ips_sensor_module.html#fortios-ips-sensor-module)
- [fortios_ips_settings – Configure IPS VDOM parameter in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_ips_settings_module.html#fortios-ips-settings-module)
- [fortios_ipv4_policy – Manage IPv4 policy objects on Fortinet FortiOS firewall devices](https://docs.ansible.com/ansible/latest/modules/fortios_ipv4_policy_module.html#fortios-ipv4-policy-module)
- [fortios_log_custom_field – Configure custom log fields in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_custom_field_module.html#fortios-log-custom-field-module)
- [fortios_log_disk_filter – Configure filters for local disk logging. Use these filters to determine the log messages to record according to severity and type in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_disk_filter_module.html#fortios-log-disk-filter-module)
- [fortios_log_disk_setting – Settings for local disk logging in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_disk_setting_module.html#fortios-log-disk-setting-module)
- [fortios_log_eventfilter – Configure log event filters in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_eventfilter_module.html#fortios-log-eventfilter-module)
- [fortios_log_fortianalyzer2_filter – Filters for FortiAnalyzer in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortianalyzer2_filter_module.html#fortios-log-fortianalyzer2-filter-module)
- [fortios_log_fortianalyzer2_setting – Global FortiAnalyzer settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortianalyzer2_setting_module.html#fortios-log-fortianalyzer2-setting-module)
- [fortios_log_fortianalyzer3_filter – Filters for FortiAnalyzer in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortianalyzer3_filter_module.html#fortios-log-fortianalyzer3-filter-module)
- [fortios_log_fortianalyzer3_setting – Global FortiAnalyzer settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortianalyzer3_setting_module.html#fortios-log-fortianalyzer3-setting-module)
- [fortios_log_fortianalyzer_filter – Filters for FortiAnalyzer in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortianalyzer_filter_module.html#fortios-log-fortianalyzer-filter-module)
- [fortios_log_fortianalyzer_override_filter – Override filters for FortiAnalyzer in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortianalyzer_override_filter_module.html#fortios-log-fortianalyzer-override-filter-module)
- [fortios_log_fortianalyzer_override_setting – Override FortiAnalyzer settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortianalyzer_override_setting_module.html#fortios-log-fortianalyzer-override-setting-module)
- [fortios_log_fortianalyzer_setting – Global FortiAnalyzer settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortianalyzer_setting_module.html#fortios-log-fortianalyzer-setting-module)
- [fortios_log_fortiguard_filter – Filters for FortiCloud in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortiguard_filter_module.html#fortios-log-fortiguard-filter-module)
- [fortios_log_fortiguard_override_filter – Override filters for FortiCloud in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortiguard_override_filter_module.html#fortios-log-fortiguard-override-filter-module)
- [fortios_log_fortiguard_override_setting – Override global FortiCloud logging settings for this VDOM in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortiguard_override_setting_module.html#fortios-log-fortiguard-override-setting-module)
- [fortios_log_fortiguard_setting – Configure logging to FortiCloud in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_fortiguard_setting_module.html#fortios-log-fortiguard-setting-module)
- [fortios_log_gui_display – Configure how log messages are displayed on the GUI in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_gui_display_module.html#fortios-log-gui-display-module)
- [fortios_log_memory_filter – Filters for memory buffer in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_memory_filter_module.html#fortios-log-memory-filter-module)
- [fortios_log_memory_global_setting – Global settings for memory logging in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_memory_global_setting_module.html#fortios-log-memory-global-setting-module)
- [fortios_log_memory_setting – Settings for memory buffer in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_memory_setting_module.html#fortios-log-memory-setting-module)
- [fortios_log_null_device_filter – Filters for null device logging in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_null_device_filter_module.html#fortios-log-null-device-filter-module)
- [fortios_log_null_device_setting – Settings for null device logging in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_null_device_setting_module.html#fortios-log-null-device-setting-module)
- [fortios_log_setting – Configure general log settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_setting_module.html#fortios-log-setting-module)
- [fortios_log_syslogd2_filter – Filters for remote system server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_syslogd2_filter_module.html#fortios-log-syslogd2-filter-module)
- [fortios_log_syslogd2_setting – Global settings for remote syslog server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_syslogd2_setting_module.html#fortios-log-syslogd2-setting-module)
- [fortios_log_syslogd3_filter – Filters for remote system server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_syslogd3_filter_module.html#fortios-log-syslogd3-filter-module)
- [fortios_log_syslogd3_setting – Global settings for remote syslog server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_syslogd3_setting_module.html#fortios-log-syslogd3-setting-module)
- [fortios_log_syslogd4_filter – Filters for remote system server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_syslogd4_filter_module.html#fortios-log-syslogd4-filter-module)
- [fortios_log_syslogd4_setting – Global settings for remote syslog server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_syslogd4_setting_module.html#fortios-log-syslogd4-setting-module)
- [fortios_log_syslogd_filter – Filters for remote system server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_syslogd_filter_module.html#fortios-log-syslogd-filter-module)
- [fortios_log_syslogd_override_filter – Override filters for remote system server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_syslogd_override_filter_module.html#fortios-log-syslogd-override-filter-module)
- [fortios_log_syslogd_override_setting – Override settings for remote syslog server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_syslogd_override_setting_module.html#fortios-log-syslogd-override-setting-module)
- [fortios_log_syslogd_setting – Global settings for remote syslog server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_syslogd_setting_module.html#fortios-log-syslogd-setting-module)
- [fortios_log_threat_weight – Configure threat weight settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_threat_weight_module.html#fortios-log-threat-weight-module)
- [fortios_log_webtrends_filter – Filters for WebTrends in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_webtrends_filter_module.html#fortios-log-webtrends-filter-module)
- [fortios_log_webtrends_setting – Settings for WebTrends in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_log_webtrends_setting_module.html#fortios-log-webtrends-setting-module)
- [fortios_report_chart – Report chart widget configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_report_chart_module.html#fortios-report-chart-module)
- [fortios_report_dataset – Report dataset configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_report_dataset_module.html#fortios-report-dataset-module)
- [fortios_report_layout – Report layout configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_report_layout_module.html#fortios-report-layout-module)
- [fortios_report_setting – Report setting configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_report_setting_module.html#fortios-report-setting-module)
- [fortios_report_style – Report style configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_report_style_module.html#fortios-report-style-module)
- [fortios_report_theme – Report themes configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_report_theme_module.html#fortios-report-theme-module)
- [fortios_router_access_list – Configure access lists in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_access_list_module.html#fortios-router-access-list-module)
- [fortios_router_access_list6 – Configure IPv6 access lists in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_access_list6_module.html#fortios-router-access-list6-module)
- [fortios_router_aspath_list – Configure Autonomous System (AS) path lists in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_aspath_list_module.html#fortios-router-aspath-list-module)
- [fortios_router_auth_path – Configure authentication based routing in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_auth_path_module.html#fortios-router-auth-path-module)
- [fortios_router_bfd – Configure BFD in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_bfd_module.html#fortios-router-bfd-module)
- [fortios_router_bfd6 – Configure IPv6 BFD in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_bfd6_module.html#fortios-router-bfd6-module)
- [fortios_router_bgp – Configure BGP in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_bgp_module.html#fortios-router-bgp-module)
- [fortios_router_community_list – Configure community lists in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_community_list_module.html#fortios-router-community-list-module)
- [fortios_router_isis – Configure IS-IS in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_isis_module.html#fortios-router-isis-module)
- [fortios_router_key_chain – Configure key-chain in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_key_chain_module.html#fortios-router-key-chain-module)
- [fortios_router_multicast – Configure router multicast in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_multicast_module.html#fortios-router-multicast-module)
- [fortios_router_multicast6 – Configure IPv6 multicast in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_multicast6_module.html#fortios-router-multicast6-module)
- [fortios_router_multicast_flow – Configure multicast-flow in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_multicast_flow_module.html#fortios-router-multicast-flow-module)
- [fortios_router_ospf – Configure OSPF in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_ospf_module.html#fortios-router-ospf-module)
- [fortios_router_ospf6 – Configure IPv6 OSPF in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_ospf6_module.html#fortios-router-ospf6-module)
- [fortios_router_policy – Configure IPv4 routing policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_policy_module.html#fortios-router-policy-module)
- [fortios_router_policy6 – Configure IPv6 routing policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_policy6_module.html#fortios-router-policy6-module)
- [fortios_router_prefix_list – Configure IPv4 prefix lists in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_prefix_list_module.html#fortios-router-prefix-list-module)
- [fortios_router_prefix_list6 – Configure IPv6 prefix lists in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_prefix_list6_module.html#fortios-router-prefix-list6-module)
- [fortios_router_rip – Configure RIP in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_rip_module.html#fortios-router-rip-module)
- [fortios_router_ripng – Configure RIPng in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_ripng_module.html#fortios-router-ripng-module)
- [fortios_router_route_map – Configure route maps in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_route_map_module.html#fortios-router-route-map-module)
- [fortios_router_setting – Configure router settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_setting_module.html#fortios-router-setting-module)
- [fortios_router_static – Configure IPv4 static routing tables in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_static_module.html#fortios-router-static-module)
- [fortios_router_static6 – Configure IPv6 static routing tables in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_router_static6_module.html#fortios-router-static6-module)
- [fortios_spamfilter_bwl – Configure anti-spam black/white list in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_spamfilter_bwl_module.html#fortios-spamfilter-bwl-module)
- [fortios_spamfilter_bword – Configure AntiSpam banned word list in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_spamfilter_bword_module.html#fortios-spamfilter-bword-module)
- [fortios_spamfilter_dnsbl – Configure AntiSpam DNSBL/ORBL in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_spamfilter_dnsbl_module.html#fortios-spamfilter-dnsbl-module)
- [fortios_spamfilter_fortishield – Configure FortiGuard - AntiSpam in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_spamfilter_fortishield_module.html#fortios-spamfilter-fortishield-module)
- [fortios_spamfilter_iptrust – Configure AntiSpam IP trust in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_spamfilter_iptrust_module.html#fortios-spamfilter-iptrust-module)
- [fortios_spamfilter_mheader – Configure AntiSpam MIME header in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_spamfilter_mheader_module.html#fortios-spamfilter-mheader-module)
- [fortios_spamfilter_options – Configure AntiSpam options in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_spamfilter_options_module.html#fortios-spamfilter-options-module)
- [fortios_spamfilter_profile – Configure AntiSpam profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_spamfilter_profile_module.html#fortios-spamfilter-profile-module)
- [fortios_ssh_filter_profile – SSH filter profile in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_ssh_filter_profile_module.html#fortios-ssh-filter-profile-module)
- [fortios_switch_controller_802_1X_settings – Configure global 802.1X settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_802_1X_settings_module.html#fortios-switch-controller-802-1x-settings-module)
- [fortios_switch_controller_custom_command – Configure the FortiGate switch controller to send custom commands to managed FortiSwitch devices in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_custom_command_module.html#fortios-switch-controller-custom-command-module)
- [fortios_switch_controller_global – Configure FortiSwitch global settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_global_module.html#fortios-switch-controller-global-module)
- [fortios_switch_controller_igmp_snooping – Configure FortiSwitch IGMP snooping global settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_igmp_snooping_module.html#fortios-switch-controller-igmp-snooping-module)
- [fortios_switch_controller_lldp_profile – Configure FortiSwitch LLDP profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_lldp_profile_module.html#fortios-switch-controller-lldp-profile-module)
- [fortios_switch_controller_lldp_settings – Configure FortiSwitch LLDP settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_lldp_settings_module.html#fortios-switch-controller-lldp-settings-module)
- [fortios_switch_controller_mac_sync_settings – Configure global MAC synchronization settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_mac_sync_settings_module.html#fortios-switch-controller-mac-sync-settings-module)
- [fortios_switch_controller_managed_switch – Configure FortiSwitch devices that are managed by this FortiGate in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_managed_switch_module.html#fortios-switch-controller-managed-switch-module)
- [fortios_switch_controller_network_monitor_settings – Configure network monitor settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_network_monitor_settings_module.html#fortios-switch-controller-network-monitor-settings-module)
- [fortios_switch_controller_qos_dot1p_map – Configure FortiSwitch QoS 802.1p in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_qos_dot1p_map_module.html#fortios-switch-controller-qos-dot1p-map-module)
- [fortios_switch_controller_qos_ip_dscp_map – Configure FortiSwitch QoS IP precedence/DSCP in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_qos_ip_dscp_map_module.html#fortios-switch-controller-qos-ip-dscp-map-module)
- [fortios_switch_controller_qos_qos_policy – Configure FortiSwitch QoS policy in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_qos_qos_policy_module.html#fortios-switch-controller-qos-qos-policy-module)
- [fortios_switch_controller_qos_queue_policy – Configure FortiSwitch QoS egress queue policy in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_qos_queue_policy_module.html#fortios-switch-controller-qos-queue-policy-module)
- [fortios_switch_controller_quarantine – Configure FortiSwitch quarantine support in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_quarantine_module.html#fortios-switch-controller-quarantine-module)
- [fortios_switch_controller_security_policy_802_1X – Configure 802.1x MAC Authentication Bypass (MAB) policies in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_security_policy_802_1X_module.html#fortios-switch-controller-security-policy-802-1x-module)
- [fortios_switch_controller_security_policy_captive_portal – Names of VLANs that use captive portal authentication in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_security_policy_captive_portal_module.html#fortios-switch-controller-security-policy-captive-portal-module)
- [fortios_switch_controller_sflow – Configure FortiSwitch sFlow in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_sflow_module.html#fortios-switch-controller-sflow-module)
- [fortios_switch_controller_storm_control – Configure FortiSwitch storm control in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_storm_control_module.html#fortios-switch-controller-storm-control-module)
- [fortios_switch_controller_stp_settings – Configure FortiSwitch spanning tree protocol (STP) in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_stp_settings_module.html#fortios-switch-controller-stp-settings-module)
- [fortios_switch_controller_switch_group – Configure FortiSwitch switch groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_switch_group_module.html#fortios-switch-controller-switch-group-module)
- [fortios_switch_controller_switch_interface_tag – Configure switch object tags in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_switch_interface_tag_module.html#fortios-switch-controller-switch-interface-tag-module)
- [fortios_switch_controller_switch_log – Configure FortiSwitch logging (logs are transferred to and inserted into FortiGate event log) in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_switch_log_module.html#fortios-switch-controller-switch-log-module)
- [fortios_switch_controller_switch_profile – Configure FortiSwitch switch profile in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_switch_profile_module.html#fortios-switch-controller-switch-profile-module)
- [fortios_switch_controller_system – Configure system-wide switch controller settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_system_module.html#fortios-switch-controller-system-module)
- [fortios_switch_controller_virtual_port_pool – Configure virtual pool in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_virtual_port_pool_module.html#fortios-switch-controller-virtual-port-pool-module)
- [fortios_switch_controller_vlan – Configure VLANs for switch controller in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_switch_controller_vlan_module.html#fortios-switch-controller-vlan-module)
- [fortios_system_accprofile – Configure access profiles for system administrators in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_accprofile_module.html#fortios-system-accprofile-module)
- [fortios_system_admin – Configure admin users in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_admin_module.html#fortios-system-admin-module)
- [fortios_system_affinity_interrupt – Configure interrupt affinity in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_affinity_interrupt_module.html#fortios-system-affinity-interrupt-module)
- [fortios_system_affinity_packet_redistribution – Configure packet redistribution in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_affinity_packet_redistribution_module.html#fortios-system-affinity-packet-redistribution-module)
- [fortios_system_alarm – Configure alarm in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_alarm_module.html#fortios-system-alarm-module)
- [fortios_system_alias – Configure alias command in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_alias_module.html#fortios-system-alias-module)
- [fortios_system_api_user – Configure API users in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_api_user_module.html#fortios-system-api-user-module)
- [fortios_system_arp_table – Configure ARP table in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_arp_table_module.html#fortios-system-arp-table-module)
- [fortios_system_auto_install – Configure USB auto installation in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_auto_install_module.html#fortios-system-auto-install-module)
- [fortios_system_auto_script – Configure auto script in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_auto_script_module.html#fortios-system-auto-script-module)
- [fortios_system_automation_action – Action for automation stitches in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_automation_action_module.html#fortios-system-automation-action-module)
- [fortios_system_automation_destination – Automation destinations in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_automation_destination_module.html#fortios-system-automation-destination-module)
- [fortios_system_automation_stitch – Automation stitches in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_automation_stitch_module.html#fortios-system-automation-stitch-module)
- [fortios_system_automation_trigger – Trigger for automation stitches in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_automation_trigger_module.html#fortios-system-automation-trigger-module)
- [fortios_system_autoupdate_push_update – Configure push updates in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_autoupdate_push_update_module.html#fortios-system-autoupdate-push-update-module)
- [fortios_system_autoupdate_schedule – Configure update schedule in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_autoupdate_schedule_module.html#fortios-system-autoupdate-schedule-module)
- [fortios_system_autoupdate_tunneling – Configure web proxy tunnelling for the FDN in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_autoupdate_tunneling_module.html#fortios-system-autoupdate-tunneling-module)
- [fortios_system_central_management – Configure central management in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_central_management_module.html#fortios-system-central-management-module)
- [fortios_system_cluster_sync – Configure FortiGate Session Life Support Protocol (FGSP) session synchronization in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_cluster_sync_module.html#fortios-system-cluster-sync-module)
- [fortios_system_console – Configure console in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_console_module.html#fortios-system-console-module)
- [fortios_system_csf – Add this FortiGate to a Security Fabric or set up a new Security Fabric on this FortiGate in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_csf_module.html#fortios-system-csf-module)
- [fortios_system_custom_language – Configure custom languages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_custom_language_module.html#fortios-system-custom-language-module)
- [fortios_system_ddns – Configure DDNS in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_ddns_module.html#fortios-system-ddns-module)
- [fortios_system_dedicated_mgmt – Configure dedicated management in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_dedicated_mgmt_module.html#fortios-system-dedicated-mgmt-module)
- [fortios_system_dhcp6_server – Configure DHCPv6 servers in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_dhcp6_server_module.html#fortios-system-dhcp6-server-module)
- [fortios_system_dhcp_server – Configure DHCP servers in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_dhcp_server_module.html#fortios-system-dhcp-server-module)
- [fortios_system_dns – Configure DNS in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_dns_module.html#fortios-system-dns-module)
- [fortios_system_dns_database – Configure DNS databases in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_dns_database_module.html#fortios-system-dns-database-module)
- [fortios_system_dns_server – Configure DNS servers in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_dns_server_module.html#fortios-system-dns-server-module)
- [fortios_system_dscp_based_priority – Configure DSCP based priority table in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_dscp_based_priority_module.html#fortios-system-dscp-based-priority-module)
- [fortios_system_email_server – Configure the email server used by the FortiGate various things. For example, for sending email messages to users to support user authentication features in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_email_server_module.html#fortios-system-email-server-module)
- [fortios_system_external_resource – Configure external resource in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_external_resource_module.html#fortios-system-external-resource-module)
- [fortios_system_fips_cc – Configure FIPS-CC mode in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_fips_cc_module.html#fortios-system-fips-cc-module)
- [fortios_system_firmware_upgrade – Perform firmware upgrade on FortiGate or FortiOS (FOS) device](https://docs.ansible.com/ansible/latest/modules/fortios_system_firmware_upgrade_module.html#fortios-system-firmware-upgrade-module)
- [fortios_system_fm – Configure FM in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_fm_module.html#fortios-system-fm-module)
- [fortios_system_fortiguard – Configure FortiGuard services in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_fortiguard_module.html#fortios-system-fortiguard-module)
- [fortios_system_fortimanager – Configure FortiManager in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_fortimanager_module.html#fortios-system-fortimanager-module)
- [fortios_system_fortisandbox – Configure FortiSandbox in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_fortisandbox_module.html#fortios-system-fortisandbox-module)
- [fortios_system_fsso_polling – Configure Fortinet Single Sign On (FSSO) server in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_fsso_polling_module.html#fortios-system-fsso-polling-module)
- [fortios_system_ftm_push – Configure FortiToken Mobile push services in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_ftm_push_module.html#fortios-system-ftm-push-module)
- [fortios_system_geoip_override – Configure geographical location mapping for IP address(es) to override mappings from FortiGuard in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_geoip_override_module.html#fortios-system-geoip-override-module)
- [fortios_system_global – Configure global attributes in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_global_module.html#fortios-system-global-module)
- [fortios_system_gre_tunnel – Configure GRE tunnel in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_gre_tunnel_module.html#fortios-system-gre-tunnel-module)
- [fortios_system_ha – Configure HA in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_ha_module.html#fortios-system-ha-module)
- [fortios_system_ha_monitor – Configure HA monitor in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_ha_monitor_module.html#fortios-system-ha-monitor-module)
- [fortios_system_interface – Configure interfaces in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_interface_module.html#fortios-system-interface-module)
- [fortios_system_ipip_tunnel – Configure IP in IP Tunneling in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_ipip_tunnel_module.html#fortios-system-ipip-tunnel-module)
- [fortios_system_ips_urlfilter_dns – Configure IPS URL filter DNS servers in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_ips_urlfilter_dns_module.html#fortios-system-ips-urlfilter-dns-module)
- [fortios_system_ips_urlfilter_dns6 – Configure IPS URL filter IPv6 DNS servers in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_ips_urlfilter_dns6_module.html#fortios-system-ips-urlfilter-dns6-module)
- [fortios_system_ipv6_neighbor_cache – Configure IPv6 neighbor cache table in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_ipv6_neighbor_cache_module.html#fortios-system-ipv6-neighbor-cache-module)
- [fortios_system_ipv6_tunnel – Configure IPv6/IPv4 in IPv6 tunnel in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_ipv6_tunnel_module.html#fortios-system-ipv6-tunnel-module)
- [fortios_system_link_monitor – Configure Link Health Monitor in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_link_monitor_module.html#fortios-system-link-monitor-module)
- [fortios_system_mac_address_table – Configure MAC address tables in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_mac_address_table_module.html#fortios-system-mac-address-table-module)
- [fortios_system_management_tunnel – Management tunnel configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_management_tunnel_module.html#fortios-system-management-tunnel-module)
- [fortios_system_mobile_tunnel – Configure Mobile tunnels, an implementation of Network Mobility (NEMO) extensions for Mobile IPv4 RFC5177 in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_mobile_tunnel_module.html#fortios-system-mobile-tunnel-module)
- [fortios_system_nat64 – Configure NAT64 in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_nat64_module.html#fortios-system-nat64-module)
- [fortios_system_nd_proxy – Configure IPv6 neighbor discovery proxy (RFC4389) in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_nd_proxy_module.html#fortios-system-nd-proxy-module)
- [fortios_system_netflow – Configure NetFlow in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_netflow_module.html#fortios-system-netflow-module)
- [fortios_system_network_visibility – Configure network visibility settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_network_visibility_module.html#fortios-system-network-visibility-module)
- [fortios_system_ntp – Configure system NTP information in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_ntp_module.html#fortios-system-ntp-module)
- [fortios_system_object_tagging – Configure object tagging in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_object_tagging_module.html#fortios-system-object-tagging-module)
- [fortios_system_password_policy – Configure password policy for locally defined administrator passwords and IPsec VPN pre-shared keys in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_password_policy_module.html#fortios-system-password-policy-module)
- [fortios_system_password_policy_guest_admin – Configure the password policy for guest administrators in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_password_policy_guest_admin_module.html#fortios-system-password-policy-guest-admin-module)
- [fortios_system_pppoe_interface – Configure the PPPoE interfaces in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_pppoe_interface_module.html#fortios-system-pppoe-interface-module)
- [fortios_system_probe_response – Configure system probe response in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_probe_response_module.html#fortios-system-probe-response-module)
- [fortios_system_proxy_arp – Configure proxy-ARP in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_proxy_arp_module.html#fortios-system-proxy-arp-module)
- [fortios_system_replacemsg_admin – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_admin_module.html#fortios-system-replacemsg-admin-module)
- [fortios_system_replacemsg_alertmail – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_alertmail_module.html#fortios-system-replacemsg-alertmail-module)
- [fortios_system_replacemsg_auth – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_auth_module.html#fortios-system-replacemsg-auth-module)
- [fortios_system_replacemsg_device_detection_portal – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_device_detection_portal_module.html#fortios-system-replacemsg-device-detection-portal-module)
- [fortios_system_replacemsg_ec – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_ec_module.html#fortios-system-replacemsg-ec-module)
- [fortios_system_replacemsg_fortiguard_wf – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_fortiguard_wf_module.html#fortios-system-replacemsg-fortiguard-wf-module)
- [fortios_system_replacemsg_ftp – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_ftp_module.html#fortios-system-replacemsg-ftp-module)
- [fortios_system_replacemsg_group – Configure replacement message groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_group_module.html#fortios-system-replacemsg-group-module)
- [fortios_system_replacemsg_http – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_http_module.html#fortios-system-replacemsg-http-module)
- [fortios_system_replacemsg_icap – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_icap_module.html#fortios-system-replacemsg-icap-module)
- [fortios_system_replacemsg_image – Configure replacement message images in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_image_module.html#fortios-system-replacemsg-image-module)
- [fortios_system_replacemsg_mail – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_mail_module.html#fortios-system-replacemsg-mail-module)
- [fortios_system_replacemsg_nac_quar – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_nac_quar_module.html#fortios-system-replacemsg-nac-quar-module)
- [fortios_system_replacemsg_nntp – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_nntp_module.html#fortios-system-replacemsg-nntp-module)
- [fortios_system_replacemsg_spam – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_spam_module.html#fortios-system-replacemsg-spam-module)
- [fortios_system_replacemsg_sslvpn – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_sslvpn_module.html#fortios-system-replacemsg-sslvpn-module)
- [fortios_system_replacemsg_traffic_quota – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_traffic_quota_module.html#fortios-system-replacemsg-traffic-quota-module)
- [fortios_system_replacemsg_utm – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_utm_module.html#fortios-system-replacemsg-utm-module)
- [fortios_system_replacemsg_webproxy – Replacement messages in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_replacemsg_webproxy_module.html#fortios-system-replacemsg-webproxy-module)
- [fortios_system_resource_limits – Configure resource limits in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_resource_limits_module.html#fortios-system-resource-limits-module)
- [fortios_system_sdn_connector – Configure connection to SDN Connector in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_sdn_connector_module.html#fortios-system-sdn-connector-module)
- [fortios_system_session_helper – Configure session helper in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_session_helper_module.html#fortios-system-session-helper-module)
- [fortios_system_session_ttl – Configure global session TTL timers for this FortiGate in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_session_ttl_module.html#fortios-system-session-ttl-module)
- [fortios_system_settings – Configure VDOM settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_settings_module.html#fortios-system-settings-module)
- [fortios_system_sflow – Configure sFlow in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_sflow_module.html#fortios-system-sflow-module)
- [fortios_system_sit_tunnel – Configure IPv6 tunnel over IPv4 in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_sit_tunnel_module.html#fortios-system-sit-tunnel-module)
- [fortios_system_sms_server – Configure SMS server for sending SMS messages to support user authentication in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_sms_server_module.html#fortios-system-sms-server-module)
- [fortios_system_snmp_community – SNMP community configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_snmp_community_module.html#fortios-system-snmp-community-module)
- [fortios_system_snmp_sysinfo – SNMP system info configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_snmp_sysinfo_module.html#fortios-system-snmp-sysinfo-module)
- [fortios_system_snmp_user – SNMP user configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_snmp_user_module.html#fortios-system-snmp-user-module)
- [fortios_system_storage – Configure logical storage in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_storage_module.html#fortios-system-storage-module)
- [fortios_system_switch_interface – Configure software switch interfaces by grouping physical and WiFi interfaces in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_switch_interface_module.html#fortios-system-switch-interface-module)
- [fortios_system_tos_based_priority – Configure Type of Service (ToS) based priority table to set network traffic priorities in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_tos_based_priority_module.html#fortios-system-tos-based-priority-module)
- [fortios_system_vdom – Configure virtual domain in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_vdom_module.html#fortios-system-vdom-module)
- [fortios_system_vdom_dns – Configure DNS servers for a non-management VDOM in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_vdom_dns_module.html#fortios-system-vdom-dns-module)
- [fortios_system_vdom_exception – Global configuration objects that can be configured independently for all VDOMs or for the defined VDOM scope in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_vdom_exception_module.html#fortios-system-vdom-exception-module)
- [fortios_system_vdom_link – Configure VDOM links in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_vdom_link_module.html#fortios-system-vdom-link-module)
- [fortios_system_vdom_netflow – Configure NetFlow per VDOM in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_vdom_netflow_module.html#fortios-system-vdom-netflow-module)
- [fortios_system_vdom_property – Configure VDOM property in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_vdom_property_module.html#fortios-system-vdom-property-module)
- [fortios_system_vdom_radius_server – Configure a RADIUS server to use as a RADIUS Single Sign On (RSSO) server for this VDOM in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_vdom_radius_server_module.html#fortios-system-vdom-radius-server-module)
- [fortios_system_vdom_sflow – Configure sFlow per VDOM to add or change the IP address and UDP port that FortiGate sFlow agents in this VDOM use to send sFlow datagrams to an sFlow collector in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_vdom_sflow_module.html#fortios-system-vdom-sflow-module)
- [fortios_system_virtual_wan_link – Configure redundant internet connections using SD-WAN (formerly virtual WAN link) in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_virtual_wan_link_module.html#fortios-system-virtual-wan-link-module)
- [fortios_system_virtual_wire_pair – Configure virtual wire pairs in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_virtual_wire_pair_module.html#fortios-system-virtual-wire-pair-module)
- [fortios_system_vxlan – Configure VXLAN devices in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_vxlan_module.html#fortios-system-vxlan-module)
- [fortios_system_wccp – Configure WCCP in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_wccp_module.html#fortios-system-wccp-module)
- [fortios_system_zone – Configure zones to group two or more interfaces. When a zone is created you can configure policies for the zone instead of individual interfaces in the zone in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_system_zone_module.html#fortios-system-zone-module)
- [fortios_user_adgrp – Configure FSSO groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_adgrp_module.html#fortios-user-adgrp-module)
- [fortios_user_device – Configure devices in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_device_module.html#fortios-user-device-module)
- [fortios_user_device_access_list – Configure device access control lists in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_device_access_list_module.html#fortios-user-device-access-list-module)
- [fortios_user_device_category – Configure device categories in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_device_category_module.html#fortios-user-device-category-module)
- [fortios_user_device_group – Configure device groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_device_group_module.html#fortios-user-device-group-module)
- [fortios_user_domain_controller – Configure domain controller entries in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_domain_controller_module.html#fortios-user-domain-controller-module)
- [fortios_user_fortitoken – Configure FortiToken in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_fortitoken_module.html#fortios-user-fortitoken-module)
- [fortios_user_fsso – Configure Fortinet Single Sign On (FSSO) agents in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_fsso_module.html#fortios-user-fsso-module)
- [fortios_user_fsso_polling – Configure FSSO active directory servers for polling mode in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_fsso_polling_module.html#fortios-user-fsso-polling-module)
- [fortios_user_group – Configure user groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_group_module.html#fortios-user-group-module)
- [fortios_user_krb_keytab – Configure Kerberos keytab entries in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_krb_keytab_module.html#fortios-user-krb-keytab-module)
- [fortios_user_ldap – Configure LDAP server entries in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_ldap_module.html#fortios-user-ldap-module)
- [fortios_user_local – Configure local users in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_local_module.html#fortios-user-local-module)
- [fortios_user_password_policy – Configure user password policy in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_password_policy_module.html#fortios-user-password-policy-module)
- [fortios_user_peer – Configure peer users in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_peer_module.html#fortios-user-peer-module)
- [fortios_user_peergrp – Configure peer groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_peergrp_module.html#fortios-user-peergrp-module)
- [fortios_user_pop3 – POP3 server entry configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_pop3_module.html#fortios-user-pop3-module)
- [fortios_user_quarantine – Configure quarantine support in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_quarantine_module.html#fortios-user-quarantine-module)
- [fortios_user_radius – Configure RADIUS server entries in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_radius_module.html#fortios-user-radius-module)
- [fortios_user_security_exempt_list – Configure security exemption list in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_security_exempt_list_module.html#fortios-user-security-exempt-list-module)
- [fortios_user_setting – Configure user authentication setting in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_setting_module.html#fortios-user-setting-module)
- [fortios_user_tacacsplus – Configure TACACS+ server entries in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_user_tacacsplus_module.html#fortios-user-tacacsplus-module)
- [fortios_voip_profile – Configure VoIP profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_voip_profile_module.html#fortios-voip-profile-module)
- [fortios_vpn_certificate_ca – CA certificate in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_certificate_ca_module.html#fortios-vpn-certificate-ca-module)
- [fortios_vpn_certificate_crl – Certificate Revocation List as a PEM file in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_certificate_crl_module.html#fortios-vpn-certificate-crl-module)
- [fortios_vpn_certificate_local – Local keys and certificates in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_certificate_local_module.html#fortios-vpn-certificate-local-module)
- [fortios_vpn_certificate_ocsp_server – OCSP server configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_certificate_ocsp_server_module.html#fortios-vpn-certificate-ocsp-server-module)
- [fortios_vpn_certificate_remote – Remote certificate as a PEM file in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_certificate_remote_module.html#fortios-vpn-certificate-remote-module)
- [fortios_vpn_certificate_setting – VPN certificate setting in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_certificate_setting_module.html#fortios-vpn-certificate-setting-module)
- [fortios_vpn_ipsec_concentrator – Concentrator configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ipsec_concentrator_module.html#fortios-vpn-ipsec-concentrator-module)
- [fortios_vpn_ipsec_forticlient – Configure FortiClient policy realm in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ipsec_forticlient_module.html#fortios-vpn-ipsec-forticlient-module)
- [fortios_vpn_ipsec_manualkey – Configure IPsec manual keys in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ipsec_manualkey_module.html#fortios-vpn-ipsec-manualkey-module)
- [fortios_vpn_ipsec_manualkey_interface – Configure IPsec manual keys in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ipsec_manualkey_interface_module.html#fortios-vpn-ipsec-manualkey-interface-module)
- [fortios_vpn_ipsec_phase1 – Configure VPN remote gateway in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ipsec_phase1_module.html#fortios-vpn-ipsec-phase1-module)
- [fortios_vpn_ipsec_phase1_interface – Configure VPN remote gateway in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ipsec_phase1_interface_module.html#fortios-vpn-ipsec-phase1-interface-module)
- [fortios_vpn_ipsec_phase2 – Configure VPN autokey tunnel in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ipsec_phase2_module.html#fortios-vpn-ipsec-phase2-module)
- [fortios_vpn_ipsec_phase2_interface – Configure VPN autokey tunnel in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ipsec_phase2_interface_module.html#fortios-vpn-ipsec-phase2-interface-module)
- [fortios_vpn_l2tp – Configure L2TP in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_l2tp_module.html#fortios-vpn-l2tp-module)
- [fortios_vpn_pptp – Configure PPTP in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_pptp_module.html#fortios-vpn-pptp-module)
- [fortios_vpn_ssl_settings – Configure SSL VPN in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ssl_settings_module.html#fortios-vpn-ssl-settings-module)
- [fortios_vpn_ssl_web_host_check_software – SSL-VPN host check software in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ssl_web_host_check_software_module.html#fortios-vpn-ssl-web-host-check-software-module)
- [fortios_vpn_ssl_web_portal – Portal in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ssl_web_portal_module.html#fortios-vpn-ssl-web-portal-module)
- [fortios_vpn_ssl_web_realm – Realm in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ssl_web_realm_module.html#fortios-vpn-ssl-web-realm-module)
- [fortios_vpn_ssl_web_user_bookmark – Configure SSL VPN user bookmark in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ssl_web_user_bookmark_module.html#fortios-vpn-ssl-web-user-bookmark-module)
- [fortios_vpn_ssl_web_user_group_bookmark – Configure SSL VPN user group bookmark in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_vpn_ssl_web_user_group_bookmark_module.html#fortios-vpn-ssl-web-user-group-bookmark-module)
- [fortios_waf_main_class – Hidden table for datasource in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_waf_main_class_module.html#fortios-waf-main-class-module)
- [fortios_waf_profile – Web application firewall configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_waf_profile_module.html#fortios-waf-profile-module)
- [fortios_waf_signature – Hidden table for datasource in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_waf_signature_module.html#fortios-waf-signature-module)
- [fortios_waf_sub_class – Hidden table for datasource in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_waf_sub_class_module.html#fortios-waf-sub-class-module)
- [fortios_wanopt_auth_group – Configure WAN optimization authentication groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wanopt_auth_group_module.html#fortios-wanopt-auth-group-module)
- [fortios_wanopt_cache_service – Designate cache-service for wan-optimization and webcache in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wanopt_cache_service_module.html#fortios-wanopt-cache-service-module)
- [fortios_wanopt_content_delivery_network_rule – Configure WAN optimization content delivery network rules in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wanopt_content_delivery_network_rule_module.html#fortios-wanopt-content-delivery-network-rule-module)
- [fortios_wanopt_peer – Configure WAN optimization peers in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wanopt_peer_module.html#fortios-wanopt-peer-module)
- [fortios_wanopt_profile – Configure WAN optimization profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wanopt_profile_module.html#fortios-wanopt-profile-module)
- [fortios_wanopt_remote_storage – Configure a remote cache device as Web cache storage in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wanopt_remote_storage_module.html#fortios-wanopt-remote-storage-module)
- [fortios_wanopt_settings – Configure WAN optimization settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wanopt_settings_module.html#fortios-wanopt-settings-module)
- [fortios_wanopt_webcache – Configure global Web cache settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wanopt_webcache_module.html#fortios-wanopt-webcache-module)
- [fortios_web_proxy_debug_url – Configure debug URL addresses in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_web_proxy_debug_url_module.html#fortios-web-proxy-debug-url-module)
- [fortios_web_proxy_explicit – Configure explicit Web proxy settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_web_proxy_explicit_module.html#fortios-web-proxy-explicit-module)
- [fortios_web_proxy_forward_server – Configure forward-server addresses in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_web_proxy_forward_server_module.html#fortios-web-proxy-forward-server-module)
- [fortios_web_proxy_forward_server_group – Configure a forward server group consisting or multiple forward servers. Supports failover and load balancing in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_web_proxy_forward_server_group_module.html#fortios-web-proxy-forward-server-group-module)
- [fortios_web_proxy_global – Configure Web proxy global settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_web_proxy_global_module.html#fortios-web-proxy-global-module)
- [fortios_web_proxy_profile – Configure web proxy profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_web_proxy_profile_module.html#fortios-web-proxy-profile-module)
- [fortios_web_proxy_url_match – Exempt URLs from web proxy forwarding and caching in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_web_proxy_url_match_module.html#fortios-web-proxy-url-match-module)
- [fortios_web_proxy_wisp – Configure Wireless Internet service provider (WISP) servers in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_web_proxy_wisp_module.html#fortios-web-proxy-wisp-module)
- [fortios_webfilter – Configure webfilter capabilities of FortiGate and FortiOS](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_module.html#fortios-webfilter-module)
- [fortios_webfilter_content – Configure Web filter banned word table in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_content_module.html#fortios-webfilter-content-module)
- [fortios_webfilter_content_header – Configure content types used by Web filter in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_content_header_module.html#fortios-webfilter-content-header-module)
- [fortios_webfilter_fortiguard – Configure FortiGuard Web Filter service in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_fortiguard_module.html#fortios-webfilter-fortiguard-module)
- [fortios_webfilter_ftgd_local_cat – Configure FortiGuard Web Filter local categories in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_ftgd_local_cat_module.html#fortios-webfilter-ftgd-local-cat-module)
- [fortios_webfilter_ftgd_local_rating – Configure local FortiGuard Web Filter local ratings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_ftgd_local_rating_module.html#fortios-webfilter-ftgd-local-rating-module)
- [fortios_webfilter_ips_urlfilter_cache_setting – Configure IPS URL filter cache settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_ips_urlfilter_cache_setting_module.html#fortios-webfilter-ips-urlfilter-cache-setting-module)
- [fortios_webfilter_ips_urlfilter_setting – Configure IPS URL filter settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_ips_urlfilter_setting_module.html#fortios-webfilter-ips-urlfilter-setting-module)
- [fortios_webfilter_ips_urlfilter_setting6 – Configure IPS URL filter settings for IPv6 in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_ips_urlfilter_setting6_module.html#fortios-webfilter-ips-urlfilter-setting6-module)
- [fortios_webfilter_override – Configure FortiGuard Web Filter administrative overrides in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_override_module.html#fortios-webfilter-override-module)
- [fortios_webfilter_profile – Configure Web filter profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_profile_module.html#fortios-webfilter-profile-module)
- [fortios_webfilter_search_engine – Configure web filter search engines in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_search_engine_module.html#fortios-webfilter-search-engine-module)
- [fortios_webfilter_urlfilter – Configure URL filter lists in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_webfilter_urlfilter_module.html#fortios-webfilter-urlfilter-module)
- [fortios_wireless_controller_ap_status – Configure access point status (rogue | accepted | suppressed) in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_ap_status_module.html#fortios-wireless-controller-ap-status-module)
- [fortios_wireless_controller_ble_profile – Configure Bluetooth Low Energy profile in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_ble_profile_module.html#fortios-wireless-controller-ble-profile-module)
- [fortios_wireless_controller_bonjour_profile – Configure Bonjour profiles. Bonjour is Apple’s zero configuration networking protocol. Bonjour profiles allow APs and FortiAPs to connect to networks using Bonjour in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_bonjour_profile_module.html#fortios-wireless-controller-bonjour-profile-module)
- [fortios_wireless_controller_global – Configure wireless controller global settings in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_global_module.html#fortios-wireless-controller-global-module)
- [fortios_wireless_controller_hotspot20_anqp_3gpp_cellular – Configure 3GPP public land mobile network (PLMN) in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_anqp_3gpp_cellular_module.html#fortios-wireless-controller-hotspot20-anqp-3gpp-cellular-module)
- [fortios_wireless_controller_hotspot20_anqp_ip_address_type – Configure IP address type availability in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_anqp_ip_address_type_module.html#fortios-wireless-controller-hotspot20-anqp-ip-address-type-module)
- [fortios_wireless_controller_hotspot20_anqp_nai_realm – Configure network access identifier (NAI) realm in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_anqp_nai_realm_module.html#fortios-wireless-controller-hotspot20-anqp-nai-realm-module)
- [fortios_wireless_controller_hotspot20_anqp_network_auth_type – Configure network authentication type in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_anqp_network_auth_type_module.html#fortios-wireless-controller-hotspot20-anqp-network-auth-type-module)
- [fortios_wireless_controller_hotspot20_anqp_roaming_consortium – Configure roaming consortium in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_anqp_roaming_consortium_module.html#fortios-wireless-controller-hotspot20-anqp-roaming-consortium-module)
- [fortios_wireless_controller_hotspot20_anqp_venue_name – Configure venue name duple in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_anqp_venue_name_module.html#fortios-wireless-controller-hotspot20-anqp-venue-name-module)
- [fortios_wireless_controller_hotspot20_h2qp_conn_capability – Configure connection capability in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_h2qp_conn_capability_module.html#fortios-wireless-controller-hotspot20-h2qp-conn-capability-module)
- [fortios_wireless_controller_hotspot20_h2qp_operator_name – Configure operator friendly name in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_h2qp_operator_name_module.html#fortios-wireless-controller-hotspot20-h2qp-operator-name-module)
- [fortios_wireless_controller_hotspot20_h2qp_osu_provider – Configure online sign up (OSU) provider list in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_h2qp_osu_provider_module.html#fortios-wireless-controller-hotspot20-h2qp-osu-provider-module)
- [fortios_wireless_controller_hotspot20_h2qp_wan_metric – Configure WAN metrics in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_h2qp_wan_metric_module.html#fortios-wireless-controller-hotspot20-h2qp-wan-metric-module)
- [fortios_wireless_controller_hotspot20_hs_profile – Configure hotspot profile in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_hs_profile_module.html#fortios-wireless-controller-hotspot20-hs-profile-module)
- [fortios_wireless_controller_hotspot20_icon – Configure OSU provider icon in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_icon_module.html#fortios-wireless-controller-hotspot20-icon-module)
- [fortios_wireless_controller_hotspot20_qos_map – Configure QoS map set in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_hotspot20_qos_map_module.html#fortios-wireless-controller-hotspot20-qos-map-module)
- [fortios_wireless_controller_inter_controller – Configure inter wireless controller operation in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_inter_controller_module.html#fortios-wireless-controller-inter-controller-module)
- [fortios_wireless_controller_qos_profile – Configure WiFi quality of service (QoS) profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_qos_profile_module.html#fortios-wireless-controller-qos-profile-module)
- [fortios_wireless_controller_setting – VDOM wireless controller configuration in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_setting_module.html#fortios-wireless-controller-setting-module)
- [fortios_wireless_controller_timers – Configure CAPWAP timers in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_timers_module.html#fortios-wireless-controller-timers-module)
- [fortios_wireless_controller_utm_profile – Configure UTM (Unified Threat Management) profile in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_utm_profile_module.html#fortios-wireless-controller-utm-profile-module)
- [fortios_wireless_controller_vap – Configure Virtual Access Points (VAPs) in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_vap_module.html#fortios-wireless-controller-vap-module)
- [fortios_wireless_controller_vap_group – Configure virtual Access Point (VAP) groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_vap_group_module.html#fortios-wireless-controller-vap-group-module)
- [fortios_wireless_controller_wids_profile – Configure wireless intrusion detection system (WIDS) profiles in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_wids_profile_module.html#fortios-wireless-controller-wids-profile-module)
- [fortios_wireless_controller_wtp – Configure Wireless Termination Points (WTPs), that is, FortiAPs or APs to be managed by FortiGate in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_wtp_module.html#fortios-wireless-controller-wtp-module)
- [fortios_wireless_controller_wtp_group – Configure WTP groups in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_wtp_group_module.html#fortios-wireless-controller-wtp-group-module)
- [fortios_wireless_controller_wtp_profile – Configure WTP profiles or FortiAP profiles that define radio settings for manageable FortiAP platforms in Fortinet’s FortiOS and FortiGate](https://docs.ansible.com/ansible/latest/modules/fortios_wireless_controller_wtp_profile_module.html#fortios-wireless-controller-wtp-profile-module)



### Frr

- [frr_bgp – Configure global BGP settings on Free Range Routing(FRR)](https://docs.ansible.com/ansible/latest/modules/frr_bgp_module.html#frr-bgp-module)
- [frr_facts – Collect facts from remote devices running Free Range Routing (FRR)](https://docs.ansible.com/ansible/latest/modules/frr_facts_module.html#frr-facts-module)



### Ftd

- [ftd_configuration – Manages configuration on Cisco FTD devices over REST API](https://docs.ansible.com/ansible/latest/modules/ftd_configuration_module.html#ftd-configuration-module)
- [ftd_file_download – Downloads files from Cisco FTD devices over HTTP(S)](https://docs.ansible.com/ansible/latest/modules/ftd_file_download_module.html#ftd-file-download-module)
- [ftd_file_upload – Uploads files to Cisco FTD devices over HTTP(S)](https://docs.ansible.com/ansible/latest/modules/ftd_file_upload_module.html#ftd-file-upload-module)
- [ftd_install – Installs FTD pkg image on the firewall](https://docs.ansible.com/ansible/latest/modules/ftd_install_module.html#ftd-install-module)



### Icx

- [icx_banner – Manage multiline banners on Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_banner_module.html#icx-banner-module)
- [icx_command – Run arbitrary commands on remote Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_command_module.html#icx-command-module)
- [icx_config – Manage configuration sections of Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_config_module.html#icx-config-module)
- [icx_copy – Transfer files from or to remote Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_copy_module.html#icx-copy-module)
- [icx_facts – Collect facts from remote Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_facts_module.html#icx-facts-module)
- [icx_interface – Manage Interface on Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_interface_module.html#icx-interface-module)
- [icx_l3_interface – Manage Layer-3 interfaces on Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_l3_interface_module.html#icx-l3-interface-module)
- [icx_linkagg – Manage link aggregation groups on Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_linkagg_module.html#icx-linkagg-module)
- [icx_lldp – Manage LLDP configuration on Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_lldp_module.html#icx-lldp-module)
- [icx_logging – Manage logging on Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_logging_module.html#icx-logging-module)
- [icx_ping – Tests reachability using ping from Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_ping_module.html#icx-ping-module)
- [icx_static_route – Manage static IP routes on Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_static_route_module.html#icx-static-route-module)
- [icx_system – Manage the system attributes on Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_system_module.html#icx-system-module)
- [icx_user – Manage the user accounts on Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_user_module.html#icx-user-module)
- [icx_vlan – Manage VLANs on Ruckus ICX 7000 series switches](https://docs.ansible.com/ansible/latest/modules/icx_vlan_module.html#icx-vlan-module)



### Illumos

- [dladm_etherstub – Manage etherstubs on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/dladm_etherstub_module.html#dladm-etherstub-module)
- [dladm_iptun – Manage IP tunnel interfaces on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/dladm_iptun_module.html#dladm-iptun-module)
- [dladm_linkprop – Manage link properties on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/dladm_linkprop_module.html#dladm-linkprop-module)
- [dladm_vlan – Manage VLAN interfaces on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/dladm_vlan_module.html#dladm-vlan-module)
- [dladm_vnic – Manage VNICs on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/dladm_vnic_module.html#dladm-vnic-module)
- [flowadm – Manage bandwidth resource control and priority for protocols, services and zones on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/flowadm_module.html#flowadm-module)
- [ipadm_addr – Manage IP addresses on an interface on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/ipadm_addr_module.html#ipadm-addr-module)
- [ipadm_addrprop – Manage IP address properties on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/ipadm_addrprop_module.html#ipadm-addrprop-module)
- [ipadm_if – Manage IP interfaces on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/ipadm_if_module.html#ipadm-if-module)
- [ipadm_ifprop – Manage IP interface properties on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/ipadm_ifprop_module.html#ipadm-ifprop-module)
- [ipadm_prop – Manage protocol properties on Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/ipadm_prop_module.html#ipadm-prop-module)



### Ingate

- [ig_config – Manage the configuration database on an Ingate SBC](https://docs.ansible.com/ansible/latest/modules/ig_config_module.html#ig-config-module)
- [ig_unit_information – Get unit information from an Ingate SBC](https://docs.ansible.com/ansible/latest/modules/ig_unit_information_module.html#ig-unit-information-module)



### Interface

- [net_interface – Manage Interface on network devices](https://docs.ansible.com/ansible/latest/modules/net_interface_module.html#net-interface-module) **(D)**
- [net_linkagg – Manage link aggregation groups on network devices](https://docs.ansible.com/ansible/latest/modules/net_linkagg_module.html#net-linkagg-module) **(D)**
- [net_lldp_interface – Manage LLDP interfaces configuration on network devices](https://docs.ansible.com/ansible/latest/modules/net_lldp_interface_module.html#net-lldp-interface-module) **(D)**



### Ios

- [ios_banner – Manage multiline banners on Cisco IOS devices](https://docs.ansible.com/ansible/latest/modules/ios_banner_module.html#ios-banner-module)
- [ios_bgp – Configure global BGP protocol settings on Cisco IOS](https://docs.ansible.com/ansible/latest/modules/ios_bgp_module.html#ios-bgp-module)
- [ios_command – Run commands on remote devices running Cisco IOS](https://docs.ansible.com/ansible/latest/modules/ios_command_module.html#ios-command-module)
- [ios_config – Manage Cisco IOS configuration sections](https://docs.ansible.com/ansible/latest/modules/ios_config_module.html#ios-config-module)
- [ios_facts – Collect facts from remote devices running Cisco IOS](https://docs.ansible.com/ansible/latest/modules/ios_facts_module.html#ios-facts-module)
- [ios_interface – Manage Interface on Cisco IOS network devices](https://docs.ansible.com/ansible/latest/modules/ios_interface_module.html#ios-interface-module) **(D)**
- [ios_interfaces – Manages interface attributes of Cisco IOS network devices](https://docs.ansible.com/ansible/latest/modules/ios_interfaces_module.html#ios-interfaces-module)
- [ios_l2_interface – Manage Layer-2 interface on Cisco IOS devices](https://docs.ansible.com/ansible/latest/modules/ios_l2_interface_module.html#ios-l2-interface-module) **(D)**
- [ios_l2_interfaces – Manage Layer-2 interface on Cisco IOS devices](https://docs.ansible.com/ansible/latest/modules/ios_l2_interfaces_module.html#ios-l2-interfaces-module)
- [ios_l3_interface – Manage Layer-3 interfaces on Cisco IOS network devices](https://docs.ansible.com/ansible/latest/modules/ios_l3_interface_module.html#ios-l3-interface-module) **(D)**
- [ios_l3_interfaces – Manage Layer-3 interface on Cisco IOS devices](https://docs.ansible.com/ansible/latest/modules/ios_l3_interfaces_module.html#ios-l3-interfaces-module)
- [ios_lacp – Manage Global Link Aggregation Control Protocol (LACP) on Cisco IOS devices](https://docs.ansible.com/ansible/latest/modules/ios_lacp_module.html#ios-lacp-module)
- [ios_lacp_interfaces – Manage Link Aggregation Control Protocol (LACP) on Cisco IOS devices interface](https://docs.ansible.com/ansible/latest/modules/ios_lacp_interfaces_module.html#ios-lacp-interfaces-module)
- [ios_lag_interfaces – Manage Link Aggregation on Cisco IOS devices](https://docs.ansible.com/ansible/latest/modules/ios_lag_interfaces_module.html#ios-lag-interfaces-module)
- [ios_linkagg – Manage link aggregation groups on Cisco IOS network devices](https://docs.ansible.com/ansible/latest/modules/ios_linkagg_module.html#ios-linkagg-module)
- [ios_lldp – Manage LLDP configuration on Cisco IOS network devices](https://docs.ansible.com/ansible/latest/modules/ios_lldp_module.html#ios-lldp-module)
- [ios_lldp_global – Configure and manage Link Layer Discovery Protocol(LLDP) attributes on IOS platforms](https://docs.ansible.com/ansible/latest/modules/ios_lldp_global_module.html#ios-lldp-global-module)
- [ios_lldp_interfaces – Manage link layer discovery protocol (LLDP) attributes of interfaces on Cisco IOS devices](https://docs.ansible.com/ansible/latest/modules/ios_lldp_interfaces_module.html#ios-lldp-interfaces-module)
- [ios_logging – Manage logging on network devices](https://docs.ansible.com/ansible/latest/modules/ios_logging_module.html#ios-logging-module)
- [ios_ntp – Manages core NTP configuration](https://docs.ansible.com/ansible/latest/modules/ios_ntp_module.html#ios-ntp-module)
- [ios_ping – Tests reachability using ping from Cisco IOS network devices](https://docs.ansible.com/ansible/latest/modules/ios_ping_module.html#ios-ping-module)
- [ios_static_route – Manage static IP routes on Cisco IOS network devices](https://docs.ansible.com/ansible/latest/modules/ios_static_route_module.html#ios-static-route-module)
- [ios_system – Manage the system attributes on Cisco IOS devices](https://docs.ansible.com/ansible/latest/modules/ios_system_module.html#ios-system-module)
- [ios_user – Manage the aggregate of local users on Cisco IOS device](https://docs.ansible.com/ansible/latest/modules/ios_user_module.html#ios-user-module)
- [ios_vlan – Manage VLANs on IOS network devices](https://docs.ansible.com/ansible/latest/modules/ios_vlan_module.html#ios-vlan-module) **(D)**
- [ios_vlans – Manage VLANs on Cisco IOS devices](https://docs.ansible.com/ansible/latest/modules/ios_vlans_module.html#ios-vlans-module)
- [ios_vrf – Manage the collection of VRF definitions on Cisco IOS devices](https://docs.ansible.com/ansible/latest/modules/ios_vrf_module.html#ios-vrf-module)



### Iosxr

- [iosxr_banner – Manage multiline banners on Cisco IOS XR devices](https://docs.ansible.com/ansible/latest/modules/iosxr_banner_module.html#iosxr-banner-module)
- [iosxr_bgp – Configure global BGP protocol settings on Cisco IOS-XR](https://docs.ansible.com/ansible/latest/modules/iosxr_bgp_module.html#iosxr-bgp-module)
- [iosxr_command – Run commands on remote devices running Cisco IOS XR](https://docs.ansible.com/ansible/latest/modules/iosxr_command_module.html#iosxr-command-module)
- [iosxr_config – Manage Cisco IOS XR configuration sections](https://docs.ansible.com/ansible/latest/modules/iosxr_config_module.html#iosxr-config-module)
- [iosxr_facts – Get facts about iosxr devices](https://docs.ansible.com/ansible/latest/modules/iosxr_facts_module.html#iosxr-facts-module)
- [iosxr_interface – Manage Interface on Cisco IOS XR network devices](https://docs.ansible.com/ansible/latest/modules/iosxr_interface_module.html#iosxr-interface-module) **(D)**
- [iosxr_interfaces – Manage interface attributes on Cisco IOS-XR network devices](https://docs.ansible.com/ansible/latest/modules/iosxr_interfaces_module.html#iosxr-interfaces-module)
- [iosxr_l2_interfaces – Manage Layer-2 interface on Cisco IOS-XR devices](https://docs.ansible.com/ansible/latest/modules/iosxr_l2_interfaces_module.html#iosxr-l2-interfaces-module)
- [iosxr_l3_interfaces – Manage Layer-3 interface on Cisco IOS-XR devices](https://docs.ansible.com/ansible/latest/modules/iosxr_l3_interfaces_module.html#iosxr-l3-interfaces-module)
- [iosxr_lacp – Manage Global Link Aggregation Control Protocol (LACP) on IOS-XR devices](https://docs.ansible.com/ansible/latest/modules/iosxr_lacp_module.html#iosxr-lacp-module)
- [iosxr_lacp_interfaces – Manage Link Aggregation Control Protocol (LACP) attributes of interfaces on IOS-XR devices](https://docs.ansible.com/ansible/latest/modules/iosxr_lacp_interfaces_module.html#iosxr-lacp-interfaces-module)
- [iosxr_lag_interfaces – Manages attributes of LAG/Ether-Bundle interfaces on IOS-XR devices](https://docs.ansible.com/ansible/latest/modules/iosxr_lag_interfaces_module.html#iosxr-lag-interfaces-module)
- [iosxr_lldp_global – Manage Global Link Layer Discovery Protocol (LLDP) settings on IOS-XR devices](https://docs.ansible.com/ansible/latest/modules/iosxr_lldp_global_module.html#iosxr-lldp-global-module)
- [iosxr_lldp_interfaces – Manage Link Layer Discovery Protocol (LLDP) attributes of interfaces on IOS-XR devices](https://docs.ansible.com/ansible/latest/modules/iosxr_lldp_interfaces_module.html#iosxr-lldp-interfaces-module)
- [iosxr_logging – Configuration management of system logging services on network devices](https://docs.ansible.com/ansible/latest/modules/iosxr_logging_module.html#iosxr-logging-module)
- [iosxr_netconf – Configures NetConf sub-system service on Cisco IOS-XR devices](https://docs.ansible.com/ansible/latest/modules/iosxr_netconf_module.html#iosxr-netconf-module)
- [iosxr_system – Manage the system attributes on Cisco IOS XR devices](https://docs.ansible.com/ansible/latest/modules/iosxr_system_module.html#iosxr-system-module)
- [iosxr_user – Manage the aggregate of local users on Cisco IOS XR device](https://docs.ansible.com/ansible/latest/modules/iosxr_user_module.html#iosxr-user-module)



### Ironware

- [ironware_command – Run arbitrary commands on Extreme IronWare devices](https://docs.ansible.com/ansible/latest/modules/ironware_command_module.html#ironware-command-module)
- [ironware_config – Manage configuration sections on Extreme Ironware devices](https://docs.ansible.com/ansible/latest/modules/ironware_config_module.html#ironware-config-module)
- [ironware_facts – Collect facts from devices running Extreme Ironware](https://docs.ansible.com/ansible/latest/modules/ironware_facts_module.html#ironware-facts-module)



### Itential

- [iap_start_workflow – Start a workflow in the Itential Automation Platform](https://docs.ansible.com/ansible/latest/modules/iap_start_workflow_module.html#iap-start-workflow-module)
- [iap_token – Get token for the Itential Automation Platform](https://docs.ansible.com/ansible/latest/modules/iap_token_module.html#iap-token-module)



### Junos

- [junos_banner – Manage multiline banners on Juniper JUNOS devices](https://docs.ansible.com/ansible/latest/modules/junos_banner_module.html#junos-banner-module)
- [junos_command – Run arbitrary commands on an Juniper JUNOS device](https://docs.ansible.com/ansible/latest/modules/junos_command_module.html#junos-command-module)
- [junos_config – Manage configuration on devices running Juniper JUNOS](https://docs.ansible.com/ansible/latest/modules/junos_config_module.html#junos-config-module)
- [junos_facts – Collect facts from remote devices running Juniper Junos](https://docs.ansible.com/ansible/latest/modules/junos_facts_module.html#junos-facts-module)
- [junos_interface – Manage Interface on Juniper JUNOS network devices](https://docs.ansible.com/ansible/latest/modules/junos_interface_module.html#junos-interface-module) **(D)**
- [junos_interfaces – Manages interface attributes of Juniper Junos OS network devices](https://docs.ansible.com/ansible/latest/modules/junos_interfaces_module.html#junos-interfaces-module)
- [junos_l2_interface – Manage Layer-2 interface on Juniper JUNOS network devices](https://docs.ansible.com/ansible/latest/modules/junos_l2_interface_module.html#junos-l2-interface-module) **(D)**
- [junos_l2_interfaces – Manage Layer-2 interface on Juniper JUNOS devices](https://docs.ansible.com/ansible/latest/modules/junos_l2_interfaces_module.html#junos-l2-interfaces-module)
- [junos_l3_interface – Manage L3 interfaces on Juniper JUNOS network devices](https://docs.ansible.com/ansible/latest/modules/junos_l3_interface_module.html#junos-l3-interface-module) **(D)**
- [junos_l3_interfaces – Manage Layer 3 interface on Juniper JUNOS devices](https://docs.ansible.com/ansible/latest/modules/junos_l3_interfaces_module.html#junos-l3-interfaces-module)
- [junos_lacp – Manage Global Link Aggregation Control Protocol (LACP) on Juniper Junos devices](https://docs.ansible.com/ansible/latest/modules/junos_lacp_module.html#junos-lacp-module)
- [junos_lacp_interfaces – Manage Link Aggregation Control Protocol (LACP) attributes of interfaces on Juniper JUNOS devices](https://docs.ansible.com/ansible/latest/modules/junos_lacp_interfaces_module.html#junos-lacp-interfaces-module)
- [junos_lag_interfaces – Manage Link Aggregation on Juniper JUNOS devices](https://docs.ansible.com/ansible/latest/modules/junos_lag_interfaces_module.html#junos-lag-interfaces-module)
- [junos_linkagg – Manage link aggregation groups on Juniper JUNOS network devices](https://docs.ansible.com/ansible/latest/modules/junos_linkagg_module.html#junos-linkagg-module) **(D)**
- [junos_lldp – Manage LLDP configuration on Juniper JUNOS network devices](https://docs.ansible.com/ansible/latest/modules/junos_lldp_module.html#junos-lldp-module) **(D)**
- [junos_lldp_global – Manage link layer discovery protocol (LLDP) attributes on Juniper JUNOS devices](https://docs.ansible.com/ansible/latest/modules/junos_lldp_global_module.html#junos-lldp-global-module)
- [junos_lldp_interface – Manage LLDP interfaces configuration on Juniper JUNOS network devices](https://docs.ansible.com/ansible/latest/modules/junos_lldp_interface_module.html#junos-lldp-interface-module) **(D)**
- [junos_lldp_interfaces – Manage link layer discovery protocol (LLDP) attributes of interfaces on Juniper JUNOS devices](https://docs.ansible.com/ansible/latest/modules/junos_lldp_interfaces_module.html#junos-lldp-interfaces-module)
- [junos_logging – Manage logging on network devices](https://docs.ansible.com/ansible/latest/modules/junos_logging_module.html#junos-logging-module)
- [junos_netconf – Configures the Junos Netconf system service](https://docs.ansible.com/ansible/latest/modules/junos_netconf_module.html#junos-netconf-module)
- [junos_package – Installs packages on remote devices running Junos](https://docs.ansible.com/ansible/latest/modules/junos_package_module.html#junos-package-module)
- [junos_ping – Tests reachability using ping from devices running Juniper JUNOS](https://docs.ansible.com/ansible/latest/modules/junos_ping_module.html#junos-ping-module)
- [junos_rpc – Runs an arbitrary RPC over NetConf on an Juniper JUNOS device](https://docs.ansible.com/ansible/latest/modules/junos_rpc_module.html#junos-rpc-module)
- [junos_scp – Transfer files from or to remote devices running Junos](https://docs.ansible.com/ansible/latest/modules/junos_scp_module.html#junos-scp-module)
- [junos_static_route – Manage static IP routes on Juniper JUNOS network devices](https://docs.ansible.com/ansible/latest/modules/junos_static_route_module.html#junos-static-route-module)
- [junos_system – Manage the system attributes on Juniper JUNOS devices](https://docs.ansible.com/ansible/latest/modules/junos_system_module.html#junos-system-module)
- [junos_user – Manage local user accounts on Juniper JUNOS devices](https://docs.ansible.com/ansible/latest/modules/junos_user_module.html#junos-user-module)
- [junos_vlan – Manage VLANs on Juniper JUNOS network devices](https://docs.ansible.com/ansible/latest/modules/junos_vlan_module.html#junos-vlan-module) **(D)**
- [junos_vlans – Create and manage VLAN configurations on Junos OS](https://docs.ansible.com/ansible/latest/modules/junos_vlans_module.html#junos-vlans-module)
- [junos_vrf – Manage the VRF definitions on Juniper JUNOS devices](https://docs.ansible.com/ansible/latest/modules/junos_vrf_module.html#junos-vrf-module)



### Layer2

- [net_l2_interface – Manage Layer-2 interface on network devices](https://docs.ansible.com/ansible/latest/modules/net_l2_interface_module.html#net-l2-interface-module) **(D)**
- [net_vlan – Manage VLANs on network devices](https://docs.ansible.com/ansible/latest/modules/net_vlan_module.html#net-vlan-module) **(D)**



### Layer3

- [net_l3_interface – Manage L3 interfaces on network devices](https://docs.ansible.com/ansible/latest/modules/net_l3_interface_module.html#net-l3-interface-module) **(D)**
- [net_vrf – Manage VRFs on network devices](https://docs.ansible.com/ansible/latest/modules/net_vrf_module.html#net-vrf-module) **(D)**



### Meraki

- [meraki_admin – Manage administrators in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_admin_module.html#meraki-admin-module)
- [meraki_config_template – Manage configuration templates in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_config_template_module.html#meraki-config-template-module)
- [meraki_content_filtering – Edit Meraki MX content filtering policies](https://docs.ansible.com/ansible/latest/modules/meraki_content_filtering_module.html#meraki-content-filtering-module)
- [meraki_device – Manage devices in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_device_module.html#meraki-device-module)
- [meraki_firewalled_services – Edit firewall policies for administrative network services](https://docs.ansible.com/ansible/latest/modules/meraki_firewalled_services_module.html#meraki-firewalled-services-module)
- [meraki_malware – Manage Malware Protection in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_malware_module.html#meraki-malware-module)
- [meraki_mr_l3_firewall – Manage MR access point layer 3 firewalls in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_mr_l3_firewall_module.html#meraki-mr-l3-firewall-module)
- [meraki_mx_l3_firewall – Manage MX appliance layer 3 firewalls in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_mx_l3_firewall_module.html#meraki-mx-l3-firewall-module)
- [meraki_mx_l7_firewall – Manage MX appliance layer 7 firewalls in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_mx_l7_firewall_module.html#meraki-mx-l7-firewall-module)
- [meraki_nat – Manage NAT rules in Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_nat_module.html#meraki-nat-module)
- [meraki_network – Manage networks in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_network_module.html#meraki-network-module)
- [meraki_organization – Manage organizations in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_organization_module.html#meraki-organization-module)
- [meraki_snmp – Manage organizations in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_snmp_module.html#meraki-snmp-module)
- [meraki_ssid – Manage wireless SSIDs in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_ssid_module.html#meraki-ssid-module)
- [meraki_static_route – Manage static routes in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_static_route_module.html#meraki-static-route-module)
- [meraki_switchport – Manage switchports on a switch in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_switchport_module.html#meraki-switchport-module)
- [meraki_syslog – Manage syslog server settings in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_syslog_module.html#meraki-syslog-module)
- [meraki_vlan – Manage VLANs in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_vlan_module.html#meraki-vlan-module)
- [meraki_webhook – Manage webhooks configured in the Meraki cloud](https://docs.ansible.com/ansible/latest/modules/meraki_webhook_module.html#meraki-webhook-module)



### Netact

- [netact_cm_command – Manage network configuration data in Nokia Core and Radio networks](https://docs.ansible.com/ansible/latest/modules/netact_cm_command_module.html#netact-cm-command-module)



### Netconf

- [netconf_config – netconf device configuration](https://docs.ansible.com/ansible/latest/modules/netconf_config_module.html#netconf-config-module)
- [netconf_get – Fetch configuration/state data from NETCONF enabled network devices](https://docs.ansible.com/ansible/latest/modules/netconf_get_module.html#netconf-get-module)
- [netconf_rpc – Execute operations on NETCONF enabled network devices](https://docs.ansible.com/ansible/latest/modules/netconf_rpc_module.html#netconf-rpc-module)



### Netscaler

- [netscaler_cs_action – Manage content switching actions](https://docs.ansible.com/ansible/latest/modules/netscaler_cs_action_module.html#netscaler-cs-action-module)
- [netscaler_cs_policy – Manage content switching policy](https://docs.ansible.com/ansible/latest/modules/netscaler_cs_policy_module.html#netscaler-cs-policy-module)
- [netscaler_cs_vserver – Manage content switching vserver](https://docs.ansible.com/ansible/latest/modules/netscaler_cs_vserver_module.html#netscaler-cs-vserver-module)
- [netscaler_gslb_service – Manage gslb service entities in Netscaler](https://docs.ansible.com/ansible/latest/modules/netscaler_gslb_service_module.html#netscaler-gslb-service-module)
- [netscaler_gslb_site – Manage gslb site entities in Netscaler](https://docs.ansible.com/ansible/latest/modules/netscaler_gslb_site_module.html#netscaler-gslb-site-module)
- [netscaler_gslb_vserver – Configure gslb vserver entities in Netscaler](https://docs.ansible.com/ansible/latest/modules/netscaler_gslb_vserver_module.html#netscaler-gslb-vserver-module)
- [netscaler_lb_monitor – Manage load balancing monitors](https://docs.ansible.com/ansible/latest/modules/netscaler_lb_monitor_module.html#netscaler-lb-monitor-module)
- [netscaler_lb_vserver – Manage load balancing vserver configuration](https://docs.ansible.com/ansible/latest/modules/netscaler_lb_vserver_module.html#netscaler-lb-vserver-module)
- [netscaler_nitro_request – Issue Nitro API requests to a Netscaler instance](https://docs.ansible.com/ansible/latest/modules/netscaler_nitro_request_module.html#netscaler-nitro-request-module)
- [netscaler_save_config – Save Netscaler configuration](https://docs.ansible.com/ansible/latest/modules/netscaler_save_config_module.html#netscaler-save-config-module)
- [netscaler_server – Manage server configuration](https://docs.ansible.com/ansible/latest/modules/netscaler_server_module.html#netscaler-server-module)
- [netscaler_service – Manage service configuration in Netscaler](https://docs.ansible.com/ansible/latest/modules/netscaler_service_module.html#netscaler-service-module)
- [netscaler_servicegroup – Manage service group configuration in Netscaler](https://docs.ansible.com/ansible/latest/modules/netscaler_servicegroup_module.html#netscaler-servicegroup-module)
- [netscaler_ssl_certkey – Manage ssl certificate keys](https://docs.ansible.com/ansible/latest/modules/netscaler_ssl_certkey_module.html#netscaler-ssl-certkey-module)



### Netvisor

- [pn_access_list – CLI command to create/delete access-list](https://docs.ansible.com/ansible/latest/modules/pn_access_list_module.html#pn-access-list-module)
- [pn_access_list_ip – CLI command to add/remove access-list-ip](https://docs.ansible.com/ansible/latest/modules/pn_access_list_ip_module.html#pn-access-list-ip-module)
- [pn_admin_service – CLI command to modify admin-service](https://docs.ansible.com/ansible/latest/modules/pn_admin_service_module.html#pn-admin-service-module)
- [pn_admin_session_timeout – CLI command to modify admin-session-timeout](https://docs.ansible.com/ansible/latest/modules/pn_admin_session_timeout_module.html#pn-admin-session-timeout-module)
- [pn_admin_syslog – CLI command to create/modify/delete admin-syslog](https://docs.ansible.com/ansible/latest/modules/pn_admin_syslog_module.html#pn-admin-syslog-module)
- [pn_cluster – CLI command to create/delete a cluster](https://docs.ansible.com/ansible/latest/modules/pn_cluster_module.html#pn-cluster-module) **(D)**
- [pn_connection_stats_settings – CLI command to modify connection-stats-settings](https://docs.ansible.com/ansible/latest/modules/pn_connection_stats_settings_module.html#pn-connection-stats-settings-module)
- [pn_cpu_class – CLI command to create/modify/delete cpu-class](https://docs.ansible.com/ansible/latest/modules/pn_cpu_class_module.html#pn-cpu-class-module)
- [pn_cpu_mgmt_class – CLI command to modify cpu-mgmt-class](https://docs.ansible.com/ansible/latest/modules/pn_cpu_mgmt_class_module.html#pn-cpu-mgmt-class-module)
- [pn_dhcp_filter – CLI command to create/modify/delete dhcp-filter](https://docs.ansible.com/ansible/latest/modules/pn_dhcp_filter_module.html#pn-dhcp-filter-module)
- [pn_dscp_map – CLI command to create/delete dscp-map](https://docs.ansible.com/ansible/latest/modules/pn_dscp_map_module.html#pn-dscp-map-module)
- [pn_dscp_map_pri_map – CLI command to modify dscp-map-pri-map](https://docs.ansible.com/ansible/latest/modules/pn_dscp_map_pri_map_module.html#pn-dscp-map-pri-map-module)
- [pn_fabric_local – CLI command to modify fabric-local](https://docs.ansible.com/ansible/latest/modules/pn_fabric_local_module.html#pn-fabric-local-module)
- [pn_igmp_snooping – CLI command to modify igmp-snooping](https://docs.ansible.com/ansible/latest/modules/pn_igmp_snooping_module.html#pn-igmp-snooping-module)
- [pn_ipv6security_raguard – CLI command to create/modify/delete ipv6security-raguard](https://docs.ansible.com/ansible/latest/modules/pn_ipv6security_raguard_module.html#pn-ipv6security-raguard-module)
- [pn_ipv6security_raguard_port – CLI command to add/remove ipv6security-raguard-port](https://docs.ansible.com/ansible/latest/modules/pn_ipv6security_raguard_port_module.html#pn-ipv6security-raguard-port-module)
- [pn_ipv6security_raguard_vlan – CLI command to add/remove ipv6security-raguard-vlan](https://docs.ansible.com/ansible/latest/modules/pn_ipv6security_raguard_vlan_module.html#pn-ipv6security-raguard-vlan-module)
- [pn_log_audit_exception – CLI command to create/delete an audit exception](https://docs.ansible.com/ansible/latest/modules/pn_log_audit_exception_module.html#pn-log-audit-exception-module)
- [pn_ospf – CLI command to add/remove ospf protocol to a vRouter](https://docs.ansible.com/ansible/latest/modules/pn_ospf_module.html#pn-ospf-module) **(D)**
- [pn_ospfarea – CLI command to add/remove ospf area to/from a vrouter](https://docs.ansible.com/ansible/latest/modules/pn_ospfarea_module.html#pn-ospfarea-module) **(D)**
- [pn_port_config – CLI command to modify port-config](https://docs.ansible.com/ansible/latest/modules/pn_port_config_module.html#pn-port-config-module)
- [pn_port_cos_bw – CLI command to modify port-cos-bw](https://docs.ansible.com/ansible/latest/modules/pn_port_cos_bw_module.html#pn-port-cos-bw-module)
- [pn_port_cos_rate_setting – CLI command to modify port-cos-rate-setting](https://docs.ansible.com/ansible/latest/modules/pn_port_cos_rate_setting_module.html#pn-port-cos-rate-setting-module)
- [pn_prefix_list – CLI command to create/delete prefix-list](https://docs.ansible.com/ansible/latest/modules/pn_prefix_list_module.html#pn-prefix-list-module)
- [pn_prefix_list_network – CLI command to add/remove prefix-list-network](https://docs.ansible.com/ansible/latest/modules/pn_prefix_list_network_module.html#pn-prefix-list-network-module)
- [pn_role – CLI command to create/delete/modify role](https://docs.ansible.com/ansible/latest/modules/pn_role_module.html#pn-role-module)
- [pn_show – Run show commands on nvOS device](https://docs.ansible.com/ansible/latest/modules/pn_show_module.html#pn-show-module) **(D)**
- [pn_snmp_community – CLI command to create/modify/delete snmp-community](https://docs.ansible.com/ansible/latest/modules/pn_snmp_community_module.html#pn-snmp-community-module)
- [pn_snmp_trap_sink – CLI command to create/delete snmp-trap-sink](https://docs.ansible.com/ansible/latest/modules/pn_snmp_trap_sink_module.html#pn-snmp-trap-sink-module)
- [pn_snmp_vacm – CLI command to create/modify/delete snmp-vacm](https://docs.ansible.com/ansible/latest/modules/pn_snmp_vacm_module.html#pn-snmp-vacm-module)
- [pn_stp – CLI command to modify stp](https://docs.ansible.com/ansible/latest/modules/pn_stp_module.html#pn-stp-module)
- [pn_stp_port – CLI command to modify stp-port](https://docs.ansible.com/ansible/latest/modules/pn_stp_port_module.html#pn-stp-port-module)
- [pn_switch_setup – CLI command to modify switch-setup](https://docs.ansible.com/ansible/latest/modules/pn_switch_setup_module.html#pn-switch-setup-module)
- [pn_trunk – CLI command to create/delete/modify a trunk](https://docs.ansible.com/ansible/latest/modules/pn_trunk_module.html#pn-trunk-module) **(D)**
- [pn_user – CLI command to create/modify/delete user](https://docs.ansible.com/ansible/latest/modules/pn_user_module.html#pn-user-module)
- [pn_vflow_table_profile – CLI command to modify vflow-table-profile](https://docs.ansible.com/ansible/latest/modules/pn_vflow_table_profile_module.html#pn-vflow-table-profile-module)
- [pn_vlag – CLI command to create/delete/modify vlag](https://docs.ansible.com/ansible/latest/modules/pn_vlag_module.html#pn-vlag-module) **(D)**
- [pn_vlan – CLI command to create/delete a VLAN](https://docs.ansible.com/ansible/latest/modules/pn_vlan_module.html#pn-vlan-module) **(D)**
- [pn_vrouter – CLI command to create/delete/modify a vrouter](https://docs.ansible.com/ansible/latest/modules/pn_vrouter_module.html#pn-vrouter-module) **(D)**
- [pn_vrouter_bgp – CLI command to add/modify/remove vrouter-bgp](https://docs.ansible.com/ansible/latest/modules/pn_vrouter_bgp_module.html#pn-vrouter-bgp-module)
- [pn_vrouter_bgp_network – CLI command to add/remove vrouter-bgp-network](https://docs.ansible.com/ansible/latest/modules/pn_vrouter_bgp_network_module.html#pn-vrouter-bgp-network-module)
- [pn_vrouter_interface_ip – CLI command to add/remove vrouter-interface-ip](https://docs.ansible.com/ansible/latest/modules/pn_vrouter_interface_ip_module.html#pn-vrouter-interface-ip-module)
- [pn_vrouter_loopback_interface – CLI command to add/remove vrouter-loopback-interface](https://docs.ansible.com/ansible/latest/modules/pn_vrouter_loopback_interface_module.html#pn-vrouter-loopback-interface-module)
- [pn_vrouter_ospf – CLI command to add/remove vrouter-ospf](https://docs.ansible.com/ansible/latest/modules/pn_vrouter_ospf_module.html#pn-vrouter-ospf-module)
- [pn_vrouter_ospf6 – CLI command to add/remove vrouter-ospf6](https://docs.ansible.com/ansible/latest/modules/pn_vrouter_ospf6_module.html#pn-vrouter-ospf6-module)
- [pn_vrouter_packet_relay – CLI command to add/remove vrouter-packet-relay](https://docs.ansible.com/ansible/latest/modules/pn_vrouter_packet_relay_module.html#pn-vrouter-packet-relay-module)
- [pn_vrouter_pim_config – CLI command to modify vrouter-pim-config](https://docs.ansible.com/ansible/latest/modules/pn_vrouter_pim_config_module.html#pn-vrouter-pim-config-module)
- [pn_vrouterbgp – CLI command to add/remove/modify vrouter-bgp](https://docs.ansible.com/ansible/latest/modules/pn_vrouterbgp_module.html#pn-vrouterbgp-module) **(D)**
- [pn_vrouterif – CLI command to add/remove/modify vrouter-interface](https://docs.ansible.com/ansible/latest/modules/pn_vrouterif_module.html#pn-vrouterif-module) **(D)**
- [pn_vrouterlbif – CLI command to add/remove vrouter-loopback-interface](https://docs.ansible.com/ansible/latest/modules/pn_vrouterlbif_module.html#pn-vrouterlbif-module) **(D)**
- [pn_vtep – CLI command to create/delete vtep](https://docs.ansible.com/ansible/latest/modules/pn_vtep_module.html#pn-vtep-module)



### Nos

- [nos_command – Run commands on remote devices running Extreme Networks NOS](https://docs.ansible.com/ansible/latest/modules/nos_command_module.html#nos-command-module)
- [nos_config – Manage Extreme Networks NOS configuration sections](https://docs.ansible.com/ansible/latest/modules/nos_config_module.html#nos-config-module)
- [nos_facts – Collect facts from devices running Extreme NOS](https://docs.ansible.com/ansible/latest/modules/nos_facts_module.html#nos-facts-module)



### Nso

- [nso_action – Executes Cisco NSO actions and verifies output](https://docs.ansible.com/ansible/latest/modules/nso_action_module.html#nso-action-module)
- [nso_config – Manage Cisco NSO configuration and service synchronization](https://docs.ansible.com/ansible/latest/modules/nso_config_module.html#nso-config-module)
- [nso_query – Query data from Cisco NSO](https://docs.ansible.com/ansible/latest/modules/nso_query_module.html#nso-query-module)
- [nso_show – Displays data from Cisco NSO](https://docs.ansible.com/ansible/latest/modules/nso_show_module.html#nso-show-module)
- [nso_verify – Verifies Cisco NSO configuration](https://docs.ansible.com/ansible/latest/modules/nso_verify_module.html#nso-verify-module)



### Nuage

- [nuage_vspk – Manage Nuage VSP environments](https://docs.ansible.com/ansible/latest/modules/nuage_vspk_module.html#nuage-vspk-module)



### Nxos

- [nxos_aaa_server – Manages AAA server global configuration](https://docs.ansible.com/ansible/latest/modules/nxos_aaa_server_module.html#nxos-aaa-server-module)
- [nxos_aaa_server_host – Manages AAA server host-specific configuration](https://docs.ansible.com/ansible/latest/modules/nxos_aaa_server_host_module.html#nxos-aaa-server-host-module)
- [nxos_acl – Manages access list entries for ACLs](https://docs.ansible.com/ansible/latest/modules/nxos_acl_module.html#nxos-acl-module)
- [nxos_acl_interface – Manages applying ACLs to interfaces](https://docs.ansible.com/ansible/latest/modules/nxos_acl_interface_module.html#nxos-acl-interface-module)
- [nxos_banner – Manage multiline banners on Cisco NXOS devices](https://docs.ansible.com/ansible/latest/modules/nxos_banner_module.html#nxos-banner-module)
- [nxos_bfd_global – Bidirectional Forwarding Detection (BFD) global-level configuration](https://docs.ansible.com/ansible/latest/modules/nxos_bfd_global_module.html#nxos-bfd-global-module)
- [nxos_bfd_interfaces – Manages BFD attributes of nxos interfaces](https://docs.ansible.com/ansible/latest/modules/nxos_bfd_interfaces_module.html#nxos-bfd-interfaces-module)
- [nxos_bgp – Manages BGP configuration](https://docs.ansible.com/ansible/latest/modules/nxos_bgp_module.html#nxos-bgp-module)
- [nxos_bgp_af – Manages BGP Address-family configuration](https://docs.ansible.com/ansible/latest/modules/nxos_bgp_af_module.html#nxos-bgp-af-module)
- [nxos_bgp_neighbor – Manages BGP neighbors configurations](https://docs.ansible.com/ansible/latest/modules/nxos_bgp_neighbor_module.html#nxos-bgp-neighbor-module)
- [nxos_bgp_neighbor_af – Manages BGP address-family’s neighbors configuration](https://docs.ansible.com/ansible/latest/modules/nxos_bgp_neighbor_af_module.html#nxos-bgp-neighbor-af-module)
- [nxos_command – Run arbitrary command on Cisco NXOS devices](https://docs.ansible.com/ansible/latest/modules/nxos_command_module.html#nxos-command-module)
- [nxos_config – Manage Cisco NXOS configuration sections](https://docs.ansible.com/ansible/latest/modules/nxos_config_module.html#nxos-config-module)
- [nxos_evpn_global – Handles the EVPN control plane for VXLAN](https://docs.ansible.com/ansible/latest/modules/nxos_evpn_global_module.html#nxos-evpn-global-module)
- [nxos_evpn_vni – Manages Cisco EVPN VXLAN Network Identifier (VNI)](https://docs.ansible.com/ansible/latest/modules/nxos_evpn_vni_module.html#nxos-evpn-vni-module)
- [nxos_facts – Gets facts about NX-OS switches](https://docs.ansible.com/ansible/latest/modules/nxos_facts_module.html#nxos-facts-module)
- [nxos_feature – Manage features in NX-OS switches](https://docs.ansible.com/ansible/latest/modules/nxos_feature_module.html#nxos-feature-module)
- [nxos_file_copy – Copy a file to a remote NXOS device](https://docs.ansible.com/ansible/latest/modules/nxos_file_copy_module.html#nxos-file-copy-module)
- [nxos_gir – Trigger a graceful removal or insertion (GIR) of the switch](https://docs.ansible.com/ansible/latest/modules/nxos_gir_module.html#nxos-gir-module)
- [nxos_gir_profile_management – Create a maintenance-mode or normal-mode profile for GIR](https://docs.ansible.com/ansible/latest/modules/nxos_gir_profile_management_module.html#nxos-gir-profile-management-module)
- [nxos_hsrp – Manages HSRP configuration on NX-OS switches](https://docs.ansible.com/ansible/latest/modules/nxos_hsrp_module.html#nxos-hsrp-module)
- [nxos_igmp – Manages IGMP global configuration](https://docs.ansible.com/ansible/latest/modules/nxos_igmp_module.html#nxos-igmp-module)
- [nxos_igmp_interface – Manages IGMP interface configuration](https://docs.ansible.com/ansible/latest/modules/nxos_igmp_interface_module.html#nxos-igmp-interface-module)
- [nxos_igmp_snooping – Manages IGMP snooping global configuration](https://docs.ansible.com/ansible/latest/modules/nxos_igmp_snooping_module.html#nxos-igmp-snooping-module)
- [nxos_install_os – Set boot options like boot, kickstart image and issu](https://docs.ansible.com/ansible/latest/modules/nxos_install_os_module.html#nxos-install-os-module)
- [nxos_interface – Manages physical attributes of interfaces](https://docs.ansible.com/ansible/latest/modules/nxos_interface_module.html#nxos-interface-module) **(D)**
- [nxos_interface_ospf – Manages configuration of an OSPF interface instance](https://docs.ansible.com/ansible/latest/modules/nxos_interface_ospf_module.html#nxos-interface-ospf-module)
- [nxos_interfaces – Manages interface attributes of NX-OS Interfaces](https://docs.ansible.com/ansible/latest/modules/nxos_interfaces_module.html#nxos-interfaces-module)
- [nxos_l2_interface – Manage Layer-2 interface on Cisco NXOS devices](https://docs.ansible.com/ansible/latest/modules/nxos_l2_interface_module.html#nxos-l2-interface-module) **(D)**
- [nxos_l2_interfaces – Manages Layer-2 Interfaces attributes of NX-OS Interfaces](https://docs.ansible.com/ansible/latest/modules/nxos_l2_interfaces_module.html#nxos-l2-interfaces-module)
- [nxos_l3_interface – Manage L3 interfaces on Cisco NXOS network devices](https://docs.ansible.com/ansible/latest/modules/nxos_l3_interface_module.html#nxos-l3-interface-module) **(D)**
- [nxos_l3_interfaces – Manages Layer-3 Interfaces attributes of NX-OS Interfaces](https://docs.ansible.com/ansible/latest/modules/nxos_l3_interfaces_module.html#nxos-l3-interfaces-module)
- [nxos_lacp – Manage Global Link Aggregation Control Protocol (LACP) on Cisco NX-OS devices](https://docs.ansible.com/ansible/latest/modules/nxos_lacp_module.html#nxos-lacp-module)
- [nxos_lacp_interfaces – Manage Link Aggregation Control Protocol (LACP) attributes of interfaces on Cisco NX-OS devices](https://docs.ansible.com/ansible/latest/modules/nxos_lacp_interfaces_module.html#nxos-lacp-interfaces-module)
- [nxos_lag_interfaces – Manages link aggregation groups of NX-OS Interfaces](https://docs.ansible.com/ansible/latest/modules/nxos_lag_interfaces_module.html#nxos-lag-interfaces-module)
- [nxos_linkagg – Manage link aggregation groups on Cisco NXOS devices](https://docs.ansible.com/ansible/latest/modules/nxos_linkagg_module.html#nxos-linkagg-module) **(D)**
- [nxos_lldp – Manage LLDP configuration on Cisco NXOS network devices](https://docs.ansible.com/ansible/latest/modules/nxos_lldp_module.html#nxos-lldp-module)
- [nxos_lldp_global – Configure and manage Link Layer Discovery Protocol(LLDP) attributes on NX-OS platforms](https://docs.ansible.com/ansible/latest/modules/nxos_lldp_global_module.html#nxos-lldp-global-module)
- [nxos_logging – Manage logging on network devices](https://docs.ansible.com/ansible/latest/modules/nxos_logging_module.html#nxos-logging-module)
- [nxos_ntp – Manages core NTP configuration](https://docs.ansible.com/ansible/latest/modules/nxos_ntp_module.html#nxos-ntp-module)
- [nxos_ntp_auth – Manages NTP authentication](https://docs.ansible.com/ansible/latest/modules/nxos_ntp_auth_module.html#nxos-ntp-auth-module)
- [nxos_ntp_options – Manages NTP options](https://docs.ansible.com/ansible/latest/modules/nxos_ntp_options_module.html#nxos-ntp-options-module)
- [nxos_nxapi – Manage NXAPI configuration on an NXOS device](https://docs.ansible.com/ansible/latest/modules/nxos_nxapi_module.html#nxos-nxapi-module)
- [nxos_ospf – Manages configuration of an ospf instance](https://docs.ansible.com/ansible/latest/modules/nxos_ospf_module.html#nxos-ospf-module)
- [nxos_ospf_vrf – Manages a VRF for an OSPF router](https://docs.ansible.com/ansible/latest/modules/nxos_ospf_vrf_module.html#nxos-ospf-vrf-module)
- [nxos_overlay_global – Configures anycast gateway MAC of the switch](https://docs.ansible.com/ansible/latest/modules/nxos_overlay_global_module.html#nxos-overlay-global-module)
- [nxos_pim – Manages configuration of a PIM instance](https://docs.ansible.com/ansible/latest/modules/nxos_pim_module.html#nxos-pim-module)
- [nxos_pim_interface – Manages PIM interface configuration](https://docs.ansible.com/ansible/latest/modules/nxos_pim_interface_module.html#nxos-pim-interface-module)
- [nxos_pim_rp_address – Manages configuration of an PIM static RP address instance](https://docs.ansible.com/ansible/latest/modules/nxos_pim_rp_address_module.html#nxos-pim-rp-address-module)
- [nxos_ping – Tests reachability using ping from Nexus switch](https://docs.ansible.com/ansible/latest/modules/nxos_ping_module.html#nxos-ping-module)
- [nxos_reboot – Reboot a network device](https://docs.ansible.com/ansible/latest/modules/nxos_reboot_module.html#nxos-reboot-module)
- [nxos_rollback – Set a checkpoint or rollback to a checkpoint](https://docs.ansible.com/ansible/latest/modules/nxos_rollback_module.html#nxos-rollback-module)
- [nxos_rpm – Install patch or feature rpms on Cisco NX-OS devices](https://docs.ansible.com/ansible/latest/modules/nxos_rpm_module.html#nxos-rpm-module)
- [nxos_smu – Perform SMUs on Cisco NX-OS devices](https://docs.ansible.com/ansible/latest/modules/nxos_smu_module.html#nxos-smu-module)
- [nxos_snapshot – Manage snapshots of the running states of selected features](https://docs.ansible.com/ansible/latest/modules/nxos_snapshot_module.html#nxos-snapshot-module)
- [nxos_snmp_community – Manages SNMP community configs](https://docs.ansible.com/ansible/latest/modules/nxos_snmp_community_module.html#nxos-snmp-community-module)
- [nxos_snmp_contact – Manages SNMP contact info](https://docs.ansible.com/ansible/latest/modules/nxos_snmp_contact_module.html#nxos-snmp-contact-module)
- [nxos_snmp_host – Manages SNMP host configuration](https://docs.ansible.com/ansible/latest/modules/nxos_snmp_host_module.html#nxos-snmp-host-module)
- [nxos_snmp_location – Manages SNMP location information](https://docs.ansible.com/ansible/latest/modules/nxos_snmp_location_module.html#nxos-snmp-location-module)
- [nxos_snmp_traps – Manages SNMP traps](https://docs.ansible.com/ansible/latest/modules/nxos_snmp_traps_module.html#nxos-snmp-traps-module)
- [nxos_snmp_user – Manages SNMP users for monitoring](https://docs.ansible.com/ansible/latest/modules/nxos_snmp_user_module.html#nxos-snmp-user-module)
- [nxos_static_route – Manages static route configuration](https://docs.ansible.com/ansible/latest/modules/nxos_static_route_module.html#nxos-static-route-module)
- [nxos_system – Manage the system attributes on Cisco NXOS devices](https://docs.ansible.com/ansible/latest/modules/nxos_system_module.html#nxos-system-module)
- [nxos_telemetry – Telemetry Monitoring Service (TMS) configuration](https://docs.ansible.com/ansible/latest/modules/nxos_telemetry_module.html#nxos-telemetry-module)
- [nxos_udld – Manages UDLD global configuration params](https://docs.ansible.com/ansible/latest/modules/nxos_udld_module.html#nxos-udld-module)
- [nxos_udld_interface – Manages UDLD interface configuration params](https://docs.ansible.com/ansible/latest/modules/nxos_udld_interface_module.html#nxos-udld-interface-module)
- [nxos_user – Manage the collection of local users on Nexus devices](https://docs.ansible.com/ansible/latest/modules/nxos_user_module.html#nxos-user-module)
- [nxos_vlan – Manages VLAN resources and attributes](https://docs.ansible.com/ansible/latest/modules/nxos_vlan_module.html#nxos-vlan-module) **(D)**
- [nxos_vlans – Create VLAN and manage VLAN configurations on NX-OS Interfaces](https://docs.ansible.com/ansible/latest/modules/nxos_vlans_module.html#nxos-vlans-module)
- [nxos_vpc – Manages global VPC configuration](https://docs.ansible.com/ansible/latest/modules/nxos_vpc_module.html#nxos-vpc-module)
- [nxos_vpc_interface – Manages interface VPC configuration](https://docs.ansible.com/ansible/latest/modules/nxos_vpc_interface_module.html#nxos-vpc-interface-module)
- [nxos_vrf – Manages global VRF configuration](https://docs.ansible.com/ansible/latest/modules/nxos_vrf_module.html#nxos-vrf-module)
- [nxos_vrf_af – Manages VRF AF](https://docs.ansible.com/ansible/latest/modules/nxos_vrf_af_module.html#nxos-vrf-af-module)
- [nxos_vrf_interface – Manages interface specific VRF configuration](https://docs.ansible.com/ansible/latest/modules/nxos_vrf_interface_module.html#nxos-vrf-interface-module)
- [nxos_vrrp – Manages VRRP configuration on NX-OS switches](https://docs.ansible.com/ansible/latest/modules/nxos_vrrp_module.html#nxos-vrrp-module)
- [nxos_vtp_domain – Manages VTP domain configuration](https://docs.ansible.com/ansible/latest/modules/nxos_vtp_domain_module.html#nxos-vtp-domain-module)
- [nxos_vtp_password – Manages VTP password configuration](https://docs.ansible.com/ansible/latest/modules/nxos_vtp_password_module.html#nxos-vtp-password-module)
- [nxos_vtp_version – Manages VTP version configuration](https://docs.ansible.com/ansible/latest/modules/nxos_vtp_version_module.html#nxos-vtp-version-module)
- [nxos_vxlan_vtep – Manages VXLAN Network Virtualization Endpoint (NVE)](https://docs.ansible.com/ansible/latest/modules/nxos_vxlan_vtep_module.html#nxos-vxlan-vtep-module)
- [nxos_vxlan_vtep_vni – Creates a Virtual Network Identifier member (VNI)](https://docs.ansible.com/ansible/latest/modules/nxos_vxlan_vtep_vni_module.html#nxos-vxlan-vtep-vni-module)



### Onyx

- [onyx_bgp – Configures BGP on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_bgp_module.html#onyx-bgp-module)
- [onyx_buffer_pool – Configures Buffer Pool](https://docs.ansible.com/ansible/latest/modules/onyx_buffer_pool_module.html#onyx-buffer-pool-module)
- [onyx_command – Run commands on remote devices running Mellanox ONYX](https://docs.ansible.com/ansible/latest/modules/onyx_command_module.html#onyx-command-module)
- [onyx_config – Manage Mellanox ONYX configuration sections](https://docs.ansible.com/ansible/latest/modules/onyx_config_module.html#onyx-config-module)
- [onyx_facts – Collect facts from Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_facts_module.html#onyx-facts-module)
- [onyx_igmp – Configures IGMP global parameters](https://docs.ansible.com/ansible/latest/modules/onyx_igmp_module.html#onyx-igmp-module)
- [onyx_igmp_interface – Configures IGMP interface parameters](https://docs.ansible.com/ansible/latest/modules/onyx_igmp_interface_module.html#onyx-igmp-interface-module)
- [onyx_igmp_vlan – Configures IGMP Vlan parameters](https://docs.ansible.com/ansible/latest/modules/onyx_igmp_vlan_module.html#onyx-igmp-vlan-module)
- [onyx_interface – Manage Interfaces on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_interface_module.html#onyx-interface-module)
- [onyx_l2_interface – Manage Layer-2 interface on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_l2_interface_module.html#onyx-l2-interface-module)
- [onyx_l3_interface – Manage L3 interfaces on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_l3_interface_module.html#onyx-l3-interface-module)
- [onyx_linkagg – Manage link aggregation groups on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_linkagg_module.html#onyx-linkagg-module)
- [onyx_lldp – Manage LLDP configuration on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_lldp_module.html#onyx-lldp-module)
- [onyx_lldp_interface – Manage LLDP interfaces configuration on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_lldp_interface_module.html#onyx-lldp-interface-module)
- [onyx_magp – Manage MAGP protocol on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_magp_module.html#onyx-magp-module)
- [onyx_mlag_ipl – Manage IPL (inter-peer link) on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_mlag_ipl_module.html#onyx-mlag-ipl-module)
- [onyx_mlag_vip – Configures MLAG VIP on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_mlag_vip_module.html#onyx-mlag-vip-module)
- [onyx_ospf – Manage OSPF protocol on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_ospf_module.html#onyx-ospf-module)
- [onyx_pfc_interface – Manage priority flow control on ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_pfc_interface_module.html#onyx-pfc-interface-module)
- [onyx_protocol – Enables/Disables protocols on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_protocol_module.html#onyx-protocol-module)
- [onyx_ptp_global – Configures PTP Global parameters](https://docs.ansible.com/ansible/latest/modules/onyx_ptp_global_module.html#onyx-ptp-global-module)
- [onyx_ptp_interface – Configures PTP on interface](https://docs.ansible.com/ansible/latest/modules/onyx_ptp_interface_module.html#onyx-ptp-interface-module)
- [onyx_qos – Configures QoS](https://docs.ansible.com/ansible/latest/modules/onyx_qos_module.html#onyx-qos-module)
- [onyx_traffic_class – Configures Traffic Class](https://docs.ansible.com/ansible/latest/modules/onyx_traffic_class_module.html#onyx-traffic-class-module)
- [onyx_vlan – Manage VLANs on Mellanox ONYX network devices](https://docs.ansible.com/ansible/latest/modules/onyx_vlan_module.html#onyx-vlan-module)
- [onyx_vxlan – Configures Vxlan](https://docs.ansible.com/ansible/latest/modules/onyx_vxlan_module.html#onyx-vxlan-module)
- [onyx_wjh – Configure what-just-happend module](https://docs.ansible.com/ansible/latest/modules/onyx_wjh_module.html#onyx-wjh-module)



### Opx

- [opx_cps – CPS operations on networking device running Openswitch (OPX)](https://docs.ansible.com/ansible/latest/modules/opx_cps_module.html#opx-cps-module)



### Ordnance

- [ordnance_config – Manage Ordnance configuration sections](https://docs.ansible.com/ansible/latest/modules/ordnance_config_module.html#ordnance-config-module)
- [ordnance_facts – Collect facts from Ordnance Virtual Routers over SSH](https://docs.ansible.com/ansible/latest/modules/ordnance_facts_module.html#ordnance-facts-module)



### Ovs

- [openvswitch_bridge – Manage Open vSwitch bridges](https://docs.ansible.com/ansible/latest/modules/openvswitch_bridge_module.html#openvswitch-bridge-module)
- [openvswitch_db – Configure open vswitch database](https://docs.ansible.com/ansible/latest/modules/openvswitch_db_module.html#openvswitch-db-module)
- [openvswitch_port – Manage Open vSwitch ports](https://docs.ansible.com/ansible/latest/modules/openvswitch_port_module.html#openvswitch-port-module)



### Panos

- [panos_admin – Add or modify PAN-OS user accounts password](https://docs.ansible.com/ansible/latest/modules/panos_admin_module.html#panos-admin-module) **(D)**
- [panos_admpwd – change admin password of PAN-OS device using SSH with SSH key](https://docs.ansible.com/ansible/latest/modules/panos_admpwd_module.html#panos-admpwd-module) **(D)**
- [panos_cert_gen_ssh – generates a self-signed certificate using SSH protocol with SSH key](https://docs.ansible.com/ansible/latest/modules/panos_cert_gen_ssh_module.html#panos-cert-gen-ssh-module) **(D)**
- [panos_check – check if PAN-OS device is ready for configuration](https://docs.ansible.com/ansible/latest/modules/panos_check_module.html#panos-check-module) **(D)**
- [panos_commit – commit firewall’s candidate configuration](https://docs.ansible.com/ansible/latest/modules/panos_commit_module.html#panos-commit-module) **(D)**
- [panos_dag – create a dynamic address group](https://docs.ansible.com/ansible/latest/modules/panos_dag_module.html#panos-dag-module) **(D)**
- [panos_dag_tags – Create tags for DAG’s on PAN-OS devices](https://docs.ansible.com/ansible/latest/modules/panos_dag_tags_module.html#panos-dag-tags-module) **(D)**
- [panos_import – import file on PAN-OS devices](https://docs.ansible.com/ansible/latest/modules/panos_import_module.html#panos-import-module) **(D)**
- [panos_interface – configure data-port network interface for DHCP](https://docs.ansible.com/ansible/latest/modules/panos_interface_module.html#panos-interface-module) **(D)**
- [panos_lic – apply authcode to a device/instance](https://docs.ansible.com/ansible/latest/modules/panos_lic_module.html#panos-lic-module) **(D)**
- [panos_loadcfg – load configuration on PAN-OS device](https://docs.ansible.com/ansible/latest/modules/panos_loadcfg_module.html#panos-loadcfg-module) **(D)**
- [panos_match_rule – Test for match against a security rule on PAN-OS devices or Panorama management console](https://docs.ansible.com/ansible/latest/modules/panos_match_rule_module.html#panos-match-rule-module) **(D)**
- [panos_mgtconfig – configure management settings of device](https://docs.ansible.com/ansible/latest/modules/panos_mgtconfig_module.html#panos-mgtconfig-module) **(D)**
- [panos_nat_rule – create a policy NAT rule](https://docs.ansible.com/ansible/latest/modules/panos_nat_rule_module.html#panos-nat-rule-module) **(D)**
- [panos_object – create/read/update/delete object in PAN-OS or Panorama](https://docs.ansible.com/ansible/latest/modules/panos_object_module.html#panos-object-module) **(D)**
- [panos_op – execute arbitrary OP commands on PANW devices (e.g. show interface all)](https://docs.ansible.com/ansible/latest/modules/panos_op_module.html#panos-op-module) **(D)**
- [panos_pg – create a security profiles group](https://docs.ansible.com/ansible/latest/modules/panos_pg_module.html#panos-pg-module) **(D)**
- [panos_query_rules – PANOS module that allows search for security rules in PANW NGFW devices](https://docs.ansible.com/ansible/latest/modules/panos_query_rules_module.html#panos-query-rules-module) **(D)**
- [panos_restart – restart a device](https://docs.ansible.com/ansible/latest/modules/panos_restart_module.html#panos-restart-module) **(D)**
- [panos_sag – Create a static address group](https://docs.ansible.com/ansible/latest/modules/panos_sag_module.html#panos-sag-module) **(D)**
- [panos_security_rule – Create security rule policy on PAN-OS devices or Panorama management console](https://docs.ansible.com/ansible/latest/modules/panos_security_rule_module.html#panos-security-rule-module) **(D)**
- [panos_set – Execute arbitrary commands on a PAN-OS device using XPath and element](https://docs.ansible.com/ansible/latest/modules/panos_set_module.html#panos-set-module) **(D)**



### Protocol

- [net_lldp – Manage LLDP service configuration on network devices](https://docs.ansible.com/ansible/latest/modules/net_lldp_module.html#net-lldp-module) **(D)**



### Radware

- [vdirect_commit – Commits pending configuration changes on Radware devices](https://docs.ansible.com/ansible/latest/modules/vdirect_commit_module.html#vdirect-commit-module)
- [vdirect_file – Uploads a new or updates an existing runnable file into Radware vDirect server](https://docs.ansible.com/ansible/latest/modules/vdirect_file_module.html#vdirect-file-module)
- [vdirect_runnable – Runs templates and workflow actions in Radware vDirect server](https://docs.ansible.com/ansible/latest/modules/vdirect_runnable_module.html#vdirect-runnable-module)



### Restconf

- [restconf_config – Handles create, update, read and delete of configuration data on RESTCONF enabled devices](https://docs.ansible.com/ansible/latest/modules/restconf_config_module.html#restconf-config-module)
- [restconf_get – Fetch configuration/state data from RESTCONF enabled devices](https://docs.ansible.com/ansible/latest/modules/restconf_get_module.html#restconf-get-module)



### Routeros

- [routeros_command – Run commands on remote devices running MikroTik RouterOS](https://docs.ansible.com/ansible/latest/modules/routeros_command_module.html#routeros-command-module)
- [routeros_facts – Collect facts from remote devices running MikroTik RouterOS](https://docs.ansible.com/ansible/latest/modules/routeros_facts_module.html#routeros-facts-module)



### Routing

- [net_static_route – Manage static IP routes on network appliances (routers, switches et. al.)](https://docs.ansible.com/ansible/latest/modules/net_static_route_module.html#net-static-route-module) **(D)**



### Skydive

- [skydive_capture – Module which manages flow capture on interfaces](https://docs.ansible.com/ansible/latest/modules/skydive_capture_module.html#skydive-capture-module)
- [skydive_edge – Module to add edges to Skydive topology](https://docs.ansible.com/ansible/latest/modules/skydive_edge_module.html#skydive-edge-module)
- [skydive_node – Module which add nodes to Skydive topology](https://docs.ansible.com/ansible/latest/modules/skydive_node_module.html#skydive-node-module)



### Slxos

- [slxos_command – Run commands on remote devices running Extreme Networks SLX-OS](https://docs.ansible.com/ansible/latest/modules/slxos_command_module.html#slxos-command-module)
- [slxos_config – Manage Extreme Networks SLX-OS configuration sections](https://docs.ansible.com/ansible/latest/modules/slxos_config_module.html#slxos-config-module)
- [slxos_facts – Collect facts from devices running Extreme SLX-OS](https://docs.ansible.com/ansible/latest/modules/slxos_facts_module.html#slxos-facts-module)
- [slxos_interface – Manage Interfaces on Extreme SLX-OS network devices](https://docs.ansible.com/ansible/latest/modules/slxos_interface_module.html#slxos-interface-module)
- [slxos_l2_interface – Manage Layer-2 interface on Extreme Networks SLX-OS devices](https://docs.ansible.com/ansible/latest/modules/slxos_l2_interface_module.html#slxos-l2-interface-module)
- [slxos_l3_interface – Manage L3 interfaces on Extreme Networks SLX-OS network devices](https://docs.ansible.com/ansible/latest/modules/slxos_l3_interface_module.html#slxos-l3-interface-module)
- [slxos_linkagg – Manage link aggregation groups on Extreme Networks SLX-OS network devices](https://docs.ansible.com/ansible/latest/modules/slxos_linkagg_module.html#slxos-linkagg-module)
- [slxos_lldp – Manage LLDP configuration on Extreme Networks SLX-OS network devices](https://docs.ansible.com/ansible/latest/modules/slxos_lldp_module.html#slxos-lldp-module)
- [slxos_vlan – Manage VLANs on Extreme Networks SLX-OS network devices](https://docs.ansible.com/ansible/latest/modules/slxos_vlan_module.html#slxos-vlan-module)



### Sros

- [sros_command – Run commands on remote devices running Nokia SR OS](https://docs.ansible.com/ansible/latest/modules/sros_command_module.html#sros-command-module)
- [sros_config – Manage Nokia SR OS device configuration](https://docs.ansible.com/ansible/latest/modules/sros_config_module.html#sros-config-module)
- [sros_rollback – Configure Nokia SR OS rollback](https://docs.ansible.com/ansible/latest/modules/sros_rollback_module.html#sros-rollback-module)



### System

- [net_banner – Manage multiline banners on network devices](https://docs.ansible.com/ansible/latest/modules/net_banner_module.html#net-banner-module) **(D)**
- [net_logging – Manage logging on network devices](https://docs.ansible.com/ansible/latest/modules/net_logging_module.html#net-logging-module) **(D)**
- [net_ping – Tests reachability using ping from a network device](https://docs.ansible.com/ansible/latest/modules/net_ping_module.html#net-ping-module)
- [net_system – Manage the system attributes on network devices](https://docs.ansible.com/ansible/latest/modules/net_system_module.html#net-system-module) **(D)**
- [net_user – Manage the aggregate of local users on network device](https://docs.ansible.com/ansible/latest/modules/net_user_module.html#net-user-module) **(D)**



### Voss

- [voss_command – Run commands on remote devices running Extreme VOSS](https://docs.ansible.com/ansible/latest/modules/voss_command_module.html#voss-command-module)
- [voss_config – Manage Extreme VOSS configuration sections](https://docs.ansible.com/ansible/latest/modules/voss_config_module.html#voss-config-module)
- [voss_facts – Collect facts from remote devices running Extreme VOSS](https://docs.ansible.com/ansible/latest/modules/voss_facts_module.html#voss-facts-module)



### Vyos

- [vyos_banner – Manage multiline banners on VyOS devices](https://docs.ansible.com/ansible/latest/modules/vyos_banner_module.html#vyos-banner-module)
- [vyos_command – Run one or more commands on VyOS devices](https://docs.ansible.com/ansible/latest/modules/vyos_command_module.html#vyos-command-module)
- [vyos_config – Manage VyOS configuration on remote device](https://docs.ansible.com/ansible/latest/modules/vyos_config_module.html#vyos-config-module)
- [vyos_facts – Get facts about vyos devices](https://docs.ansible.com/ansible/latest/modules/vyos_facts_module.html#vyos-facts-module)
- [vyos_interface – Manage Interface on VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_interface_module.html#vyos-interface-module) **(D)**
- [vyos_interfaces – Manages interface attributes of VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_interfaces_module.html#vyos-interfaces-module)
- [vyos_l3_interface – Manage L3 interfaces on VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_l3_interface_module.html#vyos-l3-interface-module) **(D)**
- [vyos_l3_interfaces – Manages L3 interface attributes of VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_l3_interfaces_module.html#vyos-l3-interfaces-module)
- [vyos_lag_interfaces – Manages attributes of link aggregation groups on VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_lag_interfaces_module.html#vyos-lag-interfaces-module)
- [vyos_linkagg – Manage link aggregation groups on VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_linkagg_module.html#vyos-linkagg-module) **(D)**
- [vyos_lldp – Manage LLDP configuration on VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_lldp_module.html#vyos-lldp-module) **(D)**
- [vyos_lldp_global – Manage link layer discovery protocol (LLDP) attributes on VyOS devices](https://docs.ansible.com/ansible/latest/modules/vyos_lldp_global_module.html#vyos-lldp-global-module)
- [vyos_lldp_interface – Manage LLDP interfaces configuration on VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_lldp_interface_module.html#vyos-lldp-interface-module) **(D)**
- [vyos_lldp_interfaces – Manages attributes of lldp interfaces on VyOS devices](https://docs.ansible.com/ansible/latest/modules/vyos_lldp_interfaces_module.html#vyos-lldp-interfaces-module)
- [vyos_logging – Manage logging on network devices](https://docs.ansible.com/ansible/latest/modules/vyos_logging_module.html#vyos-logging-module)
- [vyos_ping – Tests reachability using ping from VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_ping_module.html#vyos-ping-module)
- [vyos_static_route – Manage static IP routes on Vyatta VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_static_route_module.html#vyos-static-route-module)
- [vyos_system – Run set system commands on VyOS devices](https://docs.ansible.com/ansible/latest/modules/vyos_system_module.html#vyos-system-module)
- [vyos_user – Manage the collection of local users on VyOS device](https://docs.ansible.com/ansible/latest/modules/vyos_user_module.html#vyos-user-module)
- [vyos_vlan – Manage VLANs on VyOS network devices](https://docs.ansible.com/ansible/latest/modules/vyos_vlan_module.html#vyos-vlan-module)

## Notification modules

- [bearychat – Send BearyChat notifications](https://docs.ansible.com/ansible/latest/modules/bearychat_module.html#bearychat-module)
- [campfire – Send a message to Campfire](https://docs.ansible.com/ansible/latest/modules/campfire_module.html#campfire-module)
- [catapult – Send a sms / mms using the catapult bandwidth api](https://docs.ansible.com/ansible/latest/modules/catapult_module.html#catapult-module)
- [cisco_spark – Send a message to a Cisco Spark Room or Individual](https://docs.ansible.com/ansible/latest/modules/cisco_spark_module.html#cisco-spark-module)
- [flowdock – Send a message to a flowdock](https://docs.ansible.com/ansible/latest/modules/flowdock_module.html#flowdock-module)
- [grove – Sends a notification to a grove.io channel](https://docs.ansible.com/ansible/latest/modules/grove_module.html#grove-module)
- [hipchat – Send a message to Hipchat](https://docs.ansible.com/ansible/latest/modules/hipchat_module.html#hipchat-module)
- [irc – Send a message to an IRC channel](https://docs.ansible.com/ansible/latest/modules/irc_module.html#irc-module)
- [jabber – Send a message to jabber user or chat room](https://docs.ansible.com/ansible/latest/modules/jabber_module.html#jabber-module)
- [logentries_msg – Send a message to logentries](https://docs.ansible.com/ansible/latest/modules/logentries_msg_module.html#logentries-msg-module)
- [mail – Send an email](https://docs.ansible.com/ansible/latest/modules/mail_module.html#mail-module)
- [matrix – Send notifications to matrix](https://docs.ansible.com/ansible/latest/modules/matrix_module.html#matrix-module)
- [mattermost – Send Mattermost notifications](https://docs.ansible.com/ansible/latest/modules/mattermost_module.html#mattermost-module)
- [mqtt – Publish a message on an MQTT topic for the IoT](https://docs.ansible.com/ansible/latest/modules/mqtt_module.html#mqtt-module)
- [nexmo – Send a SMS via nexmo](https://docs.ansible.com/ansible/latest/modules/nexmo_module.html#nexmo-module)
- [office_365_connector_card – Use webhooks to create Connector Card messages within an Office 365 group](https://docs.ansible.com/ansible/latest/modules/office_365_connector_card_module.html#office-365-connector-card-module)
- [pushbullet – Sends notifications to Pushbullet](https://docs.ansible.com/ansible/latest/modules/pushbullet_module.html#pushbullet-module)
- [pushover – Send notifications via https://pushover.net](https://docs.ansible.com/ansible/latest/modules/pushover_module.html#pushover-module)
- [rabbitmq_publish – Publish a message to a RabbitMQ queue](https://docs.ansible.com/ansible/latest/modules/rabbitmq_publish_module.html#rabbitmq-publish-module)
- [rocketchat – Send notifications to Rocket Chat](https://docs.ansible.com/ansible/latest/modules/rocketchat_module.html#rocketchat-module)
- [say – Makes a computer to speak](https://docs.ansible.com/ansible/latest/modules/say_module.html#say-module)
- [sendgrid – Sends an email with the SendGrid API](https://docs.ansible.com/ansible/latest/modules/sendgrid_module.html#sendgrid-module)
- [slack – Send Slack notifications](https://docs.ansible.com/ansible/latest/modules/slack_module.html#slack-module)
- [snow_record – Manage records in ServiceNow](https://docs.ansible.com/ansible/latest/modules/snow_record_module.html#snow-record-module)
- [snow_record_find – Search for multiple records from ServiceNow](https://docs.ansible.com/ansible/latest/modules/snow_record_find_module.html#snow-record-find-module)
- [syslogger – Log messages in the syslog](https://docs.ansible.com/ansible/latest/modules/syslogger_module.html#syslogger-module)
- [telegram – module for sending notifications via telegram](https://docs.ansible.com/ansible/latest/modules/telegram_module.html#telegram-module)
- [twilio – Sends a text message to a mobile phone through Twilio](https://docs.ansible.com/ansible/latest/modules/twilio_module.html#twilio-module)
- [typetalk – Send a message to typetalk](https://docs.ansible.com/ansible/latest/modules/typetalk_module.html#typetalk-module)

## Packaging modules

### Language

- [bower – Manage bower packages with bower](https://docs.ansible.com/ansible/latest/modules/bower_module.html#bower-module)
- [bundler – Manage Ruby Gem dependencies with Bundler](https://docs.ansible.com/ansible/latest/modules/bundler_module.html#bundler-module)
- [composer – Dependency Manager for PHP](https://docs.ansible.com/ansible/latest/modules/composer_module.html#composer-module)
- [cpanm – Manages Perl library dependencies](https://docs.ansible.com/ansible/latest/modules/cpanm_module.html#cpanm-module)
- [easy_install – Installs Python libraries](https://docs.ansible.com/ansible/latest/modules/easy_install_module.html#easy-install-module)
- [gem – Manage Ruby gems](https://docs.ansible.com/ansible/latest/modules/gem_module.html#gem-module)
- [maven_artifact – Downloads an Artifact from a Maven Repository](https://docs.ansible.com/ansible/latest/modules/maven_artifact_module.html#maven-artifact-module)
- [npm – Manage node.js packages with npm](https://docs.ansible.com/ansible/latest/modules/npm_module.html#npm-module)
- [pear – Manage pear/pecl packages](https://docs.ansible.com/ansible/latest/modules/pear_module.html#pear-module)
- [pip – Manages Python library dependencies](https://docs.ansible.com/ansible/latest/modules/pip_module.html#pip-module)
- [pip_package_info – pip package information](https://docs.ansible.com/ansible/latest/modules/pip_package_info_module.html#pip-package-info-module)
- [yarn – Manage node.js packages with Yarn](https://docs.ansible.com/ansible/latest/modules/yarn_module.html#yarn-module)



### Os

- [apk – Manages apk packages](https://docs.ansible.com/ansible/latest/modules/apk_module.html#apk-module)
- [apt – Manages apt-packages](https://docs.ansible.com/ansible/latest/modules/apt_module.html#apt-module)
- [apt_key – Add or remove an apt key](https://docs.ansible.com/ansible/latest/modules/apt_key_module.html#apt-key-module)
- [apt_repo – Manage APT repositories via apt-repo](https://docs.ansible.com/ansible/latest/modules/apt_repo_module.html#apt-repo-module)
- [apt_repository – Add and remove APT repositories](https://docs.ansible.com/ansible/latest/modules/apt_repository_module.html#apt-repository-module)
- [apt_rpm – apt_rpm package manager](https://docs.ansible.com/ansible/latest/modules/apt_rpm_module.html#apt-rpm-module)
- [dnf – Manages packages with the dnf package manager](https://docs.ansible.com/ansible/latest/modules/dnf_module.html#dnf-module)
- [dpkg_selections – Dpkg package selection selections](https://docs.ansible.com/ansible/latest/modules/dpkg_selections_module.html#dpkg-selections-module)
- [flatpak – Manage flatpaks](https://docs.ansible.com/ansible/latest/modules/flatpak_module.html#flatpak-module)
- [flatpak_remote – Manage flatpak repository remotes](https://docs.ansible.com/ansible/latest/modules/flatpak_remote_module.html#flatpak-remote-module)
- [homebrew – Package manager for Homebrew](https://docs.ansible.com/ansible/latest/modules/homebrew_module.html#homebrew-module)
- [homebrew_cask – Install/uninstall homebrew casks](https://docs.ansible.com/ansible/latest/modules/homebrew_cask_module.html#homebrew-cask-module)
- [homebrew_tap – Tap a Homebrew repository](https://docs.ansible.com/ansible/latest/modules/homebrew_tap_module.html#homebrew-tap-module)
- [installp – Manage packages on AIX](https://docs.ansible.com/ansible/latest/modules/installp_module.html#installp-module)
- [layman – Manage Gentoo overlays](https://docs.ansible.com/ansible/latest/modules/layman_module.html#layman-module)
- [macports – Package manager for MacPorts](https://docs.ansible.com/ansible/latest/modules/macports_module.html#macports-module)
- [openbsd_pkg – Manage packages on OpenBSD](https://docs.ansible.com/ansible/latest/modules/openbsd_pkg_module.html#openbsd-pkg-module)
- [opkg – Package manager for OpenWrt](https://docs.ansible.com/ansible/latest/modules/opkg_module.html#opkg-module)
- [package – Generic OS package manager](https://docs.ansible.com/ansible/latest/modules/package_module.html#package-module)
- [package_facts – package information as facts](https://docs.ansible.com/ansible/latest/modules/package_facts_module.html#package-facts-module)
- [pacman – Manage packages with pacman](https://docs.ansible.com/ansible/latest/modules/pacman_module.html#pacman-module)
- [pkg5 – Manages packages with the Solaris 11 Image Packaging System](https://docs.ansible.com/ansible/latest/modules/pkg5_module.html#pkg5-module)
- [pkg5_publisher – Manages Solaris 11 Image Packaging System publishers](https://docs.ansible.com/ansible/latest/modules/pkg5_publisher_module.html#pkg5-publisher-module)
- [pkgin – Package manager for SmartOS, NetBSD, et al](https://docs.ansible.com/ansible/latest/modules/pkgin_module.html#pkgin-module)
- [pkgng – Package manager for FreeBSD >= 9.0](https://docs.ansible.com/ansible/latest/modules/pkgng_module.html#pkgng-module)
- [pkgutil – Manage CSW-Packages on Solaris](https://docs.ansible.com/ansible/latest/modules/pkgutil_module.html#pkgutil-module)
- [portage – Package manager for Gentoo](https://docs.ansible.com/ansible/latest/modules/portage_module.html#portage-module)
- [portinstall – Installing packages from FreeBSD’s ports system](https://docs.ansible.com/ansible/latest/modules/portinstall_module.html#portinstall-module)
- [pulp_repo – Add or remove Pulp repos from a remote host](https://docs.ansible.com/ansible/latest/modules/pulp_repo_module.html#pulp-repo-module)
- [redhat_subscription – Manage registration and subscriptions to RHSM using the subscription-manager command](https://docs.ansible.com/ansible/latest/modules/redhat_subscription_module.html#redhat-subscription-module)
- [rhn_channel – Adds or removes Red Hat software channels](https://docs.ansible.com/ansible/latest/modules/rhn_channel_module.html#rhn-channel-module)
- [rhn_register – Manage Red Hat Network registration using the rhnreg_ks command](https://docs.ansible.com/ansible/latest/modules/rhn_register_module.html#rhn-register-module)
- [rhsm_release – Set or Unset RHSM Release version](https://docs.ansible.com/ansible/latest/modules/rhsm_release_module.html#rhsm-release-module)
- [rhsm_repository – Manage RHSM repositories using the subscription-manager command](https://docs.ansible.com/ansible/latest/modules/rhsm_repository_module.html#rhsm-repository-module)
- [rpm_key – Adds or removes a gpg key from the rpm db](https://docs.ansible.com/ansible/latest/modules/rpm_key_module.html#rpm-key-module)
- [slackpkg – Package manager for Slackware >= 12.2](https://docs.ansible.com/ansible/latest/modules/slackpkg_module.html#slackpkg-module)
- [snap – Manages snaps](https://docs.ansible.com/ansible/latest/modules/snap_module.html#snap-module)
- [sorcery – Package manager for Source Mage GNU/Linux](https://docs.ansible.com/ansible/latest/modules/sorcery_module.html#sorcery-module)
- [svr4pkg – Manage Solaris SVR4 packages](https://docs.ansible.com/ansible/latest/modules/svr4pkg_module.html#svr4pkg-module)
- [swdepot – Manage packages with swdepot package manager (HP-UX)](https://docs.ansible.com/ansible/latest/modules/swdepot_module.html#swdepot-module)
- [swupd – Manages updates and bundles in ClearLinux systems](https://docs.ansible.com/ansible/latest/modules/swupd_module.html#swupd-module)
- [urpmi – Urpmi manager](https://docs.ansible.com/ansible/latest/modules/urpmi_module.html#urpmi-module)
- [xbps – Manage packages with XBPS](https://docs.ansible.com/ansible/latest/modules/xbps_module.html#xbps-module)
- [yum – Manages packages with the yum package manager](https://docs.ansible.com/ansible/latest/modules/yum_module.html#yum-module)
- [yum_repository – Add or remove YUM repositories](https://docs.ansible.com/ansible/latest/modules/yum_repository_module.html#yum-repository-module)
- [zypper – Manage packages on SUSE and openSUSE](https://docs.ansible.com/ansible/latest/modules/zypper_module.html#zypper-module)
- [zypper_repository – Add and remove Zypper repositories](https://docs.ansible.com/ansible/latest/modules/zypper_repository_module.html#zypper-repository-module)

## Remote Management modules

- [wakeonlan – Send a magic Wake-on-LAN (WoL) broadcast packet](https://docs.ansible.com/ansible/latest/modules/wakeonlan_module.html#wakeonlan-module)



### Cobbler

- [cobbler_sync – Sync Cobbler](https://docs.ansible.com/ansible/latest/modules/cobbler_sync_module.html#cobbler-sync-module)
- [cobbler_system – Manage system objects in Cobbler](https://docs.ansible.com/ansible/latest/modules/cobbler_system_module.html#cobbler-system-module)



### Cpm

- [cpm_plugconfig – Get and Set Plug Parameters on WTI OOB and PDU power devices](https://docs.ansible.com/ansible/latest/modules/cpm_plugconfig_module.html#cpm-plugconfig-module)
- [cpm_plugcontrol – Get and Set Plug actions on WTI OOB and PDU power devices](https://docs.ansible.com/ansible/latest/modules/cpm_plugcontrol_module.html#cpm-plugcontrol-module)
- [cpm_serial_port_config – Set Serial port parameters in WTI OOB and PDU devices](https://docs.ansible.com/ansible/latest/modules/cpm_serial_port_config_module.html#cpm-serial-port-config-module)
- [cpm_serial_port_info – Get Serial port parameters in WTI OOB and PDU devices](https://docs.ansible.com/ansible/latest/modules/cpm_serial_port_info_module.html#cpm-serial-port-info-module)
- [cpm_user – Get various status and parameters from WTI OOB and PDU devices](https://docs.ansible.com/ansible/latest/modules/cpm_user_module.html#cpm-user-module)



### Dellemc

- [idrac_firmware – Firmware update from a repository on a network share (CIFS, NFS)](https://docs.ansible.com/ansible/latest/modules/idrac_firmware_module.html#idrac-firmware-module)
- [idrac_server_config_profile – Export or Import iDRAC Server Configuration Profile (SCP)](https://docs.ansible.com/ansible/latest/modules/idrac_server_config_profile_module.html#idrac-server-config-profile-module)
- [ome_device_info – Retrieves the information about Device](https://docs.ansible.com/ansible/latest/modules/ome_device_info_module.html#ome-device-info-module)



### Foreman

- [foreman – Manage Foreman Resources](https://docs.ansible.com/ansible/latest/modules/foreman_module.html#foreman-module) **(D)**
- [katello – Manage Katello Resources](https://docs.ansible.com/ansible/latest/modules/katello_module.html#katello-module) **(D)**



### Hpilo

- [hpilo_boot – Boot system using specific media through HP iLO interface](https://docs.ansible.com/ansible/latest/modules/hpilo_boot_module.html#hpilo-boot-module)
- [hpilo_info – Gather information through an HP iLO interface](https://docs.ansible.com/ansible/latest/modules/hpilo_info_module.html#hpilo-info-module)
- [hponcfg – Configure HP iLO interface using hponcfg](https://docs.ansible.com/ansible/latest/modules/hponcfg_module.html#hponcfg-module)



### Imc

- [imc_rest – Manage Cisco IMC hardware through its REST API](https://docs.ansible.com/ansible/latest/modules/imc_rest_module.html#imc-rest-module)



### Intersight

- [intersight_info – Gather information about Intersight](https://docs.ansible.com/ansible/latest/modules/intersight_info_module.html#intersight-info-module)
- [intersight_rest_api – REST API configuration for Cisco Intersight](https://docs.ansible.com/ansible/latest/modules/intersight_rest_api_module.html#intersight-rest-api-module)



### Ipmi

- [ipmi_boot – Management of order of boot devices](https://docs.ansible.com/ansible/latest/modules/ipmi_boot_module.html#ipmi-boot-module)
- [ipmi_power – Power management for machine](https://docs.ansible.com/ansible/latest/modules/ipmi_power_module.html#ipmi-power-module)



### Lxca

- [lxca_cmms – Custom module for lxca cmms inventory utility](https://docs.ansible.com/ansible/latest/modules/lxca_cmms_module.html#lxca-cmms-module)
- [lxca_nodes – Custom module for lxca nodes inventory utility](https://docs.ansible.com/ansible/latest/modules/lxca_nodes_module.html#lxca-nodes-module)



### Manageiq

- [manageiq_alert_profiles – Configuration of alert profiles for ManageIQ](https://docs.ansible.com/ansible/latest/modules/manageiq_alert_profiles_module.html#manageiq-alert-profiles-module)
- [manageiq_alerts – Configuration of alerts in ManageIQ](https://docs.ansible.com/ansible/latest/modules/manageiq_alerts_module.html#manageiq-alerts-module)
- [manageiq_group – Management of groups in ManageIQ](https://docs.ansible.com/ansible/latest/modules/manageiq_group_module.html#manageiq-group-module)
- [manageiq_policies – Management of resource policy_profiles in ManageIQ](https://docs.ansible.com/ansible/latest/modules/manageiq_policies_module.html#manageiq-policies-module)
- [manageiq_provider – Management of provider in ManageIQ](https://docs.ansible.com/ansible/latest/modules/manageiq_provider_module.html#manageiq-provider-module)
- [manageiq_tags – Management of resource tags in ManageIQ](https://docs.ansible.com/ansible/latest/modules/manageiq_tags_module.html#manageiq-tags-module)
- [manageiq_tenant – Management of tenants in ManageIQ](https://docs.ansible.com/ansible/latest/modules/manageiq_tenant_module.html#manageiq-tenant-module)
- [manageiq_user – Management of users in ManageIQ](https://docs.ansible.com/ansible/latest/modules/manageiq_user_module.html#manageiq-user-module)



### Oneview

- [oneview_datacenter_info – Retrieve information about the OneView Data Centers](https://docs.ansible.com/ansible/latest/modules/oneview_datacenter_info_module.html#oneview-datacenter-info-module)
- [oneview_enclosure_info – Retrieve information about one or more Enclosures](https://docs.ansible.com/ansible/latest/modules/oneview_enclosure_info_module.html#oneview-enclosure-info-module)
- [oneview_ethernet_network – Manage OneView Ethernet Network resources](https://docs.ansible.com/ansible/latest/modules/oneview_ethernet_network_module.html#oneview-ethernet-network-module)
- [oneview_ethernet_network_info – Retrieve the information about one or more of the OneView Ethernet Networks](https://docs.ansible.com/ansible/latest/modules/oneview_ethernet_network_info_module.html#oneview-ethernet-network-info-module)
- [oneview_fc_network – Manage OneView Fibre Channel Network resources](https://docs.ansible.com/ansible/latest/modules/oneview_fc_network_module.html#oneview-fc-network-module)
- [oneview_fc_network_info – Retrieve the information about one or more of the OneView Fibre Channel Networks](https://docs.ansible.com/ansible/latest/modules/oneview_fc_network_info_module.html#oneview-fc-network-info-module)
- [oneview_fcoe_network – Manage OneView FCoE Network resources](https://docs.ansible.com/ansible/latest/modules/oneview_fcoe_network_module.html#oneview-fcoe-network-module)
- [oneview_fcoe_network_info – Retrieve the information about one or more of the OneView FCoE Networks](https://docs.ansible.com/ansible/latest/modules/oneview_fcoe_network_info_module.html#oneview-fcoe-network-info-module)
- [oneview_logical_interconnect_group – Manage OneView Logical Interconnect Group resources](https://docs.ansible.com/ansible/latest/modules/oneview_logical_interconnect_group_module.html#oneview-logical-interconnect-group-module)
- [oneview_logical_interconnect_group_info – Retrieve information about one or more of the OneView Logical Interconnect Groups](https://docs.ansible.com/ansible/latest/modules/oneview_logical_interconnect_group_info_module.html#oneview-logical-interconnect-group-info-module)
- [oneview_network_set – Manage HPE OneView Network Set resources](https://docs.ansible.com/ansible/latest/modules/oneview_network_set_module.html#oneview-network-set-module)
- [oneview_network_set_info – Retrieve information about the OneView Network Sets](https://docs.ansible.com/ansible/latest/modules/oneview_network_set_info_module.html#oneview-network-set-info-module)
- [oneview_san_manager – Manage OneView SAN Manager resources](https://docs.ansible.com/ansible/latest/modules/oneview_san_manager_module.html#oneview-san-manager-module)
- [oneview_san_manager_info – Retrieve information about one or more of the OneView SAN Managers](https://docs.ansible.com/ansible/latest/modules/oneview_san_manager_info_module.html#oneview-san-manager-info-module)



### Redfish

- [idrac_redfish_command – Manages Out-Of-Band controllers using iDRAC OEM Redfish APIs](https://docs.ansible.com/ansible/latest/modules/idrac_redfish_command_module.html#idrac-redfish-command-module)
- [idrac_redfish_config – Manages servers through iDRAC using Dell Redfish APIs](https://docs.ansible.com/ansible/latest/modules/idrac_redfish_config_module.html#idrac-redfish-config-module)
- [idrac_redfish_info – Manages servers through iDRAC using Dell Redfish APIs](https://docs.ansible.com/ansible/latest/modules/idrac_redfish_info_module.html#idrac-redfish-info-module)
- [redfish_command – Manages Out-Of-Band controllers using Redfish APIs](https://docs.ansible.com/ansible/latest/modules/redfish_command_module.html#redfish-command-module)
- [redfish_config – Manages Out-Of-Band controllers using Redfish APIs](https://docs.ansible.com/ansible/latest/modules/redfish_config_module.html#redfish-config-module)
- [redfish_info – Manages Out-Of-Band controllers using Redfish APIs](https://docs.ansible.com/ansible/latest/modules/redfish_info_module.html#redfish-info-module)



### Stacki

- [stacki_host – Add or remove host to stacki front-end](https://docs.ansible.com/ansible/latest/modules/stacki_host_module.html#stacki-host-module)



### Ucs

- [ucs_disk_group_policy – Configures disk group policies on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_disk_group_policy_module.html#ucs-disk-group-policy-module)
- [ucs_dns_server – Configure DNS servers on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_dns_server_module.html#ucs-dns-server-module)
- [ucs_ip_pool – Configures IP address pools on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_ip_pool_module.html#ucs-ip-pool-module)
- [ucs_lan_connectivity – Configures LAN Connectivity Policies on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_lan_connectivity_module.html#ucs-lan-connectivity-module)
- [ucs_mac_pool – Configures MAC address pools on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_mac_pool_module.html#ucs-mac-pool-module)
- [ucs_managed_objects – Configures Managed Objects on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_managed_objects_module.html#ucs-managed-objects-module)
- [ucs_ntp_server – Configures NTP server on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_ntp_server_module.html#ucs-ntp-server-module)
- [ucs_org – Manages UCS Organizations for UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_org_module.html#ucs-org-module)
- [ucs_san_connectivity – Configures SAN Connectivity Policies on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_san_connectivity_module.html#ucs-san-connectivity-module)
- [ucs_service_profile_template – Configures Service Profile Templates on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_service_profile_template_module.html#ucs-service-profile-template-module)
- [ucs_storage_profile – Configures storage profiles on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_storage_profile_module.html#ucs-storage-profile-module)
- [ucs_timezone – Configures timezone on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_timezone_module.html#ucs-timezone-module)
- [ucs_uuid_pool – Configures server UUID pools on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_uuid_pool_module.html#ucs-uuid-pool-module)
- [ucs_vhba_template – Configures vHBA templates on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_vhba_template_module.html#ucs-vhba-template-module)
- [ucs_vlan_find – Find VLANs on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_vlan_find_module.html#ucs-vlan-find-module)
- [ucs_vlans – Configures VLANs on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_vlans_module.html#ucs-vlans-module)
- [ucs_vnic_template – Configures vNIC templates on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_vnic_template_module.html#ucs-vnic-template-module)
- [ucs_vsans – Configures VSANs on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_vsans_module.html#ucs-vsans-module)
- [ucs_wwn_pool – Configures WWNN or WWPN pools on Cisco UCS Manager](https://docs.ansible.com/ansible/latest/modules/ucs_wwn_pool_module.html#ucs-wwn-pool-module)

## Source Control modules

- [bzr – Deploy software (or files) from bzr branches](https://docs.ansible.com/ansible/latest/modules/bzr_module.html#bzr-module)
- [git – Deploy software (or files) from git checkouts](https://docs.ansible.com/ansible/latest/modules/git_module.html#git-module)
- [git_config – Read and write git configuration](https://docs.ansible.com/ansible/latest/modules/git_config_module.html#git-config-module)
- [github_deploy_key – Manages deploy keys for GitHub repositories](https://docs.ansible.com/ansible/latest/modules/github_deploy_key_module.html#github-deploy-key-module)
- [github_hooks – Manages GitHub service hooks](https://docs.ansible.com/ansible/latest/modules/github_hooks_module.html#github-hooks-module) **(D)**
- [github_issue – View GitHub issue](https://docs.ansible.com/ansible/latest/modules/github_issue_module.html#github-issue-module)
- [github_key – Manage GitHub access keys](https://docs.ansible.com/ansible/latest/modules/github_key_module.html#github-key-module)
- [github_release – Interact with GitHub Releases](https://docs.ansible.com/ansible/latest/modules/github_release_module.html#github-release-module)
- [github_webhook – Manage GitHub webhooks](https://docs.ansible.com/ansible/latest/modules/github_webhook_module.html#github-webhook-module)
- [github_webhook_info – Query information about GitHub webhooks](https://docs.ansible.com/ansible/latest/modules/github_webhook_info_module.html#github-webhook-info-module)
- [gitlab_deploy_key – Manages GitLab project deploy keys](https://docs.ansible.com/ansible/latest/modules/gitlab_deploy_key_module.html#gitlab-deploy-key-module)
- [gitlab_group – Creates/updates/deletes GitLab Groups](https://docs.ansible.com/ansible/latest/modules/gitlab_group_module.html#gitlab-group-module)
- [gitlab_hook – Manages GitLab project hooks](https://docs.ansible.com/ansible/latest/modules/gitlab_hook_module.html#gitlab-hook-module)
- [gitlab_project – Creates/updates/deletes GitLab Projects](https://docs.ansible.com/ansible/latest/modules/gitlab_project_module.html#gitlab-project-module)
- [gitlab_project_variable – Creates/updates/deletes GitLab Projects Variables](https://docs.ansible.com/ansible/latest/modules/gitlab_project_variable_module.html#gitlab-project-variable-module)
- [gitlab_runner – Create, modify and delete GitLab Runners](https://docs.ansible.com/ansible/latest/modules/gitlab_runner_module.html#gitlab-runner-module)
- [gitlab_user – Creates/updates/deletes GitLab Users](https://docs.ansible.com/ansible/latest/modules/gitlab_user_module.html#gitlab-user-module)
- [hg – Manages Mercurial (hg) repositories](https://docs.ansible.com/ansible/latest/modules/hg_module.html#hg-module)
- [subversion – Deploys a subversion repository](https://docs.ansible.com/ansible/latest/modules/subversion_module.html#subversion-module)



### Bitbucket

- [bitbucket_access_key – Manages Bitbucket repository access keys](https://docs.ansible.com/ansible/latest/modules/bitbucket_access_key_module.html#bitbucket-access-key-module)
- [bitbucket_pipeline_key_pair – Manages Bitbucket pipeline SSH key pair](https://docs.ansible.com/ansible/latest/modules/bitbucket_pipeline_key_pair_module.html#bitbucket-pipeline-key-pair-module)
- [bitbucket_pipeline_known_host – Manages Bitbucket pipeline known hosts](https://docs.ansible.com/ansible/latest/modules/bitbucket_pipeline_known_host_module.html#bitbucket-pipeline-known-host-module)
- [bitbucket_pipeline_variable – Manages Bitbucket pipeline variables](https://docs.ansible.com/ansible/latest/modules/bitbucket_pipeline_variable_module.html#bitbucket-pipeline-variable-module)

## Storage modules

### Emc

- [emc_vnx_sg_member – Manage storage group member on EMC VNX](https://docs.ansible.com/ansible/latest/modules/emc_vnx_sg_member_module.html#emc-vnx-sg-member-module)



### Glusterfs

- [gluster_heal_info – Gather information on self-heal or rebalance status](https://docs.ansible.com/ansible/latest/modules/gluster_heal_info_module.html#gluster-heal-info-module)
- [gluster_peer – Attach/Detach peers to/from the cluster](https://docs.ansible.com/ansible/latest/modules/gluster_peer_module.html#gluster-peer-module)
- [gluster_volume – Manage GlusterFS volumes](https://docs.ansible.com/ansible/latest/modules/gluster_volume_module.html#gluster-volume-module)



### Hpe3Par

- [ss_3par_cpg – Manage HPE StoreServ 3PAR CPG](https://docs.ansible.com/ansible/latest/modules/ss_3par_cpg_module.html#ss-3par-cpg-module)



### Ibm

- [ibm_sa_domain – Manages domains on IBM Spectrum Accelerate Family storage systems](https://docs.ansible.com/ansible/latest/modules/ibm_sa_domain_module.html#ibm-sa-domain-module)
- [ibm_sa_host – Adds hosts to or removes them from IBM Spectrum Accelerate Family storage systems](https://docs.ansible.com/ansible/latest/modules/ibm_sa_host_module.html#ibm-sa-host-module)
- [ibm_sa_host_ports – Add host ports on IBM Spectrum Accelerate Family storage systems](https://docs.ansible.com/ansible/latest/modules/ibm_sa_host_ports_module.html#ibm-sa-host-ports-module)
- [ibm_sa_pool – Handles pools on IBM Spectrum Accelerate Family storage systems](https://docs.ansible.com/ansible/latest/modules/ibm_sa_pool_module.html#ibm-sa-pool-module)
- [ibm_sa_vol – Handle volumes on IBM Spectrum Accelerate Family storage systems](https://docs.ansible.com/ansible/latest/modules/ibm_sa_vol_module.html#ibm-sa-vol-module)
- [ibm_sa_vol_map – Handles volume mapping on IBM Spectrum Accelerate Family storage systems](https://docs.ansible.com/ansible/latest/modules/ibm_sa_vol_map_module.html#ibm-sa-vol-map-module)



### Infinidat

- [infini_export – Create, Delete or Modify NFS Exports on Infinibox](https://docs.ansible.com/ansible/latest/modules/infini_export_module.html#infini-export-module)
- [infini_export_client – Create, Delete or Modify NFS Client(s) for existing exports on Infinibox](https://docs.ansible.com/ansible/latest/modules/infini_export_client_module.html#infini-export-client-module)
- [infini_fs – Create, Delete or Modify filesystems on Infinibox](https://docs.ansible.com/ansible/latest/modules/infini_fs_module.html#infini-fs-module)
- [infini_host – Create, Delete and Modify Hosts on Infinibox](https://docs.ansible.com/ansible/latest/modules/infini_host_module.html#infini-host-module)
- [infini_pool – Create, Delete and Modify Pools on Infinibox](https://docs.ansible.com/ansible/latest/modules/infini_pool_module.html#infini-pool-module)
- [infini_vol – Create, Delete or Modify volumes on Infinibox](https://docs.ansible.com/ansible/latest/modules/infini_vol_module.html#infini-vol-module)



### Netapp

- [na_cdot_aggregate – Manage NetApp cDOT aggregates](https://docs.ansible.com/ansible/latest/modules/na_cdot_aggregate_module.html#na-cdot-aggregate-module) **(D)**
- [na_cdot_license – Manage NetApp cDOT protocol and feature licenses](https://docs.ansible.com/ansible/latest/modules/na_cdot_license_module.html#na-cdot-license-module) **(D)**
- [na_cdot_lun – Manage NetApp cDOT luns](https://docs.ansible.com/ansible/latest/modules/na_cdot_lun_module.html#na-cdot-lun-module) **(D)**
- [na_cdot_qtree – Manage qtrees](https://docs.ansible.com/ansible/latest/modules/na_cdot_qtree_module.html#na-cdot-qtree-module) **(D)**
- [na_cdot_svm – Manage NetApp cDOT svm](https://docs.ansible.com/ansible/latest/modules/na_cdot_svm_module.html#na-cdot-svm-module) **(D)**
- [na_cdot_user – useradmin configuration and management](https://docs.ansible.com/ansible/latest/modules/na_cdot_user_module.html#na-cdot-user-module) **(D)**
- [na_cdot_user_role – useradmin configuration and management](https://docs.ansible.com/ansible/latest/modules/na_cdot_user_role_module.html#na-cdot-user-role-module) **(D)**
- [na_cdot_volume – Manage NetApp cDOT volumes](https://docs.ansible.com/ansible/latest/modules/na_cdot_volume_module.html#na-cdot-volume-module) **(D)**
- [na_elementsw_access_group – NetApp Element Software Manage Access Groups](https://docs.ansible.com/ansible/latest/modules/na_elementsw_access_group_module.html#na-elementsw-access-group-module)
- [na_elementsw_account – NetApp Element Software Manage Accounts](https://docs.ansible.com/ansible/latest/modules/na_elementsw_account_module.html#na-elementsw-account-module)
- [na_elementsw_admin_users – NetApp Element Software Manage Admin Users](https://docs.ansible.com/ansible/latest/modules/na_elementsw_admin_users_module.html#na-elementsw-admin-users-module)
- [na_elementsw_backup – NetApp Element Software Create Backups](https://docs.ansible.com/ansible/latest/modules/na_elementsw_backup_module.html#na-elementsw-backup-module)
- [na_elementsw_check_connections – NetApp Element Software Check connectivity to MVIP and SVIP](https://docs.ansible.com/ansible/latest/modules/na_elementsw_check_connections_module.html#na-elementsw-check-connections-module)
- [na_elementsw_cluster – NetApp Element Software Create Cluster](https://docs.ansible.com/ansible/latest/modules/na_elementsw_cluster_module.html#na-elementsw-cluster-module)
- [na_elementsw_cluster_config – Configure Element SW Cluster](https://docs.ansible.com/ansible/latest/modules/na_elementsw_cluster_config_module.html#na-elementsw-cluster-config-module)
- [na_elementsw_cluster_pair – NetApp Element Software Manage Cluster Pair](https://docs.ansible.com/ansible/latest/modules/na_elementsw_cluster_pair_module.html#na-elementsw-cluster-pair-module)
- [na_elementsw_cluster_snmp – Configure Element SW Cluster SNMP](https://docs.ansible.com/ansible/latest/modules/na_elementsw_cluster_snmp_module.html#na-elementsw-cluster-snmp-module)
- [na_elementsw_drive – NetApp Element Software Manage Node Drives](https://docs.ansible.com/ansible/latest/modules/na_elementsw_drive_module.html#na-elementsw-drive-module)
- [na_elementsw_initiators – Manage Element SW initiators](https://docs.ansible.com/ansible/latest/modules/na_elementsw_initiators_module.html#na-elementsw-initiators-module)
- [na_elementsw_ldap – NetApp Element Software Manage ldap admin users](https://docs.ansible.com/ansible/latest/modules/na_elementsw_ldap_module.html#na-elementsw-ldap-module)
- [na_elementsw_network_interfaces – NetApp Element Software Configure Node Network Interfaces](https://docs.ansible.com/ansible/latest/modules/na_elementsw_network_interfaces_module.html#na-elementsw-network-interfaces-module)
- [na_elementsw_node – NetApp Element Software Node Operation](https://docs.ansible.com/ansible/latest/modules/na_elementsw_node_module.html#na-elementsw-node-module)
- [na_elementsw_snapshot – NetApp Element Software Manage Snapshots](https://docs.ansible.com/ansible/latest/modules/na_elementsw_snapshot_module.html#na-elementsw-snapshot-module)
- [na_elementsw_snapshot_restore – NetApp Element Software Restore Snapshot](https://docs.ansible.com/ansible/latest/modules/na_elementsw_snapshot_restore_module.html#na-elementsw-snapshot-restore-module)
- [na_elementsw_snapshot_schedule – NetApp Element Software Snapshot Schedules](https://docs.ansible.com/ansible/latest/modules/na_elementsw_snapshot_schedule_module.html#na-elementsw-snapshot-schedule-module)
- [na_elementsw_vlan – NetApp Element Software Manage VLAN](https://docs.ansible.com/ansible/latest/modules/na_elementsw_vlan_module.html#na-elementsw-vlan-module)
- [na_elementsw_volume – NetApp Element Software Manage Volumes](https://docs.ansible.com/ansible/latest/modules/na_elementsw_volume_module.html#na-elementsw-volume-module)
- [na_elementsw_volume_clone – NetApp Element Software Create Volume Clone](https://docs.ansible.com/ansible/latest/modules/na_elementsw_volume_clone_module.html#na-elementsw-volume-clone-module)
- [na_elementsw_volume_pair – NetApp Element Software Volume Pair](https://docs.ansible.com/ansible/latest/modules/na_elementsw_volume_pair_module.html#na-elementsw-volume-pair-module)
- [na_ontap_aggregate – NetApp ONTAP manage aggregates](https://docs.ansible.com/ansible/latest/modules/na_ontap_aggregate_module.html#na-ontap-aggregate-module)
- [na_ontap_autosupport – NetApp ONTAP Autosupport](https://docs.ansible.com/ansible/latest/modules/na_ontap_autosupport_module.html#na-ontap-autosupport-module)
- [na_ontap_broadcast_domain – NetApp ONTAP manage broadcast domains](https://docs.ansible.com/ansible/latest/modules/na_ontap_broadcast_domain_module.html#na-ontap-broadcast-domain-module)
- [na_ontap_broadcast_domain_ports – NetApp ONTAP manage broadcast domain ports](https://docs.ansible.com/ansible/latest/modules/na_ontap_broadcast_domain_ports_module.html#na-ontap-broadcast-domain-ports-module)
- [na_ontap_cg_snapshot – NetApp ONTAP manage consistency group snapshot](https://docs.ansible.com/ansible/latest/modules/na_ontap_cg_snapshot_module.html#na-ontap-cg-snapshot-module)
- [na_ontap_cifs – NetApp ONTAP Manage cifs-share](https://docs.ansible.com/ansible/latest/modules/na_ontap_cifs_module.html#na-ontap-cifs-module)
- [na_ontap_cifs_acl – NetApp ONTAP manage cifs-share-access-control](https://docs.ansible.com/ansible/latest/modules/na_ontap_cifs_acl_module.html#na-ontap-cifs-acl-module)
- [na_ontap_cifs_server – NetApp ONTAP CIFS server configuration](https://docs.ansible.com/ansible/latest/modules/na_ontap_cifs_server_module.html#na-ontap-cifs-server-module)
- [na_ontap_cluster – NetApp ONTAP cluster - create, join, add license](https://docs.ansible.com/ansible/latest/modules/na_ontap_cluster_module.html#na-ontap-cluster-module)
- [na_ontap_cluster_ha – NetApp ONTAP Manage HA status for cluster](https://docs.ansible.com/ansible/latest/modules/na_ontap_cluster_ha_module.html#na-ontap-cluster-ha-module)
- [na_ontap_cluster_peer – NetApp ONTAP Manage Cluster peering](https://docs.ansible.com/ansible/latest/modules/na_ontap_cluster_peer_module.html#na-ontap-cluster-peer-module)
- [na_ontap_command – NetApp ONTAP Run any cli command, the username provided needs to have console login permission](https://docs.ansible.com/ansible/latest/modules/na_ontap_command_module.html#na-ontap-command-module)
- [na_ontap_disks – NetApp ONTAP Assign disks to nodes](https://docs.ansible.com/ansible/latest/modules/na_ontap_disks_module.html#na-ontap-disks-module)
- [na_ontap_dns – NetApp ONTAP Create, delete, modify DNS servers](https://docs.ansible.com/ansible/latest/modules/na_ontap_dns_module.html#na-ontap-dns-module)
- [na_ontap_export_policy – NetApp ONTAP manage export-policy](https://docs.ansible.com/ansible/latest/modules/na_ontap_export_policy_module.html#na-ontap-export-policy-module)
- [na_ontap_export_policy_rule – NetApp ONTAP manage export policy rules](https://docs.ansible.com/ansible/latest/modules/na_ontap_export_policy_rule_module.html#na-ontap-export-policy-rule-module)
- [na_ontap_fcp – NetApp ONTAP Start, Stop and Enable FCP services](https://docs.ansible.com/ansible/latest/modules/na_ontap_fcp_module.html#na-ontap-fcp-module)
- [na_ontap_firewall_policy – NetApp ONTAP Manage a firewall policy](https://docs.ansible.com/ansible/latest/modules/na_ontap_firewall_policy_module.html#na-ontap-firewall-policy-module)
- [na_ontap_firmware_upgrade – NetApp ONTAP firmware upgrade for SP, shelf, ACP, and disk](https://docs.ansible.com/ansible/latest/modules/na_ontap_firmware_upgrade_module.html#na-ontap-firmware-upgrade-module)
- [na_ontap_flexcache – NetApp ONTAP FlexCache - create/delete relationship](https://docs.ansible.com/ansible/latest/modules/na_ontap_flexcache_module.html#na-ontap-flexcache-module)
- [na_ontap_gather_facts – NetApp information gatherer](https://docs.ansible.com/ansible/latest/modules/na_ontap_gather_facts_module.html#na-ontap-gather-facts-module) **(D)**
- [na_ontap_igroup – NetApp ONTAP iSCSI or FC igroup configuration](https://docs.ansible.com/ansible/latest/modules/na_ontap_igroup_module.html#na-ontap-igroup-module)
- [na_ontap_igroup_initiator – NetApp ONTAP igroup initiator configuration](https://docs.ansible.com/ansible/latest/modules/na_ontap_igroup_initiator_module.html#na-ontap-igroup-initiator-module)
- [na_ontap_info – NetApp information gatherer](https://docs.ansible.com/ansible/latest/modules/na_ontap_info_module.html#na-ontap-info-module)
- [na_ontap_interface – NetApp ONTAP LIF configuration](https://docs.ansible.com/ansible/latest/modules/na_ontap_interface_module.html#na-ontap-interface-module)
- [na_ontap_ipspace – NetApp ONTAP Manage an ipspace](https://docs.ansible.com/ansible/latest/modules/na_ontap_ipspace_module.html#na-ontap-ipspace-module)
- [na_ontap_iscsi – NetApp ONTAP manage iSCSI service](https://docs.ansible.com/ansible/latest/modules/na_ontap_iscsi_module.html#na-ontap-iscsi-module)
- [na_ontap_job_schedule – NetApp ONTAP Job Schedule](https://docs.ansible.com/ansible/latest/modules/na_ontap_job_schedule_module.html#na-ontap-job-schedule-module)
- [na_ontap_kerberos_realm – NetApp ONTAP vserver nfs kerberos realm](https://docs.ansible.com/ansible/latest/modules/na_ontap_kerberos_realm_module.html#na-ontap-kerberos-realm-module)
- [na_ontap_ldap – NetApp ONTAP LDAP](https://docs.ansible.com/ansible/latest/modules/na_ontap_ldap_module.html#na-ontap-ldap-module)
- [na_ontap_ldap_client – NetApp ONTAP LDAP client](https://docs.ansible.com/ansible/latest/modules/na_ontap_ldap_client_module.html#na-ontap-ldap-client-module)
- [na_ontap_license – NetApp ONTAP protocol and feature licenses](https://docs.ansible.com/ansible/latest/modules/na_ontap_license_module.html#na-ontap-license-module)
- [na_ontap_lun – NetApp ONTAP manage LUNs](https://docs.ansible.com/ansible/latest/modules/na_ontap_lun_module.html#na-ontap-lun-module)
- [na_ontap_lun_copy – NetApp ONTAP copy LUNs](https://docs.ansible.com/ansible/latest/modules/na_ontap_lun_copy_module.html#na-ontap-lun-copy-module)
- [na_ontap_lun_map – NetApp ONTAP LUN maps](https://docs.ansible.com/ansible/latest/modules/na_ontap_lun_map_module.html#na-ontap-lun-map-module)
- [na_ontap_motd – Setup motd](https://docs.ansible.com/ansible/latest/modules/na_ontap_motd_module.html#na-ontap-motd-module)
- [na_ontap_ndmp – NetApp ONTAP NDMP services configuration](https://docs.ansible.com/ansible/latest/modules/na_ontap_ndmp_module.html#na-ontap-ndmp-module)
- [na_ontap_net_ifgrp – NetApp Ontap modify network interface group](https://docs.ansible.com/ansible/latest/modules/na_ontap_net_ifgrp_module.html#na-ontap-net-ifgrp-module)
- [na_ontap_net_port – NetApp ONTAP network ports](https://docs.ansible.com/ansible/latest/modules/na_ontap_net_port_module.html#na-ontap-net-port-module)
- [na_ontap_net_routes – NetApp ONTAP network routes](https://docs.ansible.com/ansible/latest/modules/na_ontap_net_routes_module.html#na-ontap-net-routes-module)
- [na_ontap_net_subnet – NetApp ONTAP Create, delete, modify network subnets](https://docs.ansible.com/ansible/latest/modules/na_ontap_net_subnet_module.html#na-ontap-net-subnet-module)
- [na_ontap_net_vlan – NetApp ONTAP network VLAN](https://docs.ansible.com/ansible/latest/modules/na_ontap_net_vlan_module.html#na-ontap-net-vlan-module)
- [na_ontap_nfs – NetApp ONTAP NFS status](https://docs.ansible.com/ansible/latest/modules/na_ontap_nfs_module.html#na-ontap-nfs-module)
- [na_ontap_node – NetApp ONTAP Rename a node](https://docs.ansible.com/ansible/latest/modules/na_ontap_node_module.html#na-ontap-node-module)
- [na_ontap_ntp – NetApp ONTAP NTP server](https://docs.ansible.com/ansible/latest/modules/na_ontap_ntp_module.html#na-ontap-ntp-module)
- [na_ontap_nvme – NetApp ONTAP Manage NVMe Service](https://docs.ansible.com/ansible/latest/modules/na_ontap_nvme_module.html#na-ontap-nvme-module)
- [na_ontap_nvme_namespace – NetApp ONTAP Manage NVME Namespace](https://docs.ansible.com/ansible/latest/modules/na_ontap_nvme_namespace_module.html#na-ontap-nvme-namespace-module)
- [na_ontap_nvme_subsystem – NetApp ONTAP Manage NVME Subsystem](https://docs.ansible.com/ansible/latest/modules/na_ontap_nvme_subsystem_module.html#na-ontap-nvme-subsystem-module)
- [na_ontap_object_store – NetApp ONTAP manage object store config](https://docs.ansible.com/ansible/latest/modules/na_ontap_object_store_module.html#na-ontap-object-store-module)
- [na_ontap_ports – NetApp ONTAP add/remove ports](https://docs.ansible.com/ansible/latest/modules/na_ontap_ports_module.html#na-ontap-ports-module)
- [na_ontap_portset – NetApp ONTAP Create/Delete portset](https://docs.ansible.com/ansible/latest/modules/na_ontap_portset_module.html#na-ontap-portset-module)
- [na_ontap_qos_adaptive_policy_group – NetApp ONTAP Adaptive Quality of Service policy group](https://docs.ansible.com/ansible/latest/modules/na_ontap_qos_adaptive_policy_group_module.html#na-ontap-qos-adaptive-policy-group-module)
- [na_ontap_qos_policy_group – NetApp ONTAP manage policy group in Quality of Service](https://docs.ansible.com/ansible/latest/modules/na_ontap_qos_policy_group_module.html#na-ontap-qos-policy-group-module)
- [na_ontap_qtree – NetApp ONTAP manage qtrees](https://docs.ansible.com/ansible/latest/modules/na_ontap_qtree_module.html#na-ontap-qtree-module)
- [na_ontap_quotas – NetApp ONTAP Quotas](https://docs.ansible.com/ansible/latest/modules/na_ontap_quotas_module.html#na-ontap-quotas-module)
- [na_ontap_security_key_manager – NetApp ONTAP security key manager](https://docs.ansible.com/ansible/latest/modules/na_ontap_security_key_manager_module.html#na-ontap-security-key-manager-module)
- [na_ontap_service_processor_network – NetApp ONTAP service processor network](https://docs.ansible.com/ansible/latest/modules/na_ontap_service_processor_network_module.html#na-ontap-service-processor-network-module)
- [na_ontap_snapmirror – NetApp ONTAP or ElementSW Manage SnapMirror](https://docs.ansible.com/ansible/latest/modules/na_ontap_snapmirror_module.html#na-ontap-snapmirror-module)
- [na_ontap_snapshot – NetApp ONTAP manage Snapshots](https://docs.ansible.com/ansible/latest/modules/na_ontap_snapshot_module.html#na-ontap-snapshot-module)
- [na_ontap_snapshot_policy – NetApp ONTAP manage Snapshot Policy](https://docs.ansible.com/ansible/latest/modules/na_ontap_snapshot_policy_module.html#na-ontap-snapshot-policy-module)
- [na_ontap_snmp – NetApp ONTAP SNMP community](https://docs.ansible.com/ansible/latest/modules/na_ontap_snmp_module.html#na-ontap-snmp-module)
- [na_ontap_software_update – NetApp ONTAP Update Software](https://docs.ansible.com/ansible/latest/modules/na_ontap_software_update_module.html#na-ontap-software-update-module)
- [na_ontap_svm – NetApp ONTAP SVM](https://docs.ansible.com/ansible/latest/modules/na_ontap_svm_module.html#na-ontap-svm-module)
- [na_ontap_svm_options – NetApp ONTAP Modify SVM Options](https://docs.ansible.com/ansible/latest/modules/na_ontap_svm_options_module.html#na-ontap-svm-options-module)
- [na_ontap_ucadapter – NetApp ONTAP UC adapter configuration](https://docs.ansible.com/ansible/latest/modules/na_ontap_ucadapter_module.html#na-ontap-ucadapter-module)
- [na_ontap_unix_group – NetApp ONTAP UNIX Group](https://docs.ansible.com/ansible/latest/modules/na_ontap_unix_group_module.html#na-ontap-unix-group-module)
- [na_ontap_unix_user – NetApp ONTAP UNIX users](https://docs.ansible.com/ansible/latest/modules/na_ontap_unix_user_module.html#na-ontap-unix-user-module)
- [na_ontap_user – NetApp ONTAP user configuration and management](https://docs.ansible.com/ansible/latest/modules/na_ontap_user_module.html#na-ontap-user-module)
- [na_ontap_user_role – NetApp ONTAP user role configuration and management](https://docs.ansible.com/ansible/latest/modules/na_ontap_user_role_module.html#na-ontap-user-role-module)
- [na_ontap_volume – NetApp ONTAP manage volumes](https://docs.ansible.com/ansible/latest/modules/na_ontap_volume_module.html#na-ontap-volume-module)
- [na_ontap_volume_autosize – NetApp ONTAP manage volume autosize](https://docs.ansible.com/ansible/latest/modules/na_ontap_volume_autosize_module.html#na-ontap-volume-autosize-module)
- [na_ontap_volume_clone – NetApp ONTAP manage volume clones](https://docs.ansible.com/ansible/latest/modules/na_ontap_volume_clone_module.html#na-ontap-volume-clone-module)
- [na_ontap_vscan – NetApp ONTAP Vscan enable/disable](https://docs.ansible.com/ansible/latest/modules/na_ontap_vscan_module.html#na-ontap-vscan-module)
- [na_ontap_vscan_on_access_policy – NetApp ONTAP Vscan on access policy configuration](https://docs.ansible.com/ansible/latest/modules/na_ontap_vscan_on_access_policy_module.html#na-ontap-vscan-on-access-policy-module)
- [na_ontap_vscan_on_demand_task – NetApp ONTAP Vscan on demand task configuration](https://docs.ansible.com/ansible/latest/modules/na_ontap_vscan_on_demand_task_module.html#na-ontap-vscan-on-demand-task-module)
- [na_ontap_vscan_scanner_pool – NetApp ONTAP Vscan Scanner Pools Configuration](https://docs.ansible.com/ansible/latest/modules/na_ontap_vscan_scanner_pool_module.html#na-ontap-vscan-scanner-pool-module)
- [na_ontap_vserver_cifs_security – NetApp ONTAP vserver CIFS security modification](https://docs.ansible.com/ansible/latest/modules/na_ontap_vserver_cifs_security_module.html#na-ontap-vserver-cifs-security-module)
- [na_ontap_vserver_peer – NetApp ONTAP Vserver peering](https://docs.ansible.com/ansible/latest/modules/na_ontap_vserver_peer_module.html#na-ontap-vserver-peer-module)
- [netapp_e_alerts – NetApp E-Series manage email notification settings](https://docs.ansible.com/ansible/latest/modules/netapp_e_alerts_module.html#netapp-e-alerts-module)
- [netapp_e_amg – NetApp E-Series create, remove, and update asynchronous mirror groups](https://docs.ansible.com/ansible/latest/modules/netapp_e_amg_module.html#netapp-e-amg-module)
- [netapp_e_amg_role – NetApp E-Series update the role of a storage array within an Asynchronous Mirror Group (AMG)](https://docs.ansible.com/ansible/latest/modules/netapp_e_amg_role_module.html#netapp-e-amg-role-module)
- [netapp_e_amg_sync – NetApp E-Series conduct synchronization actions on asynchronous mirror groups](https://docs.ansible.com/ansible/latest/modules/netapp_e_amg_sync_module.html#netapp-e-amg-sync-module)
- [netapp_e_asup – NetApp E-Series manage auto-support settings](https://docs.ansible.com/ansible/latest/modules/netapp_e_asup_module.html#netapp-e-asup-module)
- [netapp_e_auditlog – NetApp E-Series manage audit-log configuration](https://docs.ansible.com/ansible/latest/modules/netapp_e_auditlog_module.html#netapp-e-auditlog-module)
- [netapp_e_auth – NetApp E-Series set or update the password for a storage array](https://docs.ansible.com/ansible/latest/modules/netapp_e_auth_module.html#netapp-e-auth-module)
- [netapp_e_drive_firmware – NetApp E-Series manage drive firmware](https://docs.ansible.com/ansible/latest/modules/netapp_e_drive_firmware_module.html#netapp-e-drive-firmware-module)
- [netapp_e_facts – NetApp E-Series retrieve facts about NetApp E-Series storage arrays](https://docs.ansible.com/ansible/latest/modules/netapp_e_facts_module.html#netapp-e-facts-module)
- [netapp_e_firmware – NetApp E-Series manage firmware](https://docs.ansible.com/ansible/latest/modules/netapp_e_firmware_module.html#netapp-e-firmware-module)
- [netapp_e_flashcache – NetApp E-Series manage SSD caches](https://docs.ansible.com/ansible/latest/modules/netapp_e_flashcache_module.html#netapp-e-flashcache-module)
- [netapp_e_global – NetApp E-Series manage global settings configuration](https://docs.ansible.com/ansible/latest/modules/netapp_e_global_module.html#netapp-e-global-module)
- [netapp_e_host – NetApp E-Series manage eseries hosts](https://docs.ansible.com/ansible/latest/modules/netapp_e_host_module.html#netapp-e-host-module)
- [netapp_e_hostgroup – NetApp E-Series manage array host groups](https://docs.ansible.com/ansible/latest/modules/netapp_e_hostgroup_module.html#netapp-e-hostgroup-module)
- [netapp_e_iscsi_interface – NetApp E-Series manage iSCSI interface configuration](https://docs.ansible.com/ansible/latest/modules/netapp_e_iscsi_interface_module.html#netapp-e-iscsi-interface-module)
- [netapp_e_iscsi_target – NetApp E-Series manage iSCSI target configuration](https://docs.ansible.com/ansible/latest/modules/netapp_e_iscsi_target_module.html#netapp-e-iscsi-target-module)
- [netapp_e_ldap – NetApp E-Series manage LDAP integration to use for authentication](https://docs.ansible.com/ansible/latest/modules/netapp_e_ldap_module.html#netapp-e-ldap-module)
- [netapp_e_lun_mapping – NetApp E-Series create, delete, or modify lun mappings](https://docs.ansible.com/ansible/latest/modules/netapp_e_lun_mapping_module.html#netapp-e-lun-mapping-module)
- [netapp_e_mgmt_interface – NetApp E-Series management interface configuration](https://docs.ansible.com/ansible/latest/modules/netapp_e_mgmt_interface_module.html#netapp-e-mgmt-interface-module)
- [netapp_e_snapshot_group – NetApp E-Series manage snapshot groups](https://docs.ansible.com/ansible/latest/modules/netapp_e_snapshot_group_module.html#netapp-e-snapshot-group-module)
- [netapp_e_snapshot_images – NetApp E-Series create and delete snapshot images](https://docs.ansible.com/ansible/latest/modules/netapp_e_snapshot_images_module.html#netapp-e-snapshot-images-module)
- [netapp_e_snapshot_volume – NetApp E-Series manage snapshot volumes](https://docs.ansible.com/ansible/latest/modules/netapp_e_snapshot_volume_module.html#netapp-e-snapshot-volume-module)
- [netapp_e_storage_system – NetApp E-Series Web Services Proxy manage storage arrays](https://docs.ansible.com/ansible/latest/modules/netapp_e_storage_system_module.html#netapp-e-storage-system-module)
- [netapp_e_storagepool – NetApp E-Series manage volume groups and disk pools](https://docs.ansible.com/ansible/latest/modules/netapp_e_storagepool_module.html#netapp-e-storagepool-module)
- [netapp_e_syslog – NetApp E-Series manage syslog settings](https://docs.ansible.com/ansible/latest/modules/netapp_e_syslog_module.html#netapp-e-syslog-module)
- [netapp_e_volume – NetApp E-Series manage storage volumes (standard and thin)](https://docs.ansible.com/ansible/latest/modules/netapp_e_volume_module.html#netapp-e-volume-module)
- [netapp_e_volume_copy – NetApp E-Series create volume copy pairs](https://docs.ansible.com/ansible/latest/modules/netapp_e_volume_copy_module.html#netapp-e-volume-copy-module)
- [sf_account_manager – Manage SolidFire accounts](https://docs.ansible.com/ansible/latest/modules/sf_account_manager_module.html#sf-account-manager-module) **(D)**
- [sf_check_connections – Check connectivity to MVIP and SVIP](https://docs.ansible.com/ansible/latest/modules/sf_check_connections_module.html#sf-check-connections-module) **(D)**
- [sf_snapshot_schedule_manager – Manage SolidFire snapshot schedules](https://docs.ansible.com/ansible/latest/modules/sf_snapshot_schedule_manager_module.html#sf-snapshot-schedule-manager-module) **(D)**
- [sf_volume_access_group_manager – Manage SolidFire Volume Access Groups](https://docs.ansible.com/ansible/latest/modules/sf_volume_access_group_manager_module.html#sf-volume-access-group-manager-module) **(D)**
- [sf_volume_manager – Manage SolidFire volumes](https://docs.ansible.com/ansible/latest/modules/sf_volume_manager_module.html#sf-volume-manager-module) **(D)**



### Purestorage

- [purefa_alert – Configure Pure Storage FlashArray alert email settings](https://docs.ansible.com/ansible/latest/modules/purefa_alert_module.html#purefa-alert-module)
- [purefa_arrayname – Configure Pure Storage FlashArray array name](https://docs.ansible.com/ansible/latest/modules/purefa_arrayname_module.html#purefa-arrayname-module)
- [purefa_banner – Configure Pure Storage FlashArray GUI and SSH MOTD message](https://docs.ansible.com/ansible/latest/modules/purefa_banner_module.html#purefa-banner-module)
- [purefa_connect – Manage replication connections between two FlashArrays](https://docs.ansible.com/ansible/latest/modules/purefa_connect_module.html#purefa-connect-module)
- [purefa_dns – Configure FlashArray DNS settings](https://docs.ansible.com/ansible/latest/modules/purefa_dns_module.html#purefa-dns-module)
- [purefa_ds – Configure FlashArray Directory Service](https://docs.ansible.com/ansible/latest/modules/purefa_ds_module.html#purefa-ds-module)
- [purefa_dsrole – Configure FlashArray Directory Service Roles](https://docs.ansible.com/ansible/latest/modules/purefa_dsrole_module.html#purefa-dsrole-module)
- [purefa_facts – Collect facts from Pure Storage FlashArray](https://docs.ansible.com/ansible/latest/modules/purefa_facts_module.html#purefa-facts-module) **(D)**
- [purefa_hg – Manage hostgroups on Pure Storage FlashArrays](https://docs.ansible.com/ansible/latest/modules/purefa_hg_module.html#purefa-hg-module)
- [purefa_host – Manage hosts on Pure Storage FlashArrays](https://docs.ansible.com/ansible/latest/modules/purefa_host_module.html#purefa-host-module)
- [purefa_info – Collect information from Pure Storage FlashArray](https://docs.ansible.com/ansible/latest/modules/purefa_info_module.html#purefa-info-module)
- [purefa_ntp – Configure Pure Storage FlashArray NTP settings](https://docs.ansible.com/ansible/latest/modules/purefa_ntp_module.html#purefa-ntp-module)
- [purefa_offload – Create, modify and delete NFS or S3 offload targets](https://docs.ansible.com/ansible/latest/modules/purefa_offload_module.html#purefa-offload-module)
- [purefa_pg – Manage protection groups on Pure Storage FlashArrays](https://docs.ansible.com/ansible/latest/modules/purefa_pg_module.html#purefa-pg-module)
- [purefa_pgsnap – Manage protection group snapshots on Pure Storage FlashArrays](https://docs.ansible.com/ansible/latest/modules/purefa_pgsnap_module.html#purefa-pgsnap-module)
- [purefa_phonehome – Enable or Disable Pure Storage FlashArray Phonehome](https://docs.ansible.com/ansible/latest/modules/purefa_phonehome_module.html#purefa-phonehome-module)
- [purefa_ra – Enable or Disable Pure Storage FlashArray Remote Assist](https://docs.ansible.com/ansible/latest/modules/purefa_ra_module.html#purefa-ra-module)
- [purefa_smtp – Configure FlashArray SMTP settings](https://docs.ansible.com/ansible/latest/modules/purefa_smtp_module.html#purefa-smtp-module)
- [purefa_snap – Manage volume snapshots on Pure Storage FlashArrays](https://docs.ansible.com/ansible/latest/modules/purefa_snap_module.html#purefa-snap-module)
- [purefa_snmp – Configure FlashArray SNMP Managers](https://docs.ansible.com/ansible/latest/modules/purefa_snmp_module.html#purefa-snmp-module)
- [purefa_syslog – Configure Pure Storage FlashArray syslog settings](https://docs.ansible.com/ansible/latest/modules/purefa_syslog_module.html#purefa-syslog-module)
- [purefa_user – Create, modify or delete FlashArray local user account](https://docs.ansible.com/ansible/latest/modules/purefa_user_module.html#purefa-user-module)
- [purefa_vg – Manage volume groups on Pure Storage FlashArrays](https://docs.ansible.com/ansible/latest/modules/purefa_vg_module.html#purefa-vg-module)
- [purefa_volume – Manage volumes on Pure Storage FlashArrays](https://docs.ansible.com/ansible/latest/modules/purefa_volume_module.html#purefa-volume-module)
- [purefb_bucket – Manage Object Store Buckets on a Pure Storage FlashBlade](https://docs.ansible.com/ansible/latest/modules/purefb_bucket_module.html#purefb-bucket-module)
- [purefb_ds – Configure FlashBlade Directory Service](https://docs.ansible.com/ansible/latest/modules/purefb_ds_module.html#purefb-ds-module)
- [purefb_dsrole – Configure FlashBlade Management Directory Service Roles](https://docs.ansible.com/ansible/latest/modules/purefb_dsrole_module.html#purefb-dsrole-module)
- [purefb_facts – Collect facts from Pure Storage FlashBlade](https://docs.ansible.com/ansible/latest/modules/purefb_facts_module.html#purefb-facts-module) **(D)**
- [purefb_fs – Manage filesystemon Pure Storage FlashBlade`](https://docs.ansible.com/ansible/latest/modules/purefb_fs_module.html#purefb-fs-module)
- [purefb_info – Collect information from Pure Storage FlashBlade](https://docs.ansible.com/ansible/latest/modules/purefb_info_module.html#purefb-info-module)
- [purefb_network – Manage network interfaces in a Pure Storage FlashBlade](https://docs.ansible.com/ansible/latest/modules/purefb_network_module.html#purefb-network-module)
- [purefb_ra – Enable or Disable Pure Storage FlashBlade Remote Assist](https://docs.ansible.com/ansible/latest/modules/purefb_ra_module.html#purefb-ra-module)
- [purefb_s3acc – Create or delete FlashBlade Object Store accounts](https://docs.ansible.com/ansible/latest/modules/purefb_s3acc_module.html#purefb-s3acc-module)
- [purefb_s3user – Create or delete FlashBlade Object Store account users](https://docs.ansible.com/ansible/latest/modules/purefb_s3user_module.html#purefb-s3user-module)
- [purefb_smtp – Configure SMTP for Pure Storage FlashBlade](https://docs.ansible.com/ansible/latest/modules/purefb_smtp_module.html#purefb-smtp-module)
- [purefb_snap – Manage filesystem snapshots on Pure Storage FlashBlades](https://docs.ansible.com/ansible/latest/modules/purefb_snap_module.html#purefb-snap-module)
- [purefb_subnet – Manage network subnets in a Pure Storage FlashBlade](https://docs.ansible.com/ansible/latest/modules/purefb_subnet_module.html#purefb-subnet-module)



### Vexata

- [vexata_eg – Manage export groups on Vexata VX100 storage arrays](https://docs.ansible.com/ansible/latest/modules/vexata_eg_module.html#vexata-eg-module)
- [vexata_volume – Manage volumes on Vexata VX100 storage arrays](https://docs.ansible.com/ansible/latest/modules/vexata_volume_module.html#vexata-volume-module)



### Zfs

- [zfs – Manage zfs](https://docs.ansible.com/ansible/latest/modules/zfs_module.html#zfs-module)
- [zfs_delegate_admin – Manage ZFS delegated administration (user admin privileges)](https://docs.ansible.com/ansible/latest/modules/zfs_delegate_admin_module.html#zfs-delegate-admin-module)
- [zfs_facts – Gather facts about ZFS datasets](https://docs.ansible.com/ansible/latest/modules/zfs_facts_module.html#zfs-facts-module)
- [zpool_facts – Gather facts about ZFS pools](https://docs.ansible.com/ansible/latest/modules/zpool_facts_module.html#zpool-facts-module)

## System modules

- [aix_devices – Manages AIX devices](https://docs.ansible.com/ansible/latest/modules/aix_devices_module.html#aix-devices-module)
- [aix_filesystem – Configure LVM and NFS file systems for AIX](https://docs.ansible.com/ansible/latest/modules/aix_filesystem_module.html#aix-filesystem-module)
- [aix_inittab – Manages the inittab on AIX](https://docs.ansible.com/ansible/latest/modules/aix_inittab_module.html#aix-inittab-module)
- [aix_lvg – Manage LVM volume groups on AIX](https://docs.ansible.com/ansible/latest/modules/aix_lvg_module.html#aix-lvg-module)
- [aix_lvol – Configure AIX LVM logical volumes](https://docs.ansible.com/ansible/latest/modules/aix_lvol_module.html#aix-lvol-module)
- [alternatives – Manages alternative programs for common commands](https://docs.ansible.com/ansible/latest/modules/alternatives_module.html#alternatives-module)
- [at – Schedule the execution of a command or script file via the at command](https://docs.ansible.com/ansible/latest/modules/at_module.html#at-module)
- [authorized_key – Adds or removes an SSH authorized key](https://docs.ansible.com/ansible/latest/modules/authorized_key_module.html#authorized-key-module)
- [awall – Manage awall policies](https://docs.ansible.com/ansible/latest/modules/awall_module.html#awall-module)
- [beadm – Manage ZFS boot environments on FreeBSD/Solaris/illumos systems](https://docs.ansible.com/ansible/latest/modules/beadm_module.html#beadm-module)
- [capabilities – Manage Linux capabilities](https://docs.ansible.com/ansible/latest/modules/capabilities_module.html#capabilities-module)
- [cron – Manage cron.d and crontab entries](https://docs.ansible.com/ansible/latest/modules/cron_module.html#cron-module)
- [cronvar – Manage variables in crontabs](https://docs.ansible.com/ansible/latest/modules/cronvar_module.html#cronvar-module)
- [crypttab – Encrypted Linux block devices](https://docs.ansible.com/ansible/latest/modules/crypttab_module.html#crypttab-module)
- [dconf – Modify and read dconf database](https://docs.ansible.com/ansible/latest/modules/dconf_module.html#dconf-module)
- [debconf – Configure a .deb package](https://docs.ansible.com/ansible/latest/modules/debconf_module.html#debconf-module)
- [facter – Runs the discovery program facter on the remote system](https://docs.ansible.com/ansible/latest/modules/facter_module.html#facter-module)
- [filesystem – Makes a filesystem](https://docs.ansible.com/ansible/latest/modules/filesystem_module.html#filesystem-module)
- [firewalld – Manage arbitrary ports/services with firewalld](https://docs.ansible.com/ansible/latest/modules/firewalld_module.html#firewalld-module)
- [gather_facts – Gathers facts about remote hosts](https://docs.ansible.com/ansible/latest/modules/gather_facts_module.html#gather-facts-module)
- [gconftool2 – Edit GNOME Configurations](https://docs.ansible.com/ansible/latest/modules/gconftool2_module.html#gconftool2-module)
- [getent – A wrapper to the unix getent utility](https://docs.ansible.com/ansible/latest/modules/getent_module.html#getent-module)
- [group – Add or remove groups](https://docs.ansible.com/ansible/latest/modules/group_module.html#group-module)
- [hostname – Manage hostname](https://docs.ansible.com/ansible/latest/modules/hostname_module.html#hostname-module)
- [interfaces_file – Tweak settings in /etc/network/interfaces files](https://docs.ansible.com/ansible/latest/modules/interfaces_file_module.html#interfaces-file-module)
- [iptables – Modify iptables rules](https://docs.ansible.com/ansible/latest/modules/iptables_module.html#iptables-module)
- [java_cert – Uses keytool to import/remove key from java keystore (cacerts)](https://docs.ansible.com/ansible/latest/modules/java_cert_module.html#java-cert-module)
- [java_keystore – Create or delete a Java keystore in JKS format](https://docs.ansible.com/ansible/latest/modules/java_keystore_module.html#java-keystore-module)
- [kernel_blacklist – Blacklist kernel modules](https://docs.ansible.com/ansible/latest/modules/kernel_blacklist_module.html#kernel-blacklist-module)
- [known_hosts – Add or remove a host from the known_hosts file](https://docs.ansible.com/ansible/latest/modules/known_hosts_module.html#known-hosts-module)
- [listen_ports_facts – Gather facts on processes listening on TCP and UDP ports](https://docs.ansible.com/ansible/latest/modules/listen_ports_facts_module.html#listen-ports-facts-module)
- [locale_gen – Creates or removes locales](https://docs.ansible.com/ansible/latest/modules/locale_gen_module.html#locale-gen-module)
- [lvg – Configure LVM volume groups](https://docs.ansible.com/ansible/latest/modules/lvg_module.html#lvg-module)
- [lvol – Configure LVM logical volumes](https://docs.ansible.com/ansible/latest/modules/lvol_module.html#lvol-module)
- [make – Run targets in a Makefile](https://docs.ansible.com/ansible/latest/modules/make_module.html#make-module)
- [mksysb – Generates AIX mksysb rootvg backups](https://docs.ansible.com/ansible/latest/modules/mksysb_module.html#mksysb-module)
- [modprobe – Load or unload kernel modules](https://docs.ansible.com/ansible/latest/modules/modprobe_module.html#modprobe-module)
- [mount – Control active and configured mount points](https://docs.ansible.com/ansible/latest/modules/mount_module.html#mount-module)
- [nosh – Manage services with nosh](https://docs.ansible.com/ansible/latest/modules/nosh_module.html#nosh-module)
- [ohai – Returns inventory data from Ohai](https://docs.ansible.com/ansible/latest/modules/ohai_module.html#ohai-module)
- [open_iscsi – Manage iSCSI targets with Open-iSCSI](https://docs.ansible.com/ansible/latest/modules/open_iscsi_module.html#open-iscsi-module)
- [openwrt_init – Manage services on OpenWrt](https://docs.ansible.com/ansible/latest/modules/openwrt_init_module.html#openwrt-init-module)
- [osx_defaults – Manage macOS user defaults](https://docs.ansible.com/ansible/latest/modules/osx_defaults_module.html#osx-defaults-module)
- [pam_limits – Modify Linux PAM limits](https://docs.ansible.com/ansible/latest/modules/pam_limits_module.html#pam-limits-module)
- [pamd – Manage PAM Modules](https://docs.ansible.com/ansible/latest/modules/pamd_module.html#pamd-module)
- [parted – Configure block device partitions](https://docs.ansible.com/ansible/latest/modules/parted_module.html#parted-module)
- [pids – Retrieves process IDs list if the process is running otherwise return empty list](https://docs.ansible.com/ansible/latest/modules/pids_module.html#pids-module)
- [ping – Try to connect to host, verify a usable python and return pong on success](https://docs.ansible.com/ansible/latest/modules/ping_module.html#ping-module)
- [puppet – Runs puppet](https://docs.ansible.com/ansible/latest/modules/puppet_module.html#puppet-module)
- [python_requirements_info – Show python path and assert dependency versions](https://docs.ansible.com/ansible/latest/modules/python_requirements_info_module.html#python-requirements-info-module)
- [reboot – Reboot a machine](https://docs.ansible.com/ansible/latest/modules/reboot_module.html#reboot-module)
- [runit – Manage runit services](https://docs.ansible.com/ansible/latest/modules/runit_module.html#runit-module)
- [seboolean – Toggles SELinux booleans](https://docs.ansible.com/ansible/latest/modules/seboolean_module.html#seboolean-module)
- [sefcontext – Manages SELinux file context mapping definitions](https://docs.ansible.com/ansible/latest/modules/sefcontext_module.html#sefcontext-module)
- [selinux – Change policy and state of SELinux](https://docs.ansible.com/ansible/latest/modules/selinux_module.html#selinux-module)
- [selinux_permissive – Change permissive domain in SELinux policy](https://docs.ansible.com/ansible/latest/modules/selinux_permissive_module.html#selinux-permissive-module)
- [selogin – Manages linux user to SELinux user mapping](https://docs.ansible.com/ansible/latest/modules/selogin_module.html#selogin-module)
- [seport – Manages SELinux network port type definitions](https://docs.ansible.com/ansible/latest/modules/seport_module.html#seport-module)
- [service – Manage services](https://docs.ansible.com/ansible/latest/modules/service_module.html#service-module)
- [service_facts – Return service state information as fact data](https://docs.ansible.com/ansible/latest/modules/service_facts_module.html#service-facts-module)
- [setup – Gathers facts about remote hosts](https://docs.ansible.com/ansible/latest/modules/setup_module.html#setup-module)
- [solaris_zone – Manage Solaris zones](https://docs.ansible.com/ansible/latest/modules/solaris_zone_module.html#solaris-zone-module)
- [svc – Manage daemontools services](https://docs.ansible.com/ansible/latest/modules/svc_module.html#svc-module)
- [sysctl – Manage entries in sysctl.conf](https://docs.ansible.com/ansible/latest/modules/sysctl_module.html#sysctl-module)
- [syspatch – Manage OpenBSD system patches](https://docs.ansible.com/ansible/latest/modules/syspatch_module.html#syspatch-module)
- [systemd – Manage services](https://docs.ansible.com/ansible/latest/modules/systemd_module.html#systemd-module)
- [sysvinit – Manage SysV services](https://docs.ansible.com/ansible/latest/modules/sysvinit_module.html#sysvinit-module)
- [timezone – Configure timezone setting](https://docs.ansible.com/ansible/latest/modules/timezone_module.html#timezone-module)
- [ufw – Manage firewall with UFW](https://docs.ansible.com/ansible/latest/modules/ufw_module.html#ufw-module)
- [user – Manage user accounts](https://docs.ansible.com/ansible/latest/modules/user_module.html#user-module)
- [vdo – Module to control VDO](https://docs.ansible.com/ansible/latest/modules/vdo_module.html#vdo-module)
- [xfconf – Edit XFCE4 Configurations](https://docs.ansible.com/ansible/latest/modules/xfconf_module.html#xfconf-module)
- [xfs_quota – Manage quotas on XFS filesystems](https://docs.ansible.com/ansible/latest/modules/xfs_quota_module.html#xfs-quota-module)

## Utilities modules

### Helper

- [meta – Execute Ansible ‘actions’](https://docs.ansible.com/ansible/latest/modules/meta_module.html#meta-module)

### Logic

- [assert – Asserts given expressions are true](https://docs.ansible.com/ansible/latest/modules/assert_module.html#assert-module)
- [async_status – Obtain status of asynchronous task](https://docs.ansible.com/ansible/latest/modules/async_status_module.html#async-status-module)
- [debug – Print statements during execution](https://docs.ansible.com/ansible/latest/modules/debug_module.html#debug-module)
- [fail – Fail with custom message](https://docs.ansible.com/ansible/latest/modules/fail_module.html#fail-module)
- [import_playbook – Import a playbook](https://docs.ansible.com/ansible/latest/modules/import_playbook_module.html#import-playbook-module)
- [import_role – Import a role into a play](https://docs.ansible.com/ansible/latest/modules/import_role_module.html#import-role-module)
- [import_tasks – Import a task list](https://docs.ansible.com/ansible/latest/modules/import_tasks_module.html#import-tasks-module)
- [include – Include a play or task list](https://docs.ansible.com/ansible/latest/modules/include_module.html#include-module)
- [include_role – Load and execute a role](https://docs.ansible.com/ansible/latest/modules/include_role_module.html#include-role-module)
- [include_tasks – Dynamically include a task list](https://docs.ansible.com/ansible/latest/modules/include_tasks_module.html#include-tasks-module)
- [include_vars – Load variables from files, dynamically within a task](https://docs.ansible.com/ansible/latest/modules/include_vars_module.html#include-vars-module)
- [pause – Pause playbook execution](https://docs.ansible.com/ansible/latest/modules/pause_module.html#pause-module)
- [set_fact – Set host facts from a task](https://docs.ansible.com/ansible/latest/modules/set_fact_module.html#set-fact-module)
- [set_stats – Set stats for the current ansible run](https://docs.ansible.com/ansible/latest/modules/set_stats_module.html#set-stats-module)
- [wait_for – Waits for a condition before continuing](https://docs.ansible.com/ansible/latest/modules/wait_for_module.html#wait-for-module)
- [wait_for_connection – Waits until remote system is reachable/usable](https://docs.ansible.com/ansible/latest/modules/wait_for_connection_module.html#wait-for-connection-module)

## Web Infrastructure modules

- [apache2_mod_proxy – Set and/or get members’ attributes of an Apache httpd 2.4 mod_proxy balancer pool](https://docs.ansible.com/ansible/latest/modules/apache2_mod_proxy_module.html#apache2-mod-proxy-module)
- [apache2_module – Enables/disables a module of the Apache2 webserver](https://docs.ansible.com/ansible/latest/modules/apache2_module_module.html#apache2-module-module)
- [deploy_helper – Manages some of the steps common in deploying projects](https://docs.ansible.com/ansible/latest/modules/deploy_helper_module.html#deploy-helper-module)
- [django_manage – Manages a Django application](https://docs.ansible.com/ansible/latest/modules/django_manage_module.html#django-manage-module)
- [ejabberd_user – Manages users for ejabberd servers](https://docs.ansible.com/ansible/latest/modules/ejabberd_user_module.html#ejabberd-user-module)
- [gunicorn – Run gunicorn with various settings](https://docs.ansible.com/ansible/latest/modules/gunicorn_module.html#gunicorn-module)
- [htpasswd – manage user files for basic authentication](https://docs.ansible.com/ansible/latest/modules/htpasswd_module.html#htpasswd-module)
- [jboss – Deploy applications to JBoss](https://docs.ansible.com/ansible/latest/modules/jboss_module.html#jboss-module)
- [jenkins_job – Manage jenkins jobs](https://docs.ansible.com/ansible/latest/modules/jenkins_job_module.html#jenkins-job-module)
- [jenkins_job_info – Get information about Jenkins jobs](https://docs.ansible.com/ansible/latest/modules/jenkins_job_info_module.html#jenkins-job-info-module)
- [jenkins_plugin – Add or remove Jenkins plugin](https://docs.ansible.com/ansible/latest/modules/jenkins_plugin_module.html#jenkins-plugin-module)
- [jenkins_script – Executes a groovy script in the jenkins instance](https://docs.ansible.com/ansible/latest/modules/jenkins_script_module.html#jenkins-script-module)
- [jira – create and modify issues in a JIRA instance](https://docs.ansible.com/ansible/latest/modules/jira_module.html#jira-module)
- [nginx_status_facts – Retrieve nginx status facts](https://docs.ansible.com/ansible/latest/modules/nginx_status_facts_module.html#nginx-status-facts-module) **(D)**
- [nginx_status_info – Retrieve information on nginx status](https://docs.ansible.com/ansible/latest/modules/nginx_status_info_module.html#nginx-status-info-module)
- [rundeck_acl_policy – Manage Rundeck ACL policies](https://docs.ansible.com/ansible/latest/modules/rundeck_acl_policy_module.html#rundeck-acl-policy-module)
- [rundeck_project – Manage Rundeck projects](https://docs.ansible.com/ansible/latest/modules/rundeck_project_module.html#rundeck-project-module)
- [supervisorctl – Manage the state of a program or group of programs running via supervisord](https://docs.ansible.com/ansible/latest/modules/supervisorctl_module.html#supervisorctl-module)
- [taiga_issue – Creates/deletes an issue in a Taiga Project Management Platform](https://docs.ansible.com/ansible/latest/modules/taiga_issue_module.html#taiga-issue-module)



### Ansible_Tower

- [tower_credential – create, update, or destroy Ansible Tower credential](https://docs.ansible.com/ansible/latest/modules/tower_credential_module.html#tower-credential-module)
- [tower_credential_type – Create, update, or destroy custom Ansible Tower credential type](https://docs.ansible.com/ansible/latest/modules/tower_credential_type_module.html#tower-credential-type-module)
- [tower_group – create, update, or destroy Ansible Tower group](https://docs.ansible.com/ansible/latest/modules/tower_group_module.html#tower-group-module)
- [tower_host – create, update, or destroy Ansible Tower host](https://docs.ansible.com/ansible/latest/modules/tower_host_module.html#tower-host-module)
- [tower_inventory – create, update, or destroy Ansible Tower inventory](https://docs.ansible.com/ansible/latest/modules/tower_inventory_module.html#tower-inventory-module)
- [tower_inventory_source – create, update, or destroy Ansible Tower inventory source](https://docs.ansible.com/ansible/latest/modules/tower_inventory_source_module.html#tower-inventory-source-module)
- [tower_job_cancel – Cancel an Ansible Tower Job](https://docs.ansible.com/ansible/latest/modules/tower_job_cancel_module.html#tower-job-cancel-module)
- [tower_job_launch – Launch an Ansible Job](https://docs.ansible.com/ansible/latest/modules/tower_job_launch_module.html#tower-job-launch-module)
- [tower_job_list – List Ansible Tower jobs](https://docs.ansible.com/ansible/latest/modules/tower_job_list_module.html#tower-job-list-module)
- [tower_job_template – create, update, or destroy Ansible Tower job template](https://docs.ansible.com/ansible/latest/modules/tower_job_template_module.html#tower-job-template-module)
- [tower_job_wait – Wait for Ansible Tower job to finish](https://docs.ansible.com/ansible/latest/modules/tower_job_wait_module.html#tower-job-wait-module)
- [tower_label – create, update, or destroy Ansible Tower label](https://docs.ansible.com/ansible/latest/modules/tower_label_module.html#tower-label-module)
- [tower_notification – create, update, or destroy Ansible Tower notification](https://docs.ansible.com/ansible/latest/modules/tower_notification_module.html#tower-notification-module)
- [tower_organization – create, update, or destroy Ansible Tower organizations](https://docs.ansible.com/ansible/latest/modules/tower_organization_module.html#tower-organization-module)
- [tower_project – create, update, or destroy Ansible Tower projects](https://docs.ansible.com/ansible/latest/modules/tower_project_module.html#tower-project-module)
- [tower_receive – Receive assets from Ansible Tower](https://docs.ansible.com/ansible/latest/modules/tower_receive_module.html#tower-receive-module)
- [tower_role – create, update, or destroy Ansible Tower role](https://docs.ansible.com/ansible/latest/modules/tower_role_module.html#tower-role-module)
- [tower_send – Send assets to Ansible Tower](https://docs.ansible.com/ansible/latest/modules/tower_send_module.html#tower-send-module)
- [tower_settings – Modify Ansible Tower settings](https://docs.ansible.com/ansible/latest/modules/tower_settings_module.html#tower-settings-module)
- [tower_team – create, update, or destroy Ansible Tower team](https://docs.ansible.com/ansible/latest/modules/tower_team_module.html#tower-team-module)
- [tower_user – create, update, or destroy Ansible Tower user](https://docs.ansible.com/ansible/latest/modules/tower_user_module.html#tower-user-module)
- [tower_workflow_launch – Run a workflow in Ansible Tower](https://docs.ansible.com/ansible/latest/modules/tower_workflow_launch_module.html#tower-workflow-launch-module)
- [tower_workflow_template – create, update, or destroy Ansible Tower workflow template](https://docs.ansible.com/ansible/latest/modules/tower_workflow_template_module.html#tower-workflow-template-module)



### Sophos_Utm

- [utm_aaa_group – Create, update or destroy an aaa group object in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_aaa_group_module.html#utm-aaa-group-module)
- [utm_aaa_group_info – get info for reverse_proxy frontend entry in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_aaa_group_info_module.html#utm-aaa-group-info-module)
- [utm_ca_host_key_cert – create, update or destroy ca host_key_cert entry in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_ca_host_key_cert_module.html#utm-ca-host-key-cert-module)
- [utm_ca_host_key_cert_info – Get info for a ca host_key_cert entry in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_ca_host_key_cert_info_module.html#utm-ca-host-key-cert-info-module)
- [utm_dns_host – create, update or destroy dns entry in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_dns_host_module.html#utm-dns-host-module)
- [utm_network_interface_address – Create, update or destroy network/interface_address object](https://docs.ansible.com/ansible/latest/modules/utm_network_interface_address_module.html#utm-network-interface-address-module)
- [utm_network_interface_address_info – Get info for a network/interface_address object](https://docs.ansible.com/ansible/latest/modules/utm_network_interface_address_info_module.html#utm-network-interface-address-info-module)
- [utm_proxy_auth_profile – create, update or destroy reverse_proxy auth_profile entry in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_proxy_auth_profile_module.html#utm-proxy-auth-profile-module)
- [utm_proxy_exception – Create, update or destroy reverse_proxy exception entry in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_proxy_exception_module.html#utm-proxy-exception-module)
- [utm_proxy_frontend – create, update or destroy reverse_proxy frontend entry in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_proxy_frontend_module.html#utm-proxy-frontend-module)
- [utm_proxy_frontend_info – create, update or destroy reverse_proxy frontend entry in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_proxy_frontend_info_module.html#utm-proxy-frontend-info-module)
- [utm_proxy_location – create, update or destroy reverse_proxy location entry in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_proxy_location_module.html#utm-proxy-location-module)
- [utm_proxy_location_info – create, update or destroy reverse_proxy location entry in Sophos UTM](https://docs.ansible.com/ansible/latest/modules/utm_proxy_location_info_module.html#utm-proxy-location-info-module)

## Windows modules

- [win_acl – Set file/directory/registry permissions for a system user or group](https://docs.ansible.com/ansible/latest/modules/win_acl_module.html#win-acl-module)
- [win_acl_inheritance – Change ACL inheritance](https://docs.ansible.com/ansible/latest/modules/win_acl_inheritance_module.html#win-acl-inheritance-module)
- [win_audit_policy_system – Used to make changes to the system wide Audit Policy](https://docs.ansible.com/ansible/latest/modules/win_audit_policy_system_module.html#win-audit-policy-system-module)
- [win_audit_rule – Adds an audit rule to files, folders, or registry keys](https://docs.ansible.com/ansible/latest/modules/win_audit_rule_module.html#win-audit-rule-module)
- [win_certificate_store – Manages the certificate store](https://docs.ansible.com/ansible/latest/modules/win_certificate_store_module.html#win-certificate-store-module)
- [win_chocolatey – Manage packages using chocolatey](https://docs.ansible.com/ansible/latest/modules/win_chocolatey_module.html#win-chocolatey-module)
- [win_chocolatey_config – Manages Chocolatey config settings](https://docs.ansible.com/ansible/latest/modules/win_chocolatey_config_module.html#win-chocolatey-config-module)
- [win_chocolatey_facts – Create a facts collection for Chocolatey](https://docs.ansible.com/ansible/latest/modules/win_chocolatey_facts_module.html#win-chocolatey-facts-module)
- [win_chocolatey_feature – Manages Chocolatey features](https://docs.ansible.com/ansible/latest/modules/win_chocolatey_feature_module.html#win-chocolatey-feature-module)
- [win_chocolatey_source – Manages Chocolatey sources](https://docs.ansible.com/ansible/latest/modules/win_chocolatey_source_module.html#win-chocolatey-source-module)
- [win_command – Executes a command on a remote Windows node](https://docs.ansible.com/ansible/latest/modules/win_command_module.html#win-command-module)
- [win_copy – Copies files to remote locations on windows hosts](https://docs.ansible.com/ansible/latest/modules/win_copy_module.html#win-copy-module)
- [win_credential – Manages Windows Credentials in the Credential Manager](https://docs.ansible.com/ansible/latest/modules/win_credential_module.html#win-credential-module)
- [win_defrag – Consolidate fragmented files on local volumes](https://docs.ansible.com/ansible/latest/modules/win_defrag_module.html#win-defrag-module)
- [win_disk_facts – Show the attached disks and disk information of the target host](https://docs.ansible.com/ansible/latest/modules/win_disk_facts_module.html#win-disk-facts-module)
- [win_disk_image – Manage ISO/VHD/VHDX mounts on Windows hosts](https://docs.ansible.com/ansible/latest/modules/win_disk_image_module.html#win-disk-image-module)
- [win_dns_client – Configures DNS lookup on Windows hosts](https://docs.ansible.com/ansible/latest/modules/win_dns_client_module.html#win-dns-client-module)
- [win_dns_record – Manage Windows Server DNS records](https://docs.ansible.com/ansible/latest/modules/win_dns_record_module.html#win-dns-record-module)
- [win_domain – Ensures the existence of a Windows domain](https://docs.ansible.com/ansible/latest/modules/win_domain_module.html#win-domain-module)
- [win_domain_computer – Manage computers in Active Directory](https://docs.ansible.com/ansible/latest/modules/win_domain_computer_module.html#win-domain-computer-module)
- [win_domain_controller – Manage domain controller/member server state for a Windows host](https://docs.ansible.com/ansible/latest/modules/win_domain_controller_module.html#win-domain-controller-module)
- [win_domain_group – Creates, modifies or removes domain groups](https://docs.ansible.com/ansible/latest/modules/win_domain_group_module.html#win-domain-group-module)
- [win_domain_group_membership – Manage Windows domain group membership](https://docs.ansible.com/ansible/latest/modules/win_domain_group_membership_module.html#win-domain-group-membership-module)
- [win_domain_membership – Manage domain/workgroup membership for a Windows host](https://docs.ansible.com/ansible/latest/modules/win_domain_membership_module.html#win-domain-membership-module)
- [win_domain_user – Manages Windows Active Directory user accounts](https://docs.ansible.com/ansible/latest/modules/win_domain_user_module.html#win-domain-user-module)
- [win_dotnet_ngen – Runs ngen to recompile DLLs after .NET updates](https://docs.ansible.com/ansible/latest/modules/win_dotnet_ngen_module.html#win-dotnet-ngen-module)
- [win_dsc – Invokes a PowerShell DSC configuration](https://docs.ansible.com/ansible/latest/modules/win_dsc_module.html#win-dsc-module)
- [win_environment – Modify environment variables on windows hosts](https://docs.ansible.com/ansible/latest/modules/win_environment_module.html#win-environment-module)
- [win_eventlog – Manage Windows event logs](https://docs.ansible.com/ansible/latest/modules/win_eventlog_module.html#win-eventlog-module)
- [win_eventlog_entry – Write entries to Windows event logs](https://docs.ansible.com/ansible/latest/modules/win_eventlog_entry_module.html#win-eventlog-entry-module)
- [win_feature – Installs and uninstalls Windows Features on Windows Server](https://docs.ansible.com/ansible/latest/modules/win_feature_module.html#win-feature-module)
- [win_file – Creates, touches or removes files or directories](https://docs.ansible.com/ansible/latest/modules/win_file_module.html#win-file-module)
- [win_file_version – Get DLL or EXE file build version](https://docs.ansible.com/ansible/latest/modules/win_file_version_module.html#win-file-version-module)
- [win_find – Return a list of files based on specific criteria](https://docs.ansible.com/ansible/latest/modules/win_find_module.html#win-find-module)
- [win_firewall – Enable or disable the Windows Firewall](https://docs.ansible.com/ansible/latest/modules/win_firewall_module.html#win-firewall-module)
- [win_firewall_rule – Windows firewall automation](https://docs.ansible.com/ansible/latest/modules/win_firewall_rule_module.html#win-firewall-rule-module)
- [win_format – Formats an existing volume or a new volume on an existing partition on Windows](https://docs.ansible.com/ansible/latest/modules/win_format_module.html#win-format-module)
- [win_get_url – Downloads file from HTTP, HTTPS, or FTP to node](https://docs.ansible.com/ansible/latest/modules/win_get_url_module.html#win-get-url-module)
- [win_group – Add and remove local groups](https://docs.ansible.com/ansible/latest/modules/win_group_module.html#win-group-module)
- [win_group_membership – Manage Windows local group membership](https://docs.ansible.com/ansible/latest/modules/win_group_membership_module.html#win-group-membership-module)
- [win_hostname – Manages local Windows computer name](https://docs.ansible.com/ansible/latest/modules/win_hostname_module.html#win-hostname-module)
- [win_hosts – Manages hosts file entries on Windows](https://docs.ansible.com/ansible/latest/modules/win_hosts_module.html#win-hosts-module)
- [win_hotfix – Install and uninstalls Windows hotfixes](https://docs.ansible.com/ansible/latest/modules/win_hotfix_module.html#win-hotfix-module)
- [win_http_proxy – Manages proxy settings for WinHTTP](https://docs.ansible.com/ansible/latest/modules/win_http_proxy_module.html#win-http-proxy-module)
- [win_iis_virtualdirectory – Configures a virtual directory in IIS](https://docs.ansible.com/ansible/latest/modules/win_iis_virtualdirectory_module.html#win-iis-virtualdirectory-module)
- [win_iis_webapplication – Configures IIS web applications](https://docs.ansible.com/ansible/latest/modules/win_iis_webapplication_module.html#win-iis-webapplication-module)
- [win_iis_webapppool – Configure IIS Web Application Pools](https://docs.ansible.com/ansible/latest/modules/win_iis_webapppool_module.html#win-iis-webapppool-module)
- [win_iis_webbinding – Configures a IIS Web site binding](https://docs.ansible.com/ansible/latest/modules/win_iis_webbinding_module.html#win-iis-webbinding-module)
- [win_iis_website – Configures a IIS Web site](https://docs.ansible.com/ansible/latest/modules/win_iis_website_module.html#win-iis-website-module)
- [win_inet_proxy – Manages proxy settings for WinINet and Internet Explorer](https://docs.ansible.com/ansible/latest/modules/win_inet_proxy_module.html#win-inet-proxy-module)
- [win_lineinfile – Ensure a particular line is in a file, or replace an existing line using a back-referenced regular expression](https://docs.ansible.com/ansible/latest/modules/win_lineinfile_module.html#win-lineinfile-module)
- [win_mapped_drive – Map network drives for users](https://docs.ansible.com/ansible/latest/modules/win_mapped_drive_module.html#win-mapped-drive-module)
- [win_msg – Sends a message to logged in users on Windows hosts](https://docs.ansible.com/ansible/latest/modules/win_msg_module.html#win-msg-module)
- [win_netbios – Manage NetBIOS over TCP/IP settings on Windows](https://docs.ansible.com/ansible/latest/modules/win_netbios_module.html#win-netbios-module)
- [win_nssm – Install a service using NSSM](https://docs.ansible.com/ansible/latest/modules/win_nssm_module.html#win-nssm-module)
- [win_optional_feature – Manage optional Windows features](https://docs.ansible.com/ansible/latest/modules/win_optional_feature_module.html#win-optional-feature-module)
- [win_owner – Set owner](https://docs.ansible.com/ansible/latest/modules/win_owner_module.html#win-owner-module)
- [win_package – Installs/uninstalls an installable package](https://docs.ansible.com/ansible/latest/modules/win_package_module.html#win-package-module)
- [win_pagefile – Query or change pagefile configuration](https://docs.ansible.com/ansible/latest/modules/win_pagefile_module.html#win-pagefile-module)
- [win_partition – Creates, changes and removes partitions on Windows Server](https://docs.ansible.com/ansible/latest/modules/win_partition_module.html#win-partition-module)
- [win_path – Manage Windows path environment variables](https://docs.ansible.com/ansible/latest/modules/win_path_module.html#win-path-module)
- [win_pester – Run Pester tests on Windows hosts](https://docs.ansible.com/ansible/latest/modules/win_pester_module.html#win-pester-module)
- [win_ping – A windows version of the classic ping module](https://docs.ansible.com/ansible/latest/modules/win_ping_module.html#win-ping-module)
- [win_power_plan – Changes the power plan of a Windows system](https://docs.ansible.com/ansible/latest/modules/win_power_plan_module.html#win-power-plan-module)
- [win_product_facts – Provides Windows product and license information](https://docs.ansible.com/ansible/latest/modules/win_product_facts_module.html#win-product-facts-module)
- [win_psexec – Runs commands (remotely) as another (privileged) user](https://docs.ansible.com/ansible/latest/modules/win_psexec_module.html#win-psexec-module)
- [win_psmodule – Adds or removes a Windows PowerShell module](https://docs.ansible.com/ansible/latest/modules/win_psmodule_module.html#win-psmodule-module)
- [win_psrepository – Adds, removes or updates a Windows PowerShell repository](https://docs.ansible.com/ansible/latest/modules/win_psrepository_module.html#win-psrepository-module)
- [win_rabbitmq_plugin – Manage RabbitMQ plugins](https://docs.ansible.com/ansible/latest/modules/win_rabbitmq_plugin_module.html#win-rabbitmq-plugin-module)
- [win_rds_cap – Manage Connection Authorization Policies (CAP) on a Remote Desktop Gateway server](https://docs.ansible.com/ansible/latest/modules/win_rds_cap_module.html#win-rds-cap-module)
- [win_rds_rap – Manage Resource Authorization Policies (RAP) on a Remote Desktop Gateway server](https://docs.ansible.com/ansible/latest/modules/win_rds_rap_module.html#win-rds-rap-module)
- [win_rds_settings – Manage main settings of a Remote Desktop Gateway server](https://docs.ansible.com/ansible/latest/modules/win_rds_settings_module.html#win-rds-settings-module)
- [win_reboot – Reboot a windows machine](https://docs.ansible.com/ansible/latest/modules/win_reboot_module.html#win-reboot-module)
- [win_reg_stat – Get information about Windows registry keys](https://docs.ansible.com/ansible/latest/modules/win_reg_stat_module.html#win-reg-stat-module)
- [win_regedit – Add, change, or remove registry keys and values](https://docs.ansible.com/ansible/latest/modules/win_regedit_module.html#win-regedit-module)
- [win_region – Set the region and format settings](https://docs.ansible.com/ansible/latest/modules/win_region_module.html#win-region-module)
- [win_regmerge – Merges the contents of a registry file into the Windows registry](https://docs.ansible.com/ansible/latest/modules/win_regmerge_module.html#win-regmerge-module)
- [win_robocopy – Synchronizes the contents of two directories using Robocopy](https://docs.ansible.com/ansible/latest/modules/win_robocopy_module.html#win-robocopy-module)
- [win_route – Add or remove a static route](https://docs.ansible.com/ansible/latest/modules/win_route_module.html#win-route-module)
- [win_say – Text to speech module for Windows to speak messages and optionally play sounds](https://docs.ansible.com/ansible/latest/modules/win_say_module.html#win-say-module)
- [win_scheduled_task – Manage scheduled tasks](https://docs.ansible.com/ansible/latest/modules/win_scheduled_task_module.html#win-scheduled-task-module)
- [win_scheduled_task_stat – Get information about Windows Scheduled Tasks](https://docs.ansible.com/ansible/latest/modules/win_scheduled_task_stat_module.html#win-scheduled-task-stat-module)
- [win_security_policy – Change local security policy settings](https://docs.ansible.com/ansible/latest/modules/win_security_policy_module.html#win-security-policy-module)
- [win_service – Manage and query Windows services](https://docs.ansible.com/ansible/latest/modules/win_service_module.html#win-service-module)
- [win_share – Manage Windows shares](https://docs.ansible.com/ansible/latest/modules/win_share_module.html#win-share-module)
- [win_shell – Execute shell commands on target hosts](https://docs.ansible.com/ansible/latest/modules/win_shell_module.html#win-shell-module)
- [win_shortcut – Manage shortcuts on Windows](https://docs.ansible.com/ansible/latest/modules/win_shortcut_module.html#win-shortcut-module)
- [win_snmp – Configures the Windows SNMP service](https://docs.ansible.com/ansible/latest/modules/win_snmp_module.html#win-snmp-module)
- [win_stat – Get information about Windows files](https://docs.ansible.com/ansible/latest/modules/win_stat_module.html#win-stat-module)
- [win_tempfile – Creates temporary files and directories](https://docs.ansible.com/ansible/latest/modules/win_tempfile_module.html#win-tempfile-module)
- [win_template – Template a file out to a remote server](https://docs.ansible.com/ansible/latest/modules/win_template_module.html#win-template-module)
- [win_timezone – Sets Windows machine timezone](https://docs.ansible.com/ansible/latest/modules/win_timezone_module.html#win-timezone-module)
- [win_toast – Sends Toast windows notification to logged in users on Windows 10 or later hosts](https://docs.ansible.com/ansible/latest/modules/win_toast_module.html#win-toast-module)
- [win_unzip – Unzips compressed files and archives on the Windows node](https://docs.ansible.com/ansible/latest/modules/win_unzip_module.html#win-unzip-module)
- [win_updates – Download and install Windows updates](https://docs.ansible.com/ansible/latest/modules/win_updates_module.html#win-updates-module)
- [win_uri – Interacts with webservices](https://docs.ansible.com/ansible/latest/modules/win_uri_module.html#win-uri-module)
- [win_user – Manages local Windows user accounts](https://docs.ansible.com/ansible/latest/modules/win_user_module.html#win-user-module)
- [win_user_profile – Manages the Windows user profiles](https://docs.ansible.com/ansible/latest/modules/win_user_profile_module.html#win-user-profile-module)
- [win_user_right – Manage Windows User Rights](https://docs.ansible.com/ansible/latest/modules/win_user_right_module.html#win-user-right-module)
- [win_wait_for – Waits for a condition before continuing](https://docs.ansible.com/ansible/latest/modules/win_wait_for_module.html#win-wait-for-module)
- [win_wait_for_process – Waits for a process to exist or not exist before continuing](https://docs.ansible.com/ansible/latest/modules/win_wait_for_process_module.html#win-wait-for-process-module)
- [win_wakeonlan – Send a magic Wake-on-LAN (WoL) broadcast packet](https://docs.ansible.com/ansible/latest/modules/win_wakeonlan_module.html#win-wakeonlan-module)
- [win_webpicmd – Installs packages using Web Platform Installer command-line](https://docs.ansible.com/ansible/latest/modules/win_webpicmd_module.html#win-webpicmd-module)
- [win_whoami – Get information about the current user and process](https://docs.ansible.com/ansible/latest/modules/win_whoami_module.html#win-whoami-module)
- [win_xml – Manages XML file content on Windows hosts](https://docs.ansible.com/ansible/latest/modules/win_xml_module.html#win-xml-module)