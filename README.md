
# AWS Solutions Architect Professional - Notes
> Preparation notes for the AWS Certified Solutions Architect Professional examination

---

## Supplementary Reading List

- [Reading List](#readinglist)

## Table of Contents 

- [Internal DNS](#InternalDNS)
- [FlowLogs](#FlowLogs)
- [Internal DNS](#InternalDNS)
- [SSH EC2](#SSH_EC2)
- [Sharing resources across AWS ACCOUNTS](#Sharing_resources_across_AWS-ACCOUNTS)
- [VPC Router](#VPCRouter)
- [Routing from on-prem to VPC](#Routing_from_on-prem_to_VPC)
- [Routing VPC to on-prem](#Routing_vpc_to_on-prem)
- [Configuring On-prem DNS (DHCP)](#Configuring_on-prem_DNS_with_DHCP)
- [NAT Gateway](#nat_gateway)
- [DNS EC2](#DNS_EC2)
- [EGRESS Gateway](#EGRESS_GW)
- [EGRESS Gateway Creation](#EGress_GW_creation)
- [Network Wildcard](#Network_wildcards)
- [NACL](#NACL)
- [Internet Gateway](#internet_gateway)
- [Bastion Host](#bastion_host)
- [Private Subnet](#private_subnet)
- [Public Subnet](#public_subnet)
- [NACL contd](#NACL_contd)
- [VPC Flow Logs](#vpc_flow_logs)
- [VPC Gateway Endpoints](#vpc_gateway_endpoints)
- [VPC Interface Endpoints](#vpc_interface_endpoint)
- [VPC Peering](#vpc_peering)
- [VPC Peering Cross Region](#vpc_peering_cross_region)
- [VPC Peering contd](#vpc_peering_contd)
- [VPN Site to Site](#vpn_site_to_site)
- [Route table order of precedence](#Route_table_order_of_precedence)
- [VPN versus Direct Connect](#vpn_versus_direct_connect)
- [Direct Connect](#direct_connect)
- [Direct Connect Public VIF](#direct_connect_public_VIF)
- [Direct Connect Private VIF](#direct_connect_private_VIF)
- [Direct Connect Gateway](#direct_connect_gateway_new)
- [AWS Transit Gateway](#AWS_Transit_Gateway)
- [Creating Transit Gatewat](#Creating_Transit_Gateway)
- [Connect EC2 to S3 bucket](#connect_ec2_instance_to_s3_bucket)
- [Create VPC endpoint between EC2 & S3](#create_vpc_endpoint_between_ec2_and_s3)
- [Peering Cross Region](#peering_across_regions)
- [AWS Security KMS](#aws_security_KMS)
- [KMS Commands](#kms_commands)
- [CLOUD HSM](#cloud_HSM_hardware-security-module)
- [AWS ACM](#AWS_acm)
- [AWS Directory Service](#AWS_Directory-service)
- [AWS_WAF](#AWS_WAF)
- [AWS_Guard-Duty](#AWS_Guard-Duty)
- [EC2](#EC2)
- [AMIs](#AMIs)
- [EC2 and virtualization](#EC2_and_virtualization)
- [EC2 families](#EC2_families)
- [EC2_storage](#EC2_storage)
- [IOPS](#IOPS)
- [Choosing EBS](#Choosing_EBS)
- [EBS snapshots](#EBS_snapshots)
- [EC2 instance profiles and roles](#EC2_instance_Profiles_and_roles)
- [placement_groups](#placement_groups)
- [EC2 CloudWatch](#EC2_CloudWatch)
- [RAID and EBS volumes OR instance backed volumes](#RAID_and_EBS_volumes_OR_instance_backed_volumes)
- [Restore files from EBS volume](#Restore_files_from_EBS_volume)
- [containers ECS](#containers_ECS)
- [ECS architecture](#ECS_architecture)
- [ECS permissions](#ECS_permissions)
- [Lambda](#Lambda)
- [Lambda Layers](#Lambdalayers)
- [API Gateway](#apigateway)
- [AZ zones](#AZ_zones)
- [AWS service resilence](#AWS_service_resilence)
- [EC2 and multiAZ](#EC2_and_multiAZ)
- [stateless architectures](#stateless_architectures)
- [scaling applications billing models](#scaling_applications_billing_models)
- [AMI baking](#AMI_baking)
- [Bootstrapping userdata](#Bootstrapping_userdata)
- [ASG](#ASGs)
- [Implemeneting ASG](#Implemeneting-ASG)
- [Multi AZ](#Multi_AZ)
- [ELB](#ELB)
- [ELB arch](#ELB_arch)
- [Classic LB](#Classic_LB)
- [Application LB](#Application_LB)
- [Network LB](#Network_LB)
- [ELB via Cli](#elb_via_cli)
- [proxy protocol ELB and NGINX](#proxy_protocol_ELB_and_NGINX)
- [Cloudfront](#cloudfront)
- [Cloudfront distributions](#Cloudfront_distributions)
- [Cloudfront custom_origins](#Cloudfront_custom_origins)
- [cloudfront security](#cloudfront_security)
- [Cloudfront signed url & cookies](#Cloudfront_signed_url&cookies)
- [cloudfront restrictions](#cloudfront_restrictions)
- [field level encryption](#field_level_encryption)
- [Optimizing caching](#Optimizing_caching)
- [Lambda@Edge](#Lambda@Edge)
- [Cloudfront reporting monitoring](#Cloudfront_reporting_monitoring)
- [Route53](#Route_53)
- [route53 advanced routing](#route53_advanced_routing)
- [S3 architecture](#S3_architecture)
- [s3 static website](#s3_static_website)
- [s3 access control](#s3_access_control)
- [s3 storage tiers](#s3_storage_tiers)
- [s3 lifecycle rules](#s3_lifecycle_rules)
- [s3 object locking](#s3_object_locking)
- [s3 access control](#s3_access_control)
- [s3 cross region_replication](#s3_cross_region_replication)
- [s3 encryption](#s3_encryption)
- [s3 performance](#s3_performance)
- [glacier](#glacier)
- [file commands](#file_commands)
- [EFS](#EFS)
- [EFS performance](#EFS_performance)
- [fsx architecture](#fsx_architecture)
- [storage gateway](#storage_gateway)
- [databases self managed](#databases_self_managed)
- [database RDMS NOSQL](#database_RDMS_NOSQL)
- [Elasticache](#Elasticache)
- [Amazon_RDS](#Amazon_RDS)
- [Aurora_architecture](#Aurora_architecture)
- [aurora_global_database](#aurora_global_database)
- [aurora_serverless](#aurora_serverless)
- [athena](#athena)
- [dynamodb](#dynamodb)
- [dynamodb_contd](#dynamodb_contd)
- [advanced_dynamodb](#advanced_dynamodb)


- [amazon_neptune](#amazon_neptune)
- [QLDB](#QLDB)
- [documentdb](#documentdb)
- [mapreduce](#mapreduce)
- [EMR](#EMR)
- [EMR_contd](#EMR_contd)
- [EMR_performance](#EMR_performance)
- [kinesis](#kinesis)
- [kinesis_firehose](#kinesis_firehose)
- [kinesis_data_analytics](#kinesis_data_analytics)
- [AWS_Quicksight](#AWS_Quicksight)
- [redshift](#redshift)
- [redshift_recovery](#redshift_recovery)
- [aws_iot](#aws_iot)
- [Elasticsearch](#Elasticsearch)
- [cloudwatch](#cloudwatch)
- [cloudwatch_logs](#cloudwatch_logs)
- [cloudtrail](#cloudtrail)
- [route53_logging](#route53_logging)
- [s3_logging](#s3_logging)



## InternalDNS
* 1. Create hosted zone
* 2. Assocaite with VPC , select type Private hosted zone
* 3. Create record set using private IP address of EC2
* 4. Use nslookup calling record set name and verify name resolution

# FlowLogs
* Can be enabled at three levels (VPC, subnet and resource). Collects metadata about the networking interface traffic. Does not log request body. Creates log file for each ENI. Does not log metadata requests in EC2 (these requests are isolated inside EC2 instance)

# SSH_EC2
* download key pair
* chmod 600
* connect using ec2-user

# Sharing_resources_across_AWS-ACCOUNTS
* use AZ ID which is the physical id of the AZ. The AZ name on the other hand cna be different between accounts although underneath the hood it points at same physical infrastructure. Therefore choose AZ Id

# VPCRouter
* has default router which occupies single IP address ( network +1 address)
E.g if IPv4 cidr block is 10.10.80.0/20 then router is 10.10.80.1
* VPC router highly available
* Route table defines how subnet handles traffic when it arrives at interface
* Every VPC has a main route table
* Subents which do not have a custom route table are assoicated with the default VPC route table
* One route table assigned per VPC
* Every route table starts with local route which can't be changed or deleted
* All resources created within VPC can communicate unless network ACLS used
* Route tables are processed in order of precedence. The higher the CIDR range

# Routing_from_on-prem_to_VPC
* Use VPC inbound endpoint
* highly available
* resolves internal only DNS names
* Lets on-prem resources connect to the inbound endpoint which routes to Route53 resolver and resolves to any of the internal only DNS

# Routing_vpc_to_on-prem
* use VPC outbound endpoint
* create rules which decide how to forward DNS requests for specific target IP addresses which might be on-prem
* when routing between VPC and on-premise networks inbound/outbound endpoints are the recommended approach

# Configuring_on-prem_DNS_with_DHCP
* create dhcp options set using domain name and name server IP address
* select the EC2 and edit dhcp option set
* restart the ec2 isntance
* when the instance restarts it will automtically use the dhcp option set over route 53 to connect to on-prem DNS server

# nat_gateway
* allows 10s or 100s of machines access the internet with same IP address. Eases congestion in IPv4 address space. 
* Cant use Nat gateway with ipv6
* nat gateway has a public IP address
* When NAT receives request from internal IP it converts to its public IP but does'nt allow conversion in teh other direction
* Its a managed service
* resides in public subnethas elastic IP address ( which is static)
* Not highly available so for HA you need to create instance in each AZ
* NAT GW allows you to connect to public internet, S3, DynamoDB, 
* Does not allow port forward
* Does network address translation and keeps record

# DNS_EC2
* resolver + 2. DNS server address also know as R53 resolver and only accessible withing the VPC
* Public DNS - resolves to ipv4 public address when called from outside AWS. When called internally it resolves to the internal DNS
Private DNS - internal network interface of EC2 and not accessible from outside AWS

# EGRESS_GW
* for ipv6. 
* Each IPVC resource automatically gets its own ipv6 public address
* Cant use NAT gateways with ipv6
* Egress GW allows ipv6 service speak to public internet
* By default ipvc not allocated cidr blocks in VPC creation

# EGress_GW_creation
* 1. need ipv6 cidr block allocation to vpc
* 2. need ipv6 allocation to subnet
* 3. need to allocate ipv6 to the instance
* 4. need egress only gateway  and attached to VPC

# Network_wildcards
* IPv4 0.0.0.0/0
* IPV6 ::/0

# Using_NAT 
* 1. Create Nat GW
* 2. Associate subnet ( private subnets in AZ)
* 3. Create Route table for each AZ and associate with private subnets in each AZ
* 4. Associate NAT in each AZ with private subnets

# NACL
* Network ACL's do not apply when communicating between EC2s in the same subnet

# internet_gateway
* type of NAT that uses static NAT 

# bastion_host
* Communicates with outside world using IGW which handles translation between internal address and public IP
* Has public subnet
* Public IP
* Configured to accept public traffic
* Allows connections from bastion host into private network subnets
* You can use more complicated security to  link your corporate security provider
* You can restrict based on specific ssh key or IP address

# private_subnet
* cant communicate with public internet or public zone services like S3 , Cloudwatch, dynamoDB, starts

# public_subnet 
* Has internet gateway
* Has route table pointing at internet gateway
* add 0.0.0.0/0 to IGW represents lowest prefix and all traffic
* Modify subnet association in route table and addd desired subnets.
* Doing this removes the default table association for each subnet
* Subnet cant only have 1 route table associated with it
* Option to auto-assign IP address in VPC for new resources (ec2)

# NACL_contd
* can only deal with individual IP addresses or CIDR block ranges and not resources names like security groups
* NACL do not impact resources in same subnet
* You can assoicate NACL with multiple subnets
* Each subnet can only have a single NACL
* If two identical rules exist but DENY exists then DENY will be acted 
* Rules processed in order of priority
* NACL handles responses using ephemeral port ranges
* Request and response are handled independently 
* It is stateless - cant differentiate if request is a response or the initial request
* Outbound requests when internal request is destined for outside subnet boundary
* NACL operate in space around a subnet
* Every VPC has a default acl and is associated with any subnet in that vpc that does not have its own ACL
* By default NACL allows all traffic in both directions

# vpc_flow_logs
* can take 5-15 minutes to show up in cloudwatch logs after traffic and log created
* when writing to an S3 bucket AWS automatically updates the bucket policy to allow VPC flow logs to write to the bucket
* VPC Flow logs can write to several sources from cloudwatch to S3
* Use Athena to run queries against flow logs stored in S3

# vpc_gateway_endpoints
* 10GB per second bandwidth
* s3 and dynamodb only
* NEED TO BE INSIDE vpc TO UTILIZE
* gateway and gateway endpoints exist inside VPC ( not inside subnet)
* can be referenced route table
* tied to a service and vpc
* you can associate polices with gateway endpoints
* you can restrict policies of resources so they can only be accessed by a particular VPCendpoint
* They appear in route table with pl-79878979 (unique number) ( prefix list which is a representation of all the IP addresses at this public endpoint (so s3 for example) - the public address space for the service in that region)
* With gateway endpoint you can provide access to services running in the aws public area without giving access to the wider internet
* Using gateway endpoints you can create completely private storage for a specific VPC
* Can be secured using policies not security groups

# vpc_interface_endpoint
* 10GB per second bandwidth
* Support majority of AWS public services
* Utlize DNS or private DNS
* ENI'services
* different to gateway endpoints as they do not have entry in route table
* instead puts phsyical entity in specific subnet
* They occupy a subnet as a physical object/ network interface
* They are not highly available so need to create across all AZs 
* Uses private link to provision
* Create endpoint network interfaces inside your VPC
* Can carry traffic to remote vendor or remote VPC over secure private communication channel
* Can be secured using security groups ( interface endpoints are network level devices)
* Interface endpoints comes with its own set of DNS names - which resolves to internally IP address. 
    * There are DNS names for each AZ and also one for the regio
* By default hostnames resolve to the public IP addresses of SQS, s3 etc 
* You can enable private DNS names to utilize the Route 53 resolver which once enabled means Route 53 will respond when any of teh public hostnames are called by returning the internal DNS names. This means you do not need to modify any of your applications using the public hostnames when you want to enforce use of the interface endpoint

# vpc_peering
* accounts limit blast radius, isolated
* connect vpc's with peering
* highly performant , resilent and easy to implement solution to link VPC at network level
* 4 steps to make VPC peering work
    * 1. Create Peer, requires invite and accept. This creates VPC peer object between 2 accounts (requestor is where VPC is created. Need to make sure no overalpping cidr blocks. peering request needs to be accepted)
    * 2. Configure route tables of any subnets at either end of the VPC connection (which you want to participate in the peering connection) to allow communication between VPCs. By default subnet will only have local route (10.0.0.0/16). Need to add the cidr range for the remote VPC and then select peering connection and select the new peering connection. Do the same in the remote VPC
    * 3. Configure security entities (ensure none of the NACL prevent the peering connection). Configure security groups around instances you are connecting to and check rules. One option is to create a rule that allows all traffic from cidr block of remote VPC.
    ** If the peering connection is in the same region then we can reference the remote security group in the local vpc security group when creating inbound rules ( this is a logical reference). This can also be done for security groups in different accounts using the security group identfiier and the aws account number. This process however does not work across regions
    * 4. You also need to make sure the DNS resolution is working ( if required)
* Every VPC peer gets unique id
* private dns hostnames can be resolved and is enabled by default
* Uses private AWS networking

# vpc_peering_cross_region
* You need the vpc id of the remote VPC
* You cant refer to security group so create subnet rule allowing all traffic 10.0.0.0/16
* does not support ipv6
* security group logical reference does not work
* private dns hostnames can be resolved but must be enabled
* Uses AWS private backbone ( has some latency)
* Fuly encrypted

# vpc_peering_contd
* routing is not transitive
* You can enable requestor and acceptor DNS resolution. Which allows each VPC to resolve DNS of requestor VPC hosts to priavte IP addresses

# vpn_site_to_site
* fully encrypted transit path across internet
* ipv4
* known as customer gateway ( represents physical piece of hardware on customer side) - router capable of IPsec vpn connectivity using either static or dynamic routing
* Create customer gateway for every physical customer router you have on-premise
* static routing - tell either side what subnets are available 
* dynamic routing ( recommended for production systems) - no need to hardcode information and instead infer it dynamically using bgp ( allowing to exchange ip addresses for subnets on each side of the connection)
* BGP ( dynamica routing) requires user enters BGP ASN unique ID or if none assigned use a private ASN which can be in the range 64512-65534
* Relies on presence of Virtual Private Gateway which us attached to a specific VPC
* One Virtual Private Gateway per VPC
* Virtual Private Gateway can act as the termination point for many VPN connections
* VPG acts as the endpoint for the VPN tunnels
* Once VPG created next need to create VPN connection which links the customer gateways
* Number of configuration options (No HA ( 1 Tunnels), AWS HA(2 Tunnels in diff AZ), FULL HA (VPN connections between each customer gateway and 2 Tunnels in diff AZ))
* Full HA requires dynamic routing
    * 1 Virtual Private gateway
    * 2 VPN connections
    * 2 Customer Gateways which are connected
    * 4 Tunnels (2 for each VPN connection and in different AZ)
* once vpn connection created next step is to download the configuration (via download config option and select Generic vendor)
* configure router ( home router for example) choosing site-to-site vpn option. Select manual ipsec. update advanced options to match downloaded config secuirty options. Peer ip address is the Virtual Private Gateway ip
* after updating router on-premise then update the route table for the instance making the connection and include the IP address of the on-premise router and choose virtual private gateway as the target. You can also enable route propagation


# Route_table_order_of_precedence
* routing - local route always takes priority
* routes with the highest prefix (cidr range) are favored 
* if two routes with identical network then any static routes take precedence over propagted
* direct connect always preferred over VPn
* static vpn favored over dynamic
* finally dynamic vpn


# vpn_versus_direct_connect
* vpn can be configured in a matter of minutes
* vpn is cheap
* vpn per hour cost/data charge ( higher than direct connect)
* vpn do use encryption end to end and there is a cost for using this
* vpn performance limited by internet under higher loads

# direct_connect
* physical competitor to VPN
* connects customer gateway through virtual private gateway
* private connection, stable, performant
* you can choose connection speeds ( between 1 10 gigabits)
* single low fibre
* you require a router capable of using BGP MV5 AUTH and using vlans
* you are ordering a port ( a single port at a dx location)
* once allocated you get a lower-CFA (letter of authorisation from connecting facility )
* you also need router in dx location ( your own or provided)
* you end up with a cable between you customer gateway router and the dx location router
* you cna order less than 1GB through a direct connect partner - called hosted direct connect connection
* direct path between on-prem and aws dx location
* reduced network cost ( cheaper than ISPs)
* lower rate than VPN for data transfer
* takes weeks/months to setup
* increase network consistency
* dx locations belong to a specific AWS region 
* once we get a lower-cfa we can implement cross connection (physical cable between dxlocation and customer gateway on premise)
* Once cross connect in place we can create public or private virtual interfaces
* connections over direct connect are unencrypted
* there is a port charge
* you are charged for data transfer out of direct connect
* useful when data in the terabytes
* BGP advertised routes always favoured over VPN advertised routes
* VPN can be configured as backup for direct connect setup

# direct_connect_public_VIF 
* operate in a single region
* capable of accessing public zone endpoints ( s3 etc in any region)
* cant use public VIF to access the internet
* direct connect public VIF still better than the public internet in terms of latency even if you are making requests internationally 
* customer publi VLAN

# direct_connect_private_VIF
* limited to regions - can only connect to virtual private gateway in the same region
* one option is to layer a VPN connection over your direct connect infrastructure giving access to public and private gateways
* 1:1 relationship between Private VIF and customer private VLAN

# direct_connect_gateway_new
* allows you to create direct connect gateway which can abstract details of each private VIF from customer private VLAN. This allows customer to connect to VIFs across any VPC and any region by relying on BGP in the Direct Connect Gateway
* customer only connects with Direct COnnect Gateway and doesnt need to worry about each private VIF
* not transitive device ( supported VPCs cannot communicate unless explicitly peered)

# AWS_Transit_Gateway
* Adds additional capability over virtual private gateway ad vpc peers
* we can connect vpc peers and vpn to Transit Gateway which provides transitive behavior ( hub and spoke)
* Transit gateway has multiple route tables allowing complex routing hierarchies to be defined from true hub and spoke to edge consolidation and anywhere in between
* Can link different networks in different AWS accounts
* Now supports Direct Connect (introducing a new virtual interface called the transit virtual interface to support connectivity to AWS Transit Gateway)
* vpn and vpc attachments are placed in AZs, adding routing to that AZ. You can add support for each AZ in the VPC
* Supports peering connections between Gateways in many AWS regions
* Support DNS resolution
* Can have default route table assoication and propagation

# Creating_Transit_Gateway
* Create Transit Gatway attachments
* Select attachment type (vpc or vpn)
* Give it a name
* Enable DNS support
* Choose IPV6 support or not
* Choose VPC id
* Select subnets and AZs
* As VPC attachements are added to Transit gateway there CIDR ranges are added to Transit Gateway route table
* For static VPN the route needs
* Finally update route tables for subnets to allow home network of vpn with target of transit gateway. Only necessary for static vpn

# connect_ec2_instance_to_s3_bucket 
* for public subnet use internet gateway
* from private subnet use VPC enpoint in preference to NAT gateway
* vpc endpoint connects directy to se as it doesnt use public internet so better latency also
* subnet is public when it has a route to IGW

# create_vpc_endpoint_between_ec2_and_s3
* create new endpoint
* select s3 service names
* select vpc 
* configure route tables by selecting private route table id associated with private subnet which you want to update
* Choose the default policy
* Create and verify route table associated with private subnet making sure prefix list (with ip addresses S3 uses) for VPC endpoint is added . Also double check route table associated with correct subnets

# peering_across_regions
* use VPC id for peering target ( acceptor)
* setup route table
* plugin route for requestor vpc in other region and select peering connection
* do the same for public route table in requestor vpc
* add route with destination IP of vpc in remote region and select peering connection
* chair key pair between regions ( create key pair in acceptor vpc , download the key pair, then in requestor vpc import key pair under network and security section of ec2 by providing public key)
* create ec2 instance in requestor vpc and choose existing key pair when launching
* use ssh -A to propagate SSH key between acceptor EC2 and requestr EC2 in different regions. Privatley connected and not using public internet

# aws_security_KMS
* CMK - capable encrypt up to 4k data
* CMK represents one or more backing keys ( like a shortcut)
* regional service
* CMK never leaves the service therefore never leave the region, never leave KMS , never leave hardware
* CMK are stored securely internally and you only interact via apis 
* Access to the CMK managed through policy
* Key alias - like a shortcut. Regional based so aliases can be same name in different regions but underneath they will refer to different cmks
* CMK keys are only used for encrypting data up to 4K and this works fine for some services in AWS like SNS, Elasticache however for larger data sets normally you give KMS your CMK and ask it to generate a data encryption key.
* Data encryption key returns encrypted and unencrypted data key. You use the unencrypted data key to encrypt the data and then discard that key. To decrypt the data you send KMS the encrypted data key abnd ask it to look after decryption. 

# kms_commands
* aws kms create-key --description "sample" --region us-east-1
* aws kms create-alias --target-key-id eqeqeqweq  --alias-name "alias/sample" --region us-east-1
* aws kms generate-data-key --key-id alias/sample --key-spec AUES_256 --region us-east-1 (returns plaintext and ciphertext version of data key bsae64 encoded)
* need to based64 decode keys before use ( cat plaintext | base64 --decode)
* encrypt using plaintext key - (echo "test data" | openssl enc -e -aes256 -k fileb://whereyousavedplaintextstring
* ask kms to decrypt data ( envelope encryption )
    * decode the encrypted version of data key (cat encrypted_datakey | base64 --decode)
    * aws kms decrypt --ciphertext-blob filen://./decodedkey --region us-east-1
    * the response from kms then needs to be decoded also => (echo "returned decoded string" | base64 --decode > secret.txt)
    * then use open ssl and the decoded plaintext decryption key to view data ( cat secret.txt | openssl enc -d -aes256 -k fileb://decoded_datakey)
* whenever you want to encrypt/decrypt data you always need to contact KMS as the data key is not stored anywhere
* you can use customer managed cmks ( the underlying backing keys are rotated every 3 years)
* aws managed cmks ( underlying keys rotated every year)
* you can reencrypt data with different cmks without every showing plaintext
* you can allow encrypt permission but not decrypt
* wide range of permissions via key policy
* role separation - you can grant roles permission to admin services but not to decrypt 
* can be used with vpc endpoints
* supports full logging
* supports FIPS 140-2 fully compliant with level 2
* can only interact with KMS using AWS APIs
* doesnt support industry standard libraries
* Use when you need role separation between admin and encryption

# cloud_HSM_hardware-security-module
* validated hardware
* Is a dedicated HSM which runs within your VPC. Accessibly only to you in a single tenant architecture
* AWS manages hardware but has no access to the cryptographic component
* Interaction with CloudHSM is via industry standard APIs, no normal AWS APIs
* Keys can be transferred between CLOUDHSM and other hardware solutions on premise for example. 
* Keys shared between cluster members
* No HA unless multiple HSMs are provisioned
* Apllications can be outside the VPC ( direct connect, peered ,vpn)
* Used when you need PKCS#11, Java Cryptograpgy Extensions (JCE), mSFT cRYPTOng(CNG) - kms doesnt support any of these
* Private only modules injected into your VPC with networking entities
* HSM cluster is 1 or more HSMs
* Cloud HSM not used when you need a service which fully interacts with AWS services
* Supports FIPS 140-3 
* KMS can be accessed from anywhere. Cloud HSM you cant have physical access to the HSM. If physical access a requirment then use HSM on prem
* keys transferred between HSM modules in a cluster
* Hardware acclerated 

# AWS_acm 
* lets you manage x509, ssl/tls certificates
* asymmetric certificates
* private key stored on resources ( servers, LBs) other half Public
* ACM integrates with other AWS services and generates certs that are valid for 13 months
* native integration with elb, coudfront, elastic beanstalk, api gateway
* no cost association with certs - only resources the are used with
* certs auto renewed 
* integrates with route53 to perform dns checks as part of certificate issuing process
* Is regional - certs can be applied to certificates in that region
* KMS is used
* valid 13 months
* will auto renew if assigned to resources
* cant use acm on ec2

# AWS_Directory-service
* simple AD 
    * Pros - low cost based on samba4. Basic directory services for aws and on-aws servcies. Integrates with AWS for SSO. (service integration for ec2).
    * Cons - not a true Microsofy AD directory, so wont work with more complex enterprise. Doesnt support TRUST relationship with MS AD (samba limitatio)
* Msft active directory  
    * Pros - Miscroft directory service provided as a service running windows server. HA, in multiple AZ.
    * Cons - not for large scale or web federation. More expensive then simpleAD. Use only when MS AD is required
* AD Connector 
    * Pros -Directory proxy provides a bridge between AWS services and an existing on prem AD. Allows EC2 and Workspaces
    * Cons - In isolation provides no authentication/authorisation or directory services. Requires existing implementation
* Amazon cognito 
    * Pros - Designed to support ID federation, user pool mgmt, sign-on and more for web and mobile apps
    * Cons - not suited to traditional directory service. Doesnt integrate with services in the same way
* Amazon Cloud directory
    * Pros - Graph based store of info, managed object info, relationships and schema mgmt
    * Cons -Not suited to workloads which manage users/groups or identities

# AWS_WAF
* 3 levels conditions, rules (can be combination of conditions), web acl ( allow , deny actions based on rules)
* lets you monitor incoming request to cloudfront , apigateway and elb
* WEB APPLICATION FIREWALL - protect services at edge of AWS network
* isolated set of rules
* can monitor and take actions on specific traffic arriving at a supported service
* allow webACLs to be attached to supported services    
    * webAcl consists of rules which either block or allow what matches them
    * rules consist of conditions which are elemental WAF objects which match actual traffic
    * regular or rate based rules
    * regular - only contain conditions
    * rate-based - which add a frequency requirement to conditions
* webacl processed in order and processing stops when a rule is triggered in the ACL
* WAF includes AWS Shield whihc provides DDOS
* can be associated with AWS service globally or regionally depending on the AWS service
* you can associate WEB acl with as many cloudfront distributions as you like
* you can only associate one web acl per distribution


# AWS_Shield
* provides shield outside WAF
* DDOS PROTECTION
* sits in front of all network ingress
* at the edge before traffic reaches services
* AWS WAF Advanced - 3k a month . Has a myriad of extra features.
    * Layer 3/4 attach notification and attack forensic report
    * incident mgmt during attacks
    * post attack analysis
    * cost protection - reimburse related route 53, cloudfront, and ELB DDOS
    * network flow monitoring (also on standard waf)
    * automated application layer 7 traffic monitoring (also on standard waf)
    * protects from DDOS (also on standard waf)
    * access to additional ddos mitigation capacity
    * lets you protect elastic IPs ( letting you extend network ACLs out to the edge)

# AWS_Guard-Duty
* continuously watching event sources (vpc flow logs, r53 dns query logs, cloudtrail events) , ingests other feeds such as known attacks, malicious IPS and domains and utilizes machine learning techniques to identify anything expected and potentially authorised in aws account such as unexpected infrastructure deployments in a previous unused region ir unusual api calls. 
* if multiple accounts then guard duty aligned to a master account
* makes its findings visble via GuardDuty console. It can generate cloudwatch events allowing notification or automation remediation
* AWS account can be member of only 1 guard duty account
* if your account is submitting to a master guard duty account (another aws account) you loose some of the configuration options available
* threat intelligence
* requires service role permissions
* you can have a single trusted IP ( per account connected to master account) list which can be exempt from analysis by Guard Duty
* you can create a threat list ( shared among the entire group of accounts)
* 6 lists per account
* findings are not realtime

# EC2
* every ec2 image created from an AMI 
* Amazon machine image
* root volume and OS installed in every image
* quick start ami, your ami, market ami, aws marketplace ami
* instance store (ebs root volume) or ephemeral store 
* not by default HA
* occupies a single AZ (single hosted) inside a single region inside a single vpc
* allocated network interface
* uses instance profiles to associate instance with IMA role
* adding security group to an ec2 instance is actually adding SG to the primary network interface
* can have multiple network interfaces but by default has a single eth0 interface

# AMIs
* object containing all the info needed to launch an instance
    * the owner
    * launch permissions
    * the architecture (64bit x86 etc) and OS
    * a block device mapping all volumes required
        * root volume - tree structure that comes as part of os as well as install instructions
        * block devices - 
* creating an image of ebs backed ec2 will create snapshot of each of the backed storage blocks used by the instance. The resulting AMI creates snapshots of the block storage and pointers to these. AMI doesnt contain any storage related to the storage instead it just holds pointers to various snapshots
* you can copy AMI to different regions ( copies AMI and snapshots referenced) and create new instances from it. You can also add/remove additional storage should you require
*  ami doesnt store type of family of the original instance or configuration details
* by default no permissions stored on AMI
* owner has implicit permissions on the instance
* you can make AMI public or private or add to other accounts ( no in between)
* if you copy ami between regions you will get caught by the storage costs in each region
* ami can be sold 
* with AMI you can bring your own license or pay license fee
* you can provision instances with no EBS storage ( limits the family of ec2 types and familys that can be selected)
* choose instance store filter on AMO catalog page
* create AMI from instance store backed EC2 involves bundling. A bundle is created and stored on s3 containing ALL the root volume data. Your not leveraging snapshots instead you are copying actually files. Once the bundle is created on S3 you can created the AMI.
* AMI's are configuration files and not big entities

# EC2_and_virtualization
* before virtualization we used bare metal ( 1 operating system on one piece of hardware)
* hypervisior sits between OS and phyiscal hardware and enables you run multiple OS on a single piece of hardware
* when OS requests access to physical cpu the hypervisior presents component of CPU but makes it look like the full CPU
* HVM - hardware accelerated virtualization - used in most EC2 instances. More of components, instead of requiring emulating in software were supported by the hardware. Hardware assisted components. The guest OS can talk to the virtual cards presented by the hardware bypassing the hypervisior for that communication increasing performance and reducing CPU
* AWS Nitro - latest virtualization hardware. Near bear metal level of performance

# EC2_families
* General purpose - when you dont have specific requirements. 
    * M type is default. Solid performance. Workhorse. Ma type just specifies to use AMD CPU
    * T type when you are not looking to use 100% CPU. Burstable. If you run below certain limits you gain credits. When you burst you use these credits. Useful when most of the time you will run below baseline but expect occassional burst 
    * A type  - ARM cpu ( up to 10gig network performance)
* Compute optimized - require more enhanced or high performance CPU
    * C5 type - cost effective high performance at low price per compute ratio 
    * C5n type - additonal network capabilities - data lakes etc
* Memory optimized
    * R5 type - high allocation of Memory
    * Up to 768 GB of memory per instance
    * ramp up bandwidth
* Storage optimized
    * H1 type - feature up to 16TG of HDD based local storage, deliver high disk throughput and a balance of compute and memory
    * I3 type - non-volatile memory , ssd backed instance storage optimized for low latency very high random i/o performance, high sequential read throughput and provide high IOPS at low cost. 
* Accelerted computing 
    * P3 type - GPU intensive - machine learning, high performance computing, computational fluid dynamics, computational finance, seismic analysis, speech recognition, autonomous vehicles, drug discovery
    * G3 - graphic intensive use cases. 
    * F1 - customizable hardwarae accerlation with field programmable gate arrays (FPGAs)

# EC2_storage
* ebs and instance store (ephemeral stored on the host)
* instance store - connected to host, suspectible to hardware issue. no resilence. Not all instances types come with this type of storage. I'd as ephemeral0 - ephemeral23. Included in price whether you use them or not
    * utilize individually or RAID toegether
    * you can start and stop instance but you will loose the data
    * restarting does not clear the data 
    * used for temp storage, or any volume where you can recreate the data
    * when you need access to highest I/O performance
    * hdd, ssd, nitro options available for instance storage
    * cant be used for sharing data
    * not persistent
    * cant be easily scaled as its tied to single physical storage device
* ebs 
    * latency associated with using remote storage. 
    * can add as many additional EBS volumes as you like ( up to max supported by instance type)
    * network storage product - runs over the network
    * original configuration ment the network activity could impact you regular data networking throughput transfer to the instance
    * AWS created EBS optimized instancs to create dedicated networking for connecting to EBS volumes - improving speeds and reducing contention with traditional data transfer
    * most instances provide this by default
    * 4 types of ebs storage   
        * 1. General purpose (gp2 SSD)
            * default for most workloads
            * baseline performance of 3 IOPS/Gib ( 100 IOPS -16000 IOPS p/vol)
            * bursts up to 3000 IOPS
            * Max throughput p/vol 250Mib/s
        * 2. pROVISIONED iops ssd (iO1)
            * for mission critical apps requiring sustained IOPS performance
            * large db workloads
            * volume size 4Gib to16Tib
            * Performas at provisioned level and can provision up to 64,000 IOS per volume 
            * Max throughout p/vol of 1000Mib/s
        * 3. Throughput optimized (st1) HDD
            * Low cost storage
            * for frequerntly acessed data, throuput intensive workloads ( streaming big data etc)
            * cannot be a boot volume
            * size 500Gib - 16 Tib
            * per volume max throughput of 500 Mib  & IOPS 500
        * 4. Cold HDD (sc1) HDD
            * lowest cost 
            * infrequently accessed
            * cannot be a bot volumes
            * volume size of 500Gib - 16 Tib
            * Per volume max throughput of 250Mib & 250 IOPS

# IOPS
* IOPS - INPUT OUTPUT PER SECOND
* AWS measures IOPS in 256KB chunks
* operations greater than 256kb are separated into 256kb chunks
* Given I/O sze of 1MB, 1750 IOPS => throughoput is 1,750 Mib/s
* max throughput per instance 1750MIB/s
* max IOPS is 80000


# Choosing_EBS
* persistence - able to tolerate reboots and instance failure
* durability - requires snapshots or resilence
* elasticity - changing performance demands over time
* provisioned performance - certain ebs volumes can provide guaranteed performance levels
* exist in specific AZ - if AZ fails so do all EBS volumes
* ebs cannot be shared between instances
* use snapshots to extend duarability across regions and AZ's3
* you can scale IOPS independent of storage size
* use s3 to store important content 
* use cloudfront and s3 for staic content
* you can dettach and attach to new instance
* if durability is a requirment across AZs choose something else ( s3 is a far better option)

# EBS_snapshots
* a backup of EBS volume which is stored on s3
* the first snapshot you take can consume the same storage as the ebs volume you take the data from
* future snapshots only store difference between time of original and new
* When snapshot blocks are deleted, blocks required to restore the other snapshots aare retained
* snapshots are point in time and known as crash consistent. 
* used when creating AMI
* you can resize ebs volume and instance type
* not as fast throughput as instance store volumes ( which can be RAID together to get greater IOPS but data is gone if a failure occurs)
* none can support shared
* use s3 for media content or highly durable content

# EC2_instance_Profiles_and_roles
* utilize IAM roles as best practice
* using STS api call to assume identity not possible on EC2
* Create IAM role for ec2 service where ec2 service type is principal
* when you create ec2 instance through console by assigning an IAM role, AWS automatically creates an instance profile using same name as the IAM role
* the instance profile is linked to the role and the instance profile is linked to the instance
* the cli tools are then able to access the temporary credentails as part of the ec2 metadata
* http://169.254.169.254/latest/meta-data/iam/security-credentials/<ROLENAME>
* sdk designed to fallback to any metdata defined rolenames if no explicit credentials provided
* the instance profile is constantly refreshing credentials in the background ( ec2 constantly engaging with STS to refresh)
* you can change an instance role and settings after instance created ( attach new but you can only ever have 1 role per ec2 instance)
* if creating the ec2 instance from cloudformation or sdk then you need to create the instance profile explicitly
* any applications running on the instance can consult the metadata and use role as required - if you need to restrict it inside the ec2 instance then you have to utilize an internal firewall or some other internal security mechanism
* roles offer great way to add temporary credentials at scale becasue ec2 instances can be configured to use IAM role when launching (scaling)
* the calls are http to metadata endpoint - use revoke session api call if concerned about someones access to these services


# placement_groups
* expensive
* required when require maximum performance from ec2
* you cant really modify placement groups. If you try add extra isntances no gurantee there will be space. Instead you would need to remove all the instances, delete the placement group and create new placement group 
* better outcome if you provision the same type of instance and do it in advance
* types:
    * 1. cluster (performance) - original type which groups logically in a single AZ ( cant span multiple AZ) - allow high speed and low latency between instances in group. Uses least amount of hardware possible. Allocated in advance. Can span VPC peer but you do loose some of the beneifts. Performance between network interfaces in instances is governed by the smaller instance. Potential for Gig flow between instances in placement group. If connecting to instances outside placement group then you are limited to 5Gib limit
    * 2. partitiion (large scale infrastructure , HA, lets you have some control where they are placed) - designed to spread large infrastructure sets across infrastructure in isolated fault-domains/ Uased when you need HA, but need physical location control  ( hdfs, casandra ) - can only be created using api or cli - 7 partitions per AZ
    * 3. Spread placement (insist on physical separation) - designed for small number of critical components where you need to ensure spearation. A spread placement group can be single AZ or multi AZ. You can add to spread placement groups later as you are not concerned with instances running on the same hardware , instead you want them on different isolated hardware. Max 7 instances per AZ per group
* instance can be part of only 1 placement group at a time

# EC2_CloudWatch
* Cloudwatch by default gathers control plane data on ec2 instances, metadata ( info outside ec2)
* no visibility to peer inside ec2 instance
* in order to surface memory consumption of ec2 instance it is possible install Cloudwatch agent in the ec2 instance and report data. 
* two ways to do this. Create new role with SSM ( system manager access) and with cloudwatch agent. Add the role to the ec2 instance which creates instance profile allowing ec2 interact with SSM and CloudWatch.
    * 1. manually - download latest cloud watch agent via terminal of ec2 instance ( all config option stored in /opt/aws/amazon-cloudwatch-agent/etc/)
        * create amazon-cloudwatch-agent.json in this location
        * use this new configuration file as part of the command to start the cloudwatch agent - /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-cli -a fetch-config -m ec2 file:/amazon-cloudwatch-agent.json
    * 2. Use System manager
        * Choose to Instal by using : Run Command -> AWSConfigureAWSPackage. Select action and a target instance ( 1 or hundreds)
        * Next configure agent using SYSTEM manager : Use parameter store to create json configuration. Then go to Sys Manager and Run Command -> AmazonCloudWatch-ManagerAgent. Set action to configure, use SSM for configuration source. Paste the parameter name in the optional config location. Choose the instance to run. Make sure the ec2 has role access to SSM for both GetParamter and GetParameters. Be careful of the subtle difference 

# RAID_and_EBS_volumes_OR_instance_backed_volumes
* RAID O configuration ( striping) - for performance benefits, no duplication, combining volumes, may cause throughput issues depending on instance limits ( its one piece of the puzzle, there may be others steps to take)
* RAID 1 configuration  ( mirroring ) - duplicates, redundancy
* RAID 0 config
    * log into ec2
    * download package to manage RAID (yum install mdadm)
    * from console configure 2 EBS 10Gib volumes ( should be same in size and performance, we dont want mismatch volumes (IOPS and size))
    * attach to EC2
    * from ec2 terminal session configure for RAID0 ( use sudo , password when changing user is 123456)
        * mdadm --create --verbose /dev/md0 --level=0 --name=cd-raid --raid-devices=2 /dev/xvdf /dev/xvdg
    * write a filesytem to the RIAD device across all 20Gib
        * mkfs.xfs -L cd /dev/md0
    * run lsblk to view the 2 RAID devices called md0
    * mount the devices
        * mount /dev/md0 /mnt  (/dev/md0 is the sum of the two RAID volumes)
        * run df -h to view filesystems

# Restore_files_from_EBS_volume
* requies ebs snapshot to restore ( stored in s3 bucket )
* we can create new ebs volume using s3 snapshot
* it may be necessary freeze the I/O first so you dont loose any I/O during snapshot creation - possibly for databases
* create recovery volume from same AZ as original volume ( mount /dev/xvdg /restore - commands mounts xvdg to restore directory)

# containers_ECS
* container is a small isolated environment designed to run an application in ( together with any libraries or dependencies) specific version etc
* code that will always work - -true portability ( you ship entire environment )
* Virtualization - you can run hypervisor ontop of infrastructure and then multiple VMs on top of that hypevisor to provide hardware level isolation applications ( uses hardware to create/separate the VMs)
* Containerization - Os running ontop of bare metal , containers run ontop of OS isolated with all the libraries and application. ( dropping some of the security, not using hardware to separate. All containers run on same base OS therefore each container does not require its own OS and as a result has fewer memory requirements ) - you can achieve greater density in containers. Also alot faster to start. A container like a single linux process. OS supports separating of these processes
* containers can have mapping to the host or external AWS services ( map internal ports to external ports to allow us run hundreds of images on same host ( 100s of apache servers for example))


# ECS_architecture
* you can launch linux or windows instances
* a number of options for networking mode within cluster [awsvpc]
    * awsvpc -maps specific network interface to the container ( only supported type by fargate type)
    * bridge - allows all contaienrs within ec2 instance to communicate ( network option so not fast). You can operate that ENI like any other ENI so it is very flexible. However if you use this for the EC2 type then aws will attach an ENI to every small container running in your cluster , and some ec2s have limit on number of ENIs that can be attached so if the number of containers exceeeds number of ENI's that can be attached then it wont work. 
    * host networking type - maps containers directly onto host networking ( therefore if you use port 80 inside the container that will automatically be replicated on the host , very fast networking, but limits number of containers running same type)
    * if using windows type then none of the above network mode supported. The only supported type is NAT
* base entity - cluster -> collection of compute resources to host your containers as well as definitions to those containers
* tasks - 1 or more containers that fulfil a specific goal. Task defintiion is a config file , a directive to ECS on what it should do, what containers its creates , how they interact etc
* launch method can be ec2 or fargate
    * ec2 mode - utilized ec2 instances whcih are specifically designed to operate container services. 
        * each instance has an ecs agent which communicates back with the ecs service. Responsible for scheduling, failure detection and any management functions available in ECS
        * containers also running on these instances. Task cause containers to get instantiated on this container instances. Task can cause 1 or more containers. ( analogous to pod defintion)
        * when launching on ec2 instance types you are responsible for management of ec2 instances
        * you can choose the type of provisioning mdoe to use ( on-demand or spot)
        * you can choose the instance type ( the type you choose does impact the capabilities you can use in ECS. For example can influence the number of containers you can have per instance)
        * you can select existing vpc or new one, along with cidr block , the inbound rules, and the container instance role
        * easy to add additional ec2 container hosts, container host can be member of only one cluster. This allows scaling up and down
        * if you utilize the awsvpc networking type for task then yoru ec2 instances will not be utilizing the default network interfaces for the ec2 but instead will use the ENIs created by ECS and which are attached to the instance host
    * fargate - you dont need self managed compute resources. You can direct ECS to launch your tasks in a way you dont have to manage. Each task is launched in an isolated manner adding security to your clusters. The admin costs more than if you were to manage the cluster yourself
        * you define task definitions and allow ECS run , you dont manage
        * creates ENI when creating cluster. Ties the ENI to the elastic load balancer. The ENI has associated security groups (standard security groups when awsvpc networking mode selected) which can be modified to provide security. It opens port 80 by default allow application load balancer take requests and direct toward task. If not using awsvpc then you need to look at the security groups assoicated with the container host (instance). You always have the option to use NACL, to use ACL traffic needs to cross the subnet boundary (in or out)
    * Container defintion - the part of the task definition which configured the capabilities of the container the task operates in ( image, memory, port mappings, storage, gpu attachments etc)
    * Task defintion - defines the task, contains container defintions. Configures how the container interacts with ECS, the network mode, execution role, launch type. It cna contain multiple definitions 
    * service - allows you to run a specific number of task instances within an ecs cluster. Services allow load balancing across tasks using an ELB and allow configuration of scaling and availability
    * cluster - groupings of tasks and services inside ECS. They can be managed by ECS or AS managed by Fargate
* vertical scaling an EC2 instance requires you first stop the instance and then change the instance type to the larger instance family

# ECS_permissions
* how to give permissions to ec2 container hosts or any other instances running on those container hosts
* in fargate look at tasks
* for ec2 type look at tasks and containers
    * ecsrole AmazonEC2ContainerServcieForEC2Role is the thing that gives container host permission to talk to ECS ( its attached by default)
    * also lets it log to cloudwatch logs with this same role (an instance role)
    * utilized aws logs driver ( done with role listed above)
    * also can have roles attached to particular tasks
    * you want to limit the roles to only container instances that access particular service ( you can apply task role)
    * instance role applies to all containers, task role is just that specific task. 
* for fargate you can only use task roles, you dont have access to hosts
    * task execution role is different to task role . The execution roles is used by ECS on your behalf to interact with the cluster
* by default even if you use task roles EC2 instance containers are not prevented from accessing role permissions. There is a way to block ec2 container host role access
* require public IP to pull down and push docker images

# Lambda
* you can select if you want a VPC or non-vc lambda function 
* choosing Vpc can impact speed 
* you can specify concurrency where required
* in s3 -> events section specify new event and define Lambda as the "Send To" target
* by default whenever lambda executes it will put its log output into cloudwatch logs (using a log group matching the name of the lambda fuction)
* has cold and warm startups for sanboxes ( isolated operating environments which do contain temp dir for file storage be its transient).You need to assume every invocation will use cold sandbox therefore you need to utilize other AWS services ( dynamodb, s3, sqs)
* anything defined handler method is limited to teh execution however anything created outside the handler will be available to future invocations of Lamdbda (for example data connection)
* can take environment variables which are enccrypted by KMS
* can recievce data from event source
* operates outside VPC by default
* If running inside VPC they are potentially subject to same network restrictions in that vpc
* Using lambda inside VPC slows down startup as ENI is created withing VPC and attached to sandbox
* AWS working on remote NAT so multiple lambda can utilize same ENI
* time limit 15 minutes
* Lambda architecture updated so now each function has its own dedicated micro vm which is isolated from other AWS accounts. The hypervisor , host OS and hardwareis shared across accounts
* Lambda requires an execution role

# Lambda_layers
* architecture flexibility
* lambda code can by added via 
    * s3, 
    * zip file or 
    * inline
* Previously you needed to include relevant software dependencies, libraries for function as part of deployment package. 
* layers improves this by adding additional runtime support. You can make the layer, share it and use it again. It is immutable and can be versioned ( to prevent break)
* Lambda function can use up to 5 layers
* Layers can be used to store commonly used libraries and other software dependencies allowingthem to be removed from deloyment packages
* Layers are extracted into the /opt folder of the execution environment
* Total size of all layers cannot exceed 250MB but this allows you make deployment package smaller and then reference these layers
* Layers can be shared across your AWS accounts or made public

# apigateway
* managed APIs in a completely serverless way
* REST apis, websocket apis
* REST - request / response
* websocket - bidirectional - interactivity between client server
* API gateway is a regional service. Therefore you are publishing an API into a specific region. 
* Can utilize edge locations so your APIs are closer to customers
* can deploy inside VPC
* API can have different versions or stages
* Url to access endpoint is always in format https://<api-id>.execute-api.<region>.amazonaws.com/<stage>
* the way your API interacts with other services is known as integration. There are a number of integration types
    * mock/test integration - If you open the integration response section in the console. Expand the mapping templatyes and add mock response body. Can be used to return instructions or some static response.
    * Lambda integration - api gateway forwards event/ request details to lambda handler function which then in turn returns some data depending on nature of lambda ( event driven serverless architecture)
    * service integrations - read or write data to dynamodb, s3
* API gateway allows you to cache responses 
* you can put WAF in front of API gateway ( webACL) and filter against known attacks, IPs etc
* full featured logging and tracing (cloudwatch , x-ray (serveless monitoring))
* APIs can be deployed into privat VPCs, then are region specific, they can also be pushed to edge locations. 
* can directly read/write from supported integrations
* you can host static website on s3 and then use API gateway to execute operations which are not suitable for running client side by leveraging API gateway endpoints you create
* fully resilent, fully scalable
* API runing in a region or edge location can still leverage integrations with private VPCs if it needs to run some sensitive operations in a more secure manner. 

# AZ_zones
* could be 1 data center, multiple data centers placed in close proximity however we are not sure so we need to assume it is a single fault domain

# AWS_service_resilence
* IAM
    * global product ( not regional, replicated worldwide). Still works if some region goes down. If a region goes down you can still interact
* ec2/ebs
    * EC2s run on hosts which are AZ specific. Failure in an AZ causes failure of those hosts and all instances on the host
    * EBS volumes stored on specific AZ. Replication happens within the AZ but failure can result in data loss ( snapshots are replicated across AZ and optionally copied cross region). (In order for EC2 to use EBS it must be in same AZ so outage in an AZ will cause data loss potentially). EBS does have some level of replication within the AZ so if one storage device does go down its possible the data will not be lost but we need to treat it as if it will. For completness use snapshots which can replicate the data across all AZs in the same region and utilizes S3 as the backend. (Once you have that snapshot you can potentially copy across region adding global level resilence) * snapshots resilent across all AZs in a region
* S3
    * regional service, Replication in most cases across 3 or more AZs ( with one exception if you use onezone as a storage class then replication only occurs across 1 AZ)
    * from a namespace perspective S3 shows up as Global service on AWS console however the actual bucket is specific to a region
* R53  
    * operates its name service from the AWS edge locations which are positioned globally. It is resilent even to issues that effect AWS regions ( many more edge locations around the world in major cities making it more resilent than region)
* ELB/alb 
    * regional services and enabled for specific AZs or multiple AZs in a region ( when enabled an ELB node is provisioned for an AZ and network interface are placed at a specific subnet). The recommendation is to place the ELB in all the AZs where you have instances of your application running that means if one AZ fails you still have services in other AZs which also can be accessed via the ELB which has created network interfaces in those AZ too.
* VPC
    * regional services - you can create subnets in a VPC which are tied to particular subnets. (Subnet can not span AZs and therefore services inside the subnet cannot span the AZs). Therefore architecturally the recommendation is to place a subnet in each AZ in the region where the VPC is located, services are placed inside the subnets (such as ec2, multiple instances across all AZ) giving you a multi-AZ architecture utilizing mutliple instances using a load balancer to balance load across these AZs and handling any outages in a particular AZ. 
* NAT GW
    * not truly resilent by design - They are placed inside an AZ and provide hardware resilence in that AZ (you do have multiple NAT gateways inside your AZ, placed in a subnet allowing it tolerate hardware failure). But if the AZ fails the NAT GW fails so best practice is to place NAT GW in every AZ where you have a service. The configure your private instances to have a default route to 0.0.0.0/0 which uses that NAT for any internet based traffic 
* ASG
    * resilent at a regional level. They manage the provisioning of services within a region on any AZ. ASG have a unit of compute capable of reacting to AZ failure. The ASG operate in a VPC across subnets in that Vpc
* VPN
    * Configured using Virtual private gateway. Whenever you create a virtual private gateway and attach it to a VPC you are creating a number of public vpn endpoints operating from different AZs

# EC2_and_multiAZ
* EC2 can only run in a single AZ however you can use an auto-scaling group which can create instances of the same services in other AZs by choosing 1.1.1. min max desired

# stateless_architectures
* elasticity is the characteristic allowing instances to scale up and down based on system load - available in stateless stateless_architectures

# scaling_applications_billing_models
* on-demand
    * default billing model
    * pay for only what you consume ( perf hour/GB transferred, GB stored/month)
    * good for ad-hoc usage where future patterns are unclear
    * provides small usage discounts for high volume but is generally most expensive option
    * standard startup priority
    * when you have peaked traffic throughout the year
    * most useful , when you need reliability
* reserved
    * significant cost reductions and optionally capacity reservations ( if committed to 12-36 month term)  
    * 3 payments options - all upfront ( cheapest ), partial upfront, no upfront
    * reservations can be used for Ec2, RDS, DynamoDB performance etc
    * Useful when usage is known and steady
    * high start-up priority
    * you need to absolutely guarantee capacity in an AZ
    * for base consistent load 24-7
    * you can specify reserved instances based on AZ or region. If you choose AZ and if there are capacity constraints then you take priority
* spot
    * Sporadic workloads
    * you can tolerate interruptions and want lowest price
    * significantly cheaper than on-demand but is 100% dependent on spare capacity - therfore prices can be higher if capacity is constrained
    * resources can be terminated with little notice
    * workloads need to be tolerant to interruptions
    * lowest startup priority
    * analytic workloads
    * different instance types have different spot prices
* on-demand capacity reservations
* scheduled reserved instances -  reserve for discrete chunks of time rather than long term contract ( useful for online store with spikes )
* spot fleet - a collection of spot instances, allows you define spot instance pools, which are a set of EC2 instances with same instance type (same OS,AZ, networking platform) . Reduce the likelihood you have an outage while reducing your costs

# AMI_baking
* create an EC2 instance, do teh configuration, once created "create image" ot provision one instance, or many instances
* quick
* using an ASG you can provision instances at scale without any configuration period
* downside is the more you bake in the less configuration you can do later. To adjust you need to create new AMI and update.
* Its not a flexible way of launching instances however it is quick

# Bootstrapping_userdata
* use bash script in ec2 provisioning to instruct ec2 what setup your instance requires
* all the configuration is performed live as the image is created giving us complete flexibility
* adds additional processing time ( every instance provisioned goes through all the setup unlike the AMI option)
* gain flexibility but loose speed

# ASGs 
* provide HA
* elasticity ( scaling in and out)
* allows sustem adjust number of ec2 instances as load increases/decreases
* ASG contains the AS group and then the launch template used to start up the EC2 instances
    * Launch Template - configuration of the ec2 instances that will be launched by ASG. It is the "what" is deployed of the ASG.
        * Contains AMI, instance family , billing mode, IAM role, name, userdata, monitoring, kernel, ram disk, address type (public, ), storage, security group, keypair. 
        * It is an immutable package , cannot be changed. Create new entity of you want changes. Then update the launch configuration in the ASG. 
    * The ASG is the where and when 
* ASG can only have one Launch Template associated with it but it can be changed. 
* Launch configuration is the legacy way of creating ASG. 
* Launch Template is the recommended way to create ASG ( similiar but improves the process)
* Launch Template - you configure the same basic information ( in addition you can add shutdown behavior, termination protection, tenacy, placement group etc)
* Launch Template can be versioned or you can create new template based on an existing as the source ( making admin easier)
* ASG controls everything beyond the instance configuration
    * you specify the launch configuration or the launch template
    * you can pick teh version of the launch template
    * you can choose other purchase options and instances
    * select group size ( desired, max, min)
    * select when and where instances are created ( which vpc and subnets ( can be all subnets in vpc))
    * in advanced section you can associate with Load balancer
    * asg has built in health checks  - you can set grace period telling ASG to give instances time to startup before its applies any scaling rules
    * scaling policies
    * ASG can notify you when they change number instances. 

# Implemeneting-ASG
* during scaling events attempts to keep balance of instances across subnets whereever possible
* can add scaling policies to ASG
    * scaling policy with steps - adjust actions taken based on how much certain metrics are ( if cpu or disk space increase by a huge amount then respond to a greater degree that if it only slightly increases slightly). You can add additional steps and make the scaling policy as complex as required
    * target tracking policy - set target values for given entity (cpu, memory). Based on the target increase or decreases
    * simple scaling policy - similiar to policy to scaling with steps only without the steps. When a specific policy is breached then take some action.
* you can define warm-up time before any action is taken
* you can disable scaling at anytime
* you cna modify the target value when scaling event occurs
* ASG can execute scheduled actions - you can scale in or out based on a timeframe. 
* You can configure cool-down times for ASG group - if your group executes a scaling activity then you may specify not to take further action until cool down period of for example 10 mins passes before taking further action. This gives the new or terminated instances time to take effect. 
* Termination policy - allows ASG to specify the order in which instances are shut down during scaling activity ( for example multi instances in a specific AZ, oldest launch config, closest to billing hour, random)
* monitoring privided as part of ASG - you can select "Enable group metrics collection" to collect as group ( shows averages , summaries etc) - enabled per AUTO scaling group
* you can pause activities in the ASG such as healthcheck, launch, terminate, replace unhealthy, azrebalance
* you can protect an instance so it cant be terminated, you can also set an instance to standby for example if you need to do some maintenance. 
* You can also detach instances from an ASG. 
* healthcheck type can be EC2 or ELB. EC2 type simply uses AWS EC2 instance status of host and does not check anything explicitly linked to the application. If you choose ELB you can specify port and path of your application. Which may be more suitable for a true healthcheck


# Multi_AZ
* planning for AZ failures ( the goal is to achieve best resilence with least buffer over provisioned)
    * buy reserved capacity in AZs to prepare for occassions when you need to scale up (costly)
    * over provision - if 3 AZs required for normal operation then add a 4th AZ , if one goes down application will still operate at 100% (costly)
    * spread instances across more AZs -  increasing the spread means the impact is lessened when an outage does occur. So if 2 instances spread across 5 AZs then you only need provision 1 extra AZ with two instances to handle event of an AZ outage. If you have 5 instances in 2 AZs and you want to plan for an AZ failure then you need to provision another AZ with 5 instances which is a more costly strategy then if you had utilized more AZs with less instances per AZ.
* Minimum AZs should be 3 

# ELB
* accept connections from clients and distribute among multiple backend servers ( in some equal or level way across available instances)
* highly available and scalable load balancer as a service
* integrate with Auto scaling group 
* designed to distribute equally between ELB nodes ( 1 per AZ). Some exceptions to this. If you have two ELB nodes in different AZs and in one AZ there are 4 instances and the other has a single instance. Then ELB will route 50% of the traffic to each node however one node will split teh traffic between 4 nodes while the other can only forward to one instance. This creates an imbalance.
* cross-zone load balancing - when this option is enabled it allows the ELB to load balance taffic to instances located across multiple availability zones. Solving the scenario mentiond previously. This allows for highly available and fault tolerant architecture. The ELB nodes can route to any instance registered with the ELB regardless of the AZ. Enabled by defualt in newer ELBS. 
* configured to operate in a number of AZs. The ELB places a node in each AZ it is configured to use. The node performs the load balancing
* instances can be registered to load balancer in a number of ways
    * manually
    * via target group ( app or network LB)
    * via ASG
* When you deploy an ELB it is given its own record set in Route 53 (A Record) that allows for direct access from its external side
* provides abstractions between layers
* built in healthchecks
* ELB can be externally or internally facing
    * public facing -  each ELB node gets a public IP address
    * private facing - get VPC internal IP address not accessible to the outside world
* By default ELB gets publicily routable IP addresses
* 3 flavors of ELB
    
# ELB_arch
* contains listeners which define what protocol and port the ELB nodes are listening on. Two pieces , the load balancer protocol and port it listens on for requests coming in and the instance protocol and port which is the target of the requests the load balancer is forwarding
* uses security groups to control access to EC2 instances
* healthcheck: ELB is actively communicating with backend services ( you can specify port, protocol, path to ping). You can also define how often, how long to wait for response, how many healthechks to fail and pass to change state. 
* you can enable cross zone load balancing
* you can enable connection draining
* configure the ASG to use the ELB healthcheck type as this will check the application path and scale in and out based appropriately. This also registers the current instances of the ASG with the ELB. 
* round robin by default
* stateless by default
* can enable ELB stickiness if you have session requirements and need the request to return to same server ( enable load balancer generated cookie stickiness - first time client hits a service a cookie is generated and that cookie is used to ensure request returns to the same server for the lifetime of the session or until that instance fails). You can set an expiration period. You can also use application generated cookie stickiness where you give the ELB the name of the cookie and let the application provide it with the request. 
* Can use SSL offload /termination whereby requests to AWS Route 53 and ELB are over HTTPS but then requests to backend services once inside AWS are over standard HTTP - useful when you dont want each individual service/server in AWS to have to handle encryption/decryption - therefore the load balancer handles the compute heavy enc/dec translations. This saves us having to add SSL certificate on every other backend service in AWS that handles the request. 
* to support SSL offload an SSL certificate needs to be added to the ALB. Use ACM to generate certificate for the URL you are using to connect to website. 
* [compare tool](https://aws.amazon.com/elasticloadbalancing/features/#compare)
* if there is only one healthy target in a target group then the load balancer will route to just the healthy instance. If there are no healthy instances in the target group then the load balancer will route requests to all registered targets. 


# Classic_LB
* classic Clb - deprecated and not recommended by AWS. Only used with EC2 classic.Don't understand layer 7 communication. No granular routing rules. E.g no path routing. You can only configure listeners, one per protocol per port and forwarding to only one group. You do not assign public IPs to classic load balancers. You dont communicate with the CLB nodes, you always communicate with the route 53 A-record. Never use direct IP address to talk to a CLB
 
# Application_LB
* understand and operate up to layer 7
* can see paths appended to Urls. Fully understands connections between client and backend services - which can be used to influence how the ALB works
* recommended ELB type to use within VPCs
* perform better and cheaper than classic LB
* can take routing decisions based on application level specifics (layer 7 protocol)
* same basic architecture as classic lB
* capacble of using IP v4 or dualtsack ( 4 and 6)
* http or https listeners
* created in a VPC and you choose AZs to deploy nodes too ( which allocates IP automatically)
* uses security group wrapped around the ALB, and the nodes in each subnet the ALB is servicing
* Lets you define target groups - you dont associate instances of the application directly with ALB like classic LB. 
    * The target type can be instance, IP, lambda function
* because it understand layer 7 protocol you can use http codes to check that the response from a target is in a range you deem to denote success.  
* When associating with ASG you can edit the ASG and update the Target Groups field and select the target group created and associated with the ALB. When the ASG registers with Target Group it updates the Targets assoicated with that Target Group
* for a given listener all of the routing behavior is controlled by actions. For every listener we have a default action. Therefore we can specify for any request to HTTPS 443 we want to forward to a specific Target Group
* ALB can also react to the hostname - therefore we can have multiple sites for example routing to the same load balancer
    * can be achieved using new listener - with type host header ( so it reacts to a particular URL and not path) and specify domain and then forward to a target group.
* you can add additional SSL certificates to ALB if you are handling requests from multiple domains
* rules can be host-based or path-based
* ALBs support ECS, EKS, HTTPS, HTTP.2, Websockets, Access Logs, Sticky Sessions, AWS WAF
* ALBs allow routing to multiple applications on same EC2 instance - such as containers
* HTTP /2 allows up to 128 incoming requests on a single connection and the load balancer will split them up and distrubute them equally as htp1.1 requests over all targets. 
* if using http2 you can improve efficieny of ALB
* can also redirect requests and not just forward. Can authenticate or return fixed response. 
* can monitor health of each service, not directly connected to each instance
* not a single unbroken connection between client and backend resources. Offload happens at ELB where SSL termination may occur. Then a new connection on specified port routes internally to AWS target service. 
* content based routing


# Network_LB
* used if you have specific requirements above what ALB can give 
* Lets you define target Groups
* operate at layer 4 - TCP
* extreme performance, much less operational overhead at layer 4
* support static IP addresses to front load balancer for ultra low latency 
* service requests on a particular IP and route to instances registered with a target group
* uninterrupted end to end encryption ( the NLB only looks at TCP layer)
* does not require and certificate configuration on the NLB, no encryption/decryption and you can have the backend resources handle the encryption and decryption
* doesnt understand or interact with http or https
* does not support udp
* can route traffic to addresses outside the vpc
* when routing to targets inside the VPC it does hold onto the client source IP address but not when forwarding outside
* used for high volume usage
* useful when we have huge spikes in traffic

# elb_via_cli
* aws elbv2
    * create-load-balancer
    * create-target_group
    * register-targets
    * create-listener
    * describe-target-health

# proxy_protocol_ELB_and_NGINX
* nginx can act as a reverse proxy and forward requests to some particular server
* nginx can also proxy websocket connections to a backend server - tcp, layer 4
* ELB can also route straight at tcp level ( layer 4) without inspecting protocol (layer 7)
* on layer 7, with http, the load balancer injects x-forwarded-for header with the original client ip address however routing on layer 4 does not support this header inclusion
* tcp layer 4 supports websockets , layer 7 does not
* HA-proxy provide solution (proxy protocol) when you are working on layer 4 but still want client IP address
* Proxy protocol lets us configure additional header.
* to enable procy protocol on ELB need to enable policy on the ELB ( policy which controls whether to include the IP addres and port of the originating request for TCP messages)
* 1. Create policy with ProxyProtocolPolicyType
* 2. Set attribute ProxyProtocol = true [ --policy-attributes AttributeName=ProxyProtocol.AttributeValue=true]
* 3. Assign policy to ELB - specify ELB name, instance port, policy name ( we cna assign more than one policy to a particular port. Important to list all during update otherwise existing are deleted.)
* 4. Configure Nginx to accept the proxy protocol and get this information into our log files
```bash
server { 
    listen 80 proxy_protocol;
    listen [::]:80 proxy_protocol;
    set_real_ip_from [cidr block range of VPC]; 
    real_ip_header proxy_protocol;
    ...
```
* 5. Update log format
```bash
    replace log_format main '$remote_addr with '$proxy_protocol_addr
```

# cloudfront
* operates around base configuration entity known as distribution
* dsitributions are either web ( static and dynamic content, media files (over http), live streaming) or RTMP ( speed up distribution of streaming media files , this protocol allows end user to begin playing a media file before the file has finished downloading from a cloudfront edge location. )
* Web distributions
    * origin (where the content lives)
    * behavior setting (can have multiple bahavior but there is a default behavior) which are matched to a path. Default is invoked if not match found
    * origin fetch - process of fetching content from the edge locations from the origins
    * viewer side - between the edge locations and the client (viewer protocol settings define technical configuration of the communication between the client and the edge location )
    * origin protocol - defines the communication protocol between the origins and the edge locations 
* advanced setup configuration only required when using a custom origin. When choosing S3, ELB, EC2 there is no advanced config required
* you can enable "Field Level Encryption COnfig" which instructs the edge locations to encrypt your data and transmit all the way to origin using custom encryption to make sure noone can decrypt [secure end to end]
* you can deploy distributions to different categories of edge locations
* aim is to push content as close to clients as possible
* you can link a Cf distribution with a web ACL (used to filter out known bad actors and known exploits)
* changing WAF wEB acl requires redeployment of distribution across all edge locations (can take up to 45 minutes)
* by default distribution is given its own CNAME but you can assign your own ( and provide your own SSL certificate, or reference one in ACM)
* SNI - allows a server to present multiple certificates on the same IP address and TCP port number and hence allows multiple secure HTTPS websites to be served by the same IP address without requiing all those sites to use the same certificate. 
* update the DNS record set ( which is an ALIAS record type allowing mapping to another name and can coexit with other records on that name) to point to the cloudfront distribution DNS name
* you can invalidate distributions associated with particular path or entire distribution - can take up to 45 mins as change needs to be run on every edge location your distribution is deployed too. 
* you can restrict viewer access per behavior and not per distribution. 
* first request does origin fetch, subsequent requests do a cache hit and dont need to do an origin fetch
* can also use regional cache ( as well as edge location cache). When a request hits edge location, if content does not exist it will next check the regional cache before trying to do an origin fetch
* Lambda can be used at the edge to provide compute at any of the 4 communication channels involved in distribution (viewer request/response, and origin request/response)
* can restict content - no geo restriction by default

# Cloudfront_distributions
* when we create a distribution AWS packages up all the changes and deployes to each of the edge nodes we have choosen - any changes need to be propagated again across all nodes
* select edge locations via the "Price Class" which determines which edge nodes you have deployed across
* distribution contains set of origins and origin groups ( used to reroute during a failover event). 
* you cna define a number of origins and then configure how they are used inside a behavior setting
* only need to worry about ssl if your are using a custom endpoint to access your distribution (you can use your own certificate or one from ACM - ACM cert will automatically renew and no charge for using it)
* using this custom SSL lets you in effect add SSL capability to an S3 bucket
* cloudfront serves content over SSL only to clients that support SNI
* if your client dont support SNI then you need to make sure you have dedicated IPs for every CloudFront edge location ( which has an extra charge)
* cloudfront support TLSv1 TLSv1_2016 TLSv1.1_2016(recommended) TLSv1.2_2018
* Use HTTP/2 where possible , it is faster. CloudFront will then use http1.1 to forward to the origin
* you always specify the defualt root object - for example index.html
* in distribution behavior you can specify which requests you want to route to the origin. For example requests matching pattern images/*.jpg can be routed to an images folder in S3 bucket 
* you can define custom error pages
* cloudfront is a distrubuted system - you cna preform actions (enable, delete, disable)
* distributions are just configuration objects
* you can use custom headers which will be sent between cloudfront and the origins (useful to track information between CF and origins). If the headers are the same as ones supplied by the client then these override the client values
* if using AWS origin like S3 and the viewer request is https then the origin request will also be https. This changes for custom origins where you have more flexibility to choose [HTTP ONLY, HTTPS ONLY, MATCH Viewer]

# Cloudfront_custom_origins
* EC2 , or on prem servers
* as long as it has public internet access it can be used with CloudFront
* you have more flexibility to modify the origin protocol and SSL policy [HTTP ONLY, HTTPS ONLY, MATCH Viewer]
* TLSv1 TLSv1.1 TLSv1.2 SSLv3
* you can select ports between cloudfront and custom origin server
* used only for legacy environments
* custom origins REQUIRE publiC IP addresses. and if using SSL must have certificate signed by trusted party and not self signed or internal authority
* custom ports and protocols cant be modified when using S3 or other AWS origins

# cloudfront_security
* cf can filter malformed packets at the edge before they even reach your origin servers (allowing only valid http or https through) - providing a simple level of ddos protection
* you can also applly AWS Waf web ACL to the distribution adding another layer of proetction ( layer 7 firewall system )
* if using SSL between client and edge locations then the certificate needs to be one issued by trusted certificate authority ( must be trusted by the client)
* if using S3 then you can leverage the default certificate generated by S3 and no further config required.
* If using an ELB you can use a certificate generated from ACM
* Use OAI ( origin access identity) to prevent requests bypassing your cloudfront edge and going straight to the origin s3 endpoint -
    * 1. create the OAI
    * 2. request cloudfront to update the bucket policy ( see example below )
    * 3. remove original policy on s3 bucket which previously allowed access from any used
```bash
    {
        "sid" : "2",
        "Effect" : "Allow",
        "Principal" : {
            "AWS" : "arn:aws:s3:::somes3bucjket.com/CloudFront Origin Access Identity <cf dirtirbutionid>"
        },
        "Action": "s3:GetObject",
        "Resource" : "arn:aws:s3:::somes3bucket.com/*"
    }
``` 

# Cloudfront_signed_url&cookies
* similiar to S3 signed URLS (both linked to an identity)
* provides signed url access to private cloudfront distribution
* Make Cloudfront distribution behavior private ( for a single bahavior you cannot have signed URLs and public access at the same time)
    * not enabled at a distribution level - instead inside behavior settings scroll to option "Restrict Viewer Access (Use Signed URLs or Signed Cookies)
* Its is possible to set the default behavior to public and then create a behavior for a specific path make it private. 
* if usnig RTMP you cant use cookies
* If granting permissions to all sets of data and file types use cookies otherwise use signed URLs ( single objects )
* signed URLs allow an entity ( an application ) to cretae a URL which includes the necessary information to provide the holder of that URL, read/write access to an object even if they have no permissions on that object - cookies extend this allowing accesss to an object type or folder and dont need a specifically formatted URL. 
    * signed urls/cookies are linked to an existing identity ( role/user) and they have the permissions of that entity
    * they can have their own validity period ( default 60 minutes)
    * they expire either at the end of the period or until the entity on which they are based expires. If you use a role this is when the roles temp credentials expire
    * anyone can create a signed URL even if tehy dont have permissions on the object
    * with cloudfront you defined the accounts which can sign, the key pair TrustedSigners is needed for Cloudfront. 
    * SIgned Cookies dont work with RTMP

# cloudfront_restrictions
* geo-restrictions - enable whitelist ( allow ) or blacklist ( deny ) - Edge locations obtains location of requestor IP address and then edge asks cloudformation if this is allowed. 
* can only do geo restriction and only based on location and Ip address
* for any additional checks on sessions, browsers, devices, location , language, country etc you need to use 3rd party restriction and that requires isolated compute to generate signed URL which needs a private behavior to be configured

# field_level_encryption
* you can use a public key with cloudfront (via field level encryption option)  - which encrypts all data entering the edge locations and passes to origins. This means if the request is writing data to dynamodb then you will be storing encrypted data
* you can then use private key with applications that need to decrypt the data. This means data is encrypted closer to the client providing more comprehensive security. 
* To use feld encryption you configure your CF distribution to specify the set of fields in POST requests that you want to be encrypted and the public key to use to encrypt them. You can encrypt up to 10 fields in a request. You must specify individual fields to encrypt as you cannot simply encrypt all data in the request. 
* the data is then forwarded through your origin sub-system , the sensitive data is still encrypted reducing the risk of a data breach or accidental data loss of sensitive data. 
* your origin must support chunked encoding to allow field level encryption.
* uses asymmetric encryption (aka public ket encryption)

# Optimizing_caching
* aiming for best ratio between cache hits and misses
* you can edit caching behavior inside distribution behavior settings under Minimum , maximum and default TTL (in seconds)
* default cache is 86400 
* by default cloudfront does not forward query strings ( meaning the cache does not differentiate between similiar requests with different params)
    * forward all, cache based on all ( cache takes query strings into consideration and caches accordingly creating new objects for each variation)
    * forward all, cache based on whitelist - maybe only some of the query strings in a request alter the content so you only want the cache to differentiate this small subset. in this case you can create a whitelist of query strings allowing cache to be influenced E.g language might be important but id might not influence data
    * none - default option. Query string does not impact caching

# Lambda@Edge
* configured in cloudfront distribution on per behavior basis
* lambda function must already exist - 4 event types can trigger execution 
    * 1. Viewer Request
    * 2. Viewer response
    * 3. Origin Request
    * 4. Origin response
* once you associate lambda function with a behavior it is pushed out to each of those edge locations. You can do whatever you want with those lambda functions, like performing advanced authentication
* when the lambda is invoked it is provided with a structure of data and this data dependis on the type of event that triggers the lambda (see types earlier)
* using lambda at the edge you can provide realtime manipulation stream between client and origin source and reverse flow of that communication
* when to use scenarios
    * to inspect cookies from client to origin to potentially offer different versions of the response for A/B testing
    * display different layout or images to the website depending on the device 
    * deliver different page format depending on location of client
    * inspect cookies and provide advanced authentication. 
    * differentiate between activities and serve different resolution images
* functions need to be deloyed in us-east (north virgina) region - 
* cloudfront doesnt execute lambda functions for viewer response events if the origin returns http status code 400 or higher
* you cant nodify the http status code from a viewer response event for a successful request 
* You can however execute lambda functions for origin response errors, including http status code 4xx and 5xx

# Cloudfront_reporting_monitoring
* you can see across all distributions or a given distribution  (by different granularity, countries etc) -
    * total request
    * % of viewer resquests by result type
    * bytes transferred to viewers
    * cache hits/misses
    * http status codes
    * num field level encryption requests
    * referral report
    * able to create cloudwatch alerms based on reporting data ( and implement some real time event driven architecture)
* we can also turn on distributed access logging for a distributio or across all distributions  ( configure s3 bucket, add logging prefix if desire, and choose to log cookies or not) - need to make sure proper ACL exists on the bucket to allow aws logs delivery entity to write logs to the s3 bucket
* can integrate with cloudwatch and cloudtrail, cloud config, billing and usage/ 

# Route_53
* provides public and private (available inside VPCs) DNS services
* can register and host domains
* dns registered domains store nameserver records - if these are updated route53 communicates these changes to the global DNS platform
* hosted zone - by default a hosted zone will have 4 nameservers attached to it 
* nameserver on the domain must match nameserver associated with hosted zone in AWS (done automatically if you register domain in AWS)
* hosted zones are public (available across the internet) or private ( can be attached to a VPC)
* hosted zones contain record sets - detailing how the hosted zone interacts with the outside world 
* record types - A (ipv4) , CNAME (hostname to hostname mapping), ALIAS, AAAA (ipv6), MX (route email) etc
* Alias - instead of an IP address an alias record set contains a pointer to an AWS specific resource such as ELB, CF distribution, ElasticBeanstalk env, S3 bucket
* you create hosted zones for DNS names
* record sets can specifcy how long other dns services cache record set details using TTL 
* route 53 you can configure healthchecks - you can use IP addresses or domain names. It can utilize the HTTP, HTTPS, TCP protocols
* cant use CNAME at the apex of a domain
* 3 is the number of consecutive healthchecks that an endpoint must pass before route 53 marks as unhealthy ( checks every 30 seconds)
* using a record and alias you can create a failover solution which will redirect requests to your website to a failover page should your site become unresponsive. 
    * 1. create a record pointing at your ec2 instance. Set routing policy as failover and select primary record type
    * 2. create alias record pointing at S3 bucket, choose routing type as failover and set as secondary record type
* healthchecks will not detect failures behind load balancers in individual AZs
* domains registered with private hosted zone are available to the dns servers in that VPC
* See inbound and outbound endpoints

# route53_advanced_routing
* default simple routing policy -  only allows the association of one record set type with your dns. You can however associate with multiple IP addresses through the value field. Route53 will the return all values in a random order. 
* failover routing policy - to work effectively the primary needs to be associated with a healthcheck 
* geo-location routing - you can specify a location for a given record set to route to for example an S3 in a particular region, or set a default region if user request from a location not catered for
* latency routing - aws monitors latency and route 53 will map the request to the target with the lowest latency
* weighted routing type - 
* multivalue routing - similiar to simple but lets you set healthchecks on each ip you add and then will only attempt to forward to heathy endpoints
* you can version control different traffic policies are roll out or roll back as required. 

# S3_architecture
* object storage system 
* flat structure
* object isolated entity with metadata
* can store almost unlimited number of objects (finite number of buckets however bucket can have unlimited number of objects inside)
* objects stored in storage classes
* access restrictions using bucket policies and permissions
* lifecycle policies
* static files
* origin for Cloudfront
* used for backup ( AWS storage gateway)
* s3 is a global service however you specify region during creation and then can view buckets together
* you only have 100 buckets inside every AWS account but you can increase this using service ticket
* bucket naming
    * must not contain upper case leters, 
    * no underscores
    * shoudl not end with a dash
    * must be between 3 and 63 characters long
    * must start with lowercases letter or number
    * avoid periods
    * must be globally unique
* s3 bucket is a container that contains objects
* can store versions/ can encrypt
* s3 objects - no folders, it has flat structure. It is key/value store. When you create folders it gives the impression of file structure however the folder simple gives you another way create your key. The key name can be simple of contain prefixes (complex) and a delimiter which allows S3 to preset its flat structure as a hierarchy (E.g. where / is delimiter and prefix is cdugga/images/ )
* object stores - versionid, value ( ranging from 0 to 5TB) , metadata 9user defined or system defined), subresources ( ACL or torrent information associated with an object), ACL
* you can do inventory reporting , on a daily weekly basis for the entire bucekt or a shared prefix ( use athena to do analysis)

# s3_static_website
* you need to enable CORS (cross origin resource sharing) to enable s3 hosted bucket to be able communicate with other domains

# s3_access_control
* you grant permissions to a bucket in a number of ways
    * identity policies attached to IAN identities in your account
    * bucket policy 
    * ACLs - applied at object level
* supports ipv4 and ipv6
* s3 can generate events - and send to SNS Topic, SQS Queue, Lambda Function ( event driven)
* default billing method - storage class standard
    * any data you upload to S3 , the data transfer is freeze
    * when you transfer data out there is a cost ( differes whether you are using public internet or vp, vpn, direct connect.)
    * gigabyte per month charge for data objects inside s3 bucket
    * you get chareged for the data capacity used for your bucket
    * price for puts or gets you use to interacts with objects
* you can make certain objects within an s3 bucket public
* there are account defaults and bucket defaults for new objects/buckets
* S3 block public access setting (at bucket or object level)

# s3_storage_tiers
* storage classes can be adjusted manually or using lifecycle policies
* storage class determines the cost, durability, and first byte latency for retrieval
* all storage clases offer 99.9999999999 (eleven nines) object durability
    * intelligent-tiering
        * designed for unknown, or unpredictable access patterns.
        * moves objects between two tiers , one optimized for frequent access the other for infrequent access
        * objects not access in 30 days are moved to infrequent tier ( cheaper)
        * objects accessed from the infrequent tier are moved to the frequent access tier for no cost.
        * includes a per object monthly automation and monitoring fee - but does not include retrieval costs
    * standard - all-purpose storage
        * default option
        * 99.99% object availability (99.9% availability SLA)
        * millisecond first byte latency
        * most expensive
        * transfer costs. puts and gets also have small charges
        * three pricing categoires [gigabyte per month, transfer costs for retrieval, api operations like gets and puts]
    * infrequent access ( S3-IA)
        * for important objects, access is infrequent
        * 99.9% object availability (99% availability SLA) 
        * 3+ AZs
        * millisecond first byte latency
        * less expensive then general storage
        * 30day minimum storage charge per object, 128kb minimum storage charge
        * object retrieval free
    * one zone infrequent access (S3 One Zone-IA)
        * NON-CRITICAL REPRODUCIBLE objects
        * 99.5% availability (99% availability SLA)
        * 1 AZ replication
        * 30 day minimum storage charge per object , 128kb minimum storage charge
        * object retrieval free
        * less expensive then standard and S3-IA 
        * if the AZ fails you could loose the data
    * Glacier
        * for long-term archival storage not for hot backups
        * can take several minutes or hours for objects stored in Glacier to be retrieved ( the faster you need it retrieved the more it will cost)
        * cheapest S3 storage class
        * 3+ AZ
        * 90 day minimum charge per object, 40kb minimum storage charge
        * free retrieval
    * Glacier Deep Archive
        * long term archival storage - ideal alternative to tape backup. 
        * cheaper than normal glacier but slower to retrieved ( no option for faster retrieval)
        * 3+ AZ
        * several hours for objects retrieval
        * 180 day minimum charge per object , 40kb minimum storage charge
        * object retrieval fee
* glacier is a much different storage architecture than S3. Although you can still see Glacier objects listed in S3 they are actually moved to an entirely different system.

# s3_lifecycle_rules
* define what happens objects after certain number of days
* add rules for both current and versioned forms of objects
* expire/delete data at a certain junture
* move between storage tiers
* you can only move objects in certain directions between tiers - you can't move from glacier to standard for example
* rules added at bucket level
* objects smaller than 128kb cannot be transitioned into intelligent tiering
* objects must be in original storage class atleast 30 days before tranistioning to either IA class 
* if objects are encrypted they remain encrypted during transition into glacier or temporary restoration into S3

# s3_lifecycle_rules
* uploading objects to s3 will overwrite what currently exists in bucket if object name and prefix are identical 
* versioning adds a unique id onto each object names
* S3 updates the previous version to non-current and uses the new version as current
* versioning cannot be disabled once enabled but it can be suspended.
* versioning is required for cross region replication
* deleting an object with versioning enabled adds a delete marker, when you try access that version with deleted marker it returns a 404 error , you can go back and remove the delete marker and make the object available once more if required. 
* bucket owners can directly delete version using the id, permanently deleting the object
* fetching an object without an id will always return the latest version
* versions can occupy different storage tiers
* provides a good audit trail and prevents objects being deleted or overwritten accidentally
* comes with additional charges

# s3_object_locking
* allows you place restrictions on what you can do with objects in an s3 bucket
* two methods - retention periods and legal holds and requires versioning is Enabled
* both prevent udpates or deletions for a period of time for a given object.  (in the case of legal holds there is no expiration date)
* legal holds are independent of retention periods and re used for legal or auditing style situations
* available for new buckets at time of creation once versioning enabled
* cross region replication not available when object lick is enabled.

# s3_access_control
* all buckets private by default allowing access only to resource or object owner
* bucket trusts owning account by default - therefore can create iam policies to give other IAM users access to the bucket
* IAM roles can be created with permissions on the bucket and shared cross Account using AssumeRole 
* when an IAM user accesses bucket it is known as an Authenticated Identity - similiarly when an IAM role is assumed 
* situations exist when you need to grant access to bucket to non authenticated users - using resource policies for un-authenticated users
* following policies deals with non authenticated users
```bash
{
    "Sid" :"AddPerm",
    "Effect" : "Allow",
    "Principal" : "*",
    "Action" : "s3:GetObject",
    "Resource" : "arn:aws:s3:::somedomainname.com/*"

}
```
* bucket policies can have multiple statement blocks, but only 1 policy per bucket
* bucket policies can also restrict access based on for example known bad IP address or range
* bucket policies can also restrict for certain times of day
* bucket policies can also restrict based on tags of objects or object name
* bucket policies are AWS recommeneded way of controlling access to buckets
* bucket ACO are legacy for of access control
* ACL - dont have ability use conditions or restrict access. Just simply allow you to give list, write and read permissions to different actors (aws accounts, public, s3 log delivery group)
* ACL however can be applied to particular objects - so you can define permissions at object level using the ACL
* Pre-signed URLS - give permanent or temporary access to s3 object or objects without granting permanent permissions on wider bucket
    * provides restricted access to private data
    * you can create pre-signed url to an object even if it doesnt exist. 
    * you can also generate pre-siged url to object you dont have permissions to
    * access denied if user who created pre-signed URL losses permissions when pre-signed url is called
    * Running the following command generates a presigned URL with permissions (based on IAM user creating the URL) baked into the URL - contains an expiry date
```bash
aws s3 presign s3://somedomain.com/someasset.png
```

# s3_cross_region_replication
* replicate objects in source bucket to another bucket in s3 bucket 
* only applies to bucket objects creted, updated , deleted after cross region replication (CRR) enabled
* you can replicate entire bucket or prefix or tags (or a combination) in a bucket
* you can replicate objects which are encrypted using KMS
* you cant replicate objects encrypted using cmks
* by default you cant replicate encrypted objects, you need to specify KMS
* Lifecycle events are not encrypted
* if bucket owner has no permissions objects are not replicated
* an IAM role provides S3 with the permissions required to add to the destination
* you can replicate to buckets in different AWS accounts
* CRR maintains storage class and ownership. Both can be changed however

# s3_encryption
* default no encryption
* client side or server side encryption
* client-side encryption - the client handles encrypting of object and managing keys and then passes the encrypted data to s3
* server side encryption - client offloads encryption to s3 , s3 manages keys and encryption and decryption of data
* objects are necrypted and not buckets
* you can alter type of encryption 
* with server side encryption the data sent to and received from s3 is un-encrypted however it is sent over https encrypted tunnel
    * Server side encryption with S3-Managed Keys (SSE-S3): default type of encryption ( envelop encryption)
        * S3 encrypts an object with a unique key stored with each object. That key is then encrypted with a master key (which is regularly rotated) and stored with object. S3 manages everything. 
    * SSE-C (using CMKs)  - server side encryption with customer provided keys 
        * User uploads unencrypted object to s3 along with encryption key (using x-amz-server-side-encryption-customer-key)
        * customer manages the key
        * s3 encrypts data with key and stores, then discards the key
        * to decrypt the object teh user must supply key, allowing S3 to decrypt and pass back the key in plain text form
        * cant use with Cross region replication
        * used with on-prem HSM
    * Server side encryption with AWS KMS Managed Keys (SSE-KMS)
        * s3 uses a CMK which is managed by KMS
        * s3 requests a data encryption key (DEK) for each object it wants to encrypt
        * KMS returns plaintext and encryted version of the key 
        * s3 uses plaintext version to encryt the data and then stores the encrypted key with the object
        * when decrypting S3 sends the encrypted key back as plaintext 
        * s3 uses plaintext version to decrypt 
        * this option allows you split up administration of objects to s3 and management of encryption keys to KMS ( you can have specific permissions, add auditing and reuse across other services, etc)
* you can add a bucket policy to deny upload to a bucket where a specific type of encryption is not used.
```bash
 "statement" : [
     {
         "Sid": "DenyIncorrectEncryptedObjects",
         "Effect": "Deny",
         "Principal": "*",
         "Action": "s3:PutObject",
         "Resource": "arn:aws:s3:::YourBucket/*",
         "Condition": {
             "StringNotEquals" : {
                 "s3:x-amz-server-side-encryption": "AWS256"
             }
         }
     },
     {
         "Sid": "DenyUnEncryptedObjects",
         "Effect": "Deny",
         "Principal": "*",
         "Action": "s3:PutObject",
         "Resource": "arn:aws:s3:::YourBucket/*",
         "Condition": {
             "Null" : {
                 "s3:x-amz-server-side-encryption": "true"
             }
         }
     }
 ]
 
```

# s3_performance
* standard ( only on objects up to 5gb, single data stream, slow, prone to network disruption ) 
* multipart upload ( objects up to 5TB, multithreaded uploads to maximize bandwidth (splits and upload in parallel), reduces the impact of network issues by reducing the zie of restart domains )
    * initiate upload and obtain upload id
    * split and upload in parallel
    * complete or abort ( aws charges for each chunk of the upload as it arrives in S3 however if the upload is aborted there is no cost)  
    * max 10000 parts per upload
    * sizes 5MB to 5gb
* TRANSFER ACCELERATION - enabled per bucket basis
    * given additional endpoints to access S3 from - you are given a local clodufront edge location URL rather than interacting directly with s3 regional endpoint ( uses nearest edge location.) . Once enabled any s3 uploads or downloads are transmitted across AWS global backbone network ( low latency and efficient backbone transit )
* partition and object naming   
    * when you cretae s3 bucket it has a single partition capable of 3500Puts per second and 5500 gets per second (not both but a combination )
    * s3 can split the objects in a particular bucket into multipel partitions each with that same partition performance of 3500puts and 5500gets eefectively increasing bucket performance
    * s3 uses prefixes to create partitions
    * you cna now use logica or sequential naming patterns in s3 object naming without performance impact
* if you dont need to achieve more than 3500puts or 5500 reads per second then dont worry about object naming in the bucket

# glacier
* one of the cheapest ways to store data in AWS as long as you dont need it in a hurry
* account can have 1000 vaults per region
* limited UI console
* vaults consist of archives (data) - need a unique per region per account (names can be smae across region). 
* archive has unique id and description - the description can only be added to glacier when created and not afterwards
* interact with glacier as asynchronous operation - it takes time 
* you get notifictaions via SNS
* inventory taken of every vault very 24hours
* when you retrieve an inventory you either get the contents of the last inventory or an ad-hoc inventory which retrieves any additions or deletions
* vault inventory contains a list of every archive in that vault. ( lists archive id, creation date, and size, no metadata or user defined fields, no names)
* archives cant be edited, only deleted , modifications are treated as new archives
* retrieval speeds  - expedited (1-5 minutesfor anything below 250MB), standard (3-5 hours), bulk ( 5-12 hours most economical)
    * by default when you request an archive you get the entire archive data. But you can request specific portions. If you have put metadata in that archive you can ask for specific components. 
* No real value interacting with Glacier directly, use S3 instead to view objects etc. 

# file_commands
* fdisk -l - list devices attached to an ec2 instance
* under root dir you can do a lsblk (list block devices) to see any block devices attached to filsystem 
* you can create filesytem on the raw block storage device  
    * mkfs -t xfs /dev/xvdf ( create file system on the volume )
    * mount block storage device into a folder  - mount /dev/xvdf /test
    * running df -k lets you see the /dev/xvdf is mounted on the /test folder

# EFS
* shared filesystem - highly scalable and highly performant
* shared network file system which can be mounted on EC2 instances or on-prem ( uses NFS - network file system)
* nfs can be mounted across multiple linux os  (supports version 4 and 4.1)
* can be mounted into filesystems
* s3 is not a good option when you need a shared filesystem inside an ec instance
* base entity of EFS is file system - with mount points
    * instances connect to a file system using mount targets you create. 
    * create mount target in each AZ to alow EC2 instances in arcoss your VPC access the file system
    * you can select security group for each mount target
    * you can use default for the VPC or a custom one
* lives inside a VPC
* supports encryption (at rest)
    * you can select a KMS key from your account to protect your file system or you can provide the ARN of a key from a different account,  ( you can use default KMS master key or your own CMK)
    * encryption of data at rest can only be enabled during file system creation
        * encryption of metadata - handled directly by EFS
        * encryption of data - you manage the configuration for this
    * encryption of data in transit is configured when mounting your file system
        * configured when mounting on client
* use AWS EFS Utils to interact between ec2 and EFS (download with sudo yum install -y amazon-efs-utils)
* once you have EFS utils installed you only need the ID of the filesystem and not the IP 
* mounting EFS filesystem
    * create a directory at the root level which will be used to mount EFS - sudo mkdir efs
    * mount - sudo mount -t efc <filesystem-id> /efs  (BY DEFAULT NOT USING ENCRYPTION IN TRANSIT)
    * ** ec2 instances and mount targets need to have congruent security groups - default security group allows communication by any resource in the VPC
    * to use encryption in transit specify options tls 
    ```bash
        sudo mount -t efs -o tls efs-987897897:/ /efs
    ```
* you dont have to set the size for EFS filesystem and instead AWS charges for whatever you use
* permissions to create the filesystem and enable creation 
    * using aws permissions policies - give individual identities access using IAM
    * key policy when using encryption - adding resource and AIM user
* permissions on the file system
    * unix style permissions (POSIX)
    * root user can interact with any file
* can work with AWS DayaSync and AWS Backup

# EFS_performance
* PERFORMANCE mode can be general purpose or max I/O which is optimized for applications where ten, hundreds, thousands of EC2 instances are accessing the file system ( can only be configured during creation) - max i/o has additional latency overhead
* THROUGHPUT mode ( can be adjusted after filesystem created)
    * bursting - for 99% of cases
    * provisioned - when you have more throughput requirements
* efs data is replicated across AZs so a single AZ failure will not cause data loss
* write operations durably stored across AZs
* use cases - big data, media processing, content management, home dir, shared log storage
* not used when only required on single instance - not used for object storage or where you need to integrate with cloudfront, not used for temp storage
* can scale up to 10+GB per second, can scale out to 100s, 1000s of connections
* need to make sure the direct connect or VPN is not a bottleneck when communicating between efs and on-prem

# fsx_architecture
* you can provision managed third party file systems
* like efs
* by default not highly available
* sprovides filesystems based on SMb or luster
* needs an implementation of Microsoft AD
* you configure trust between Microsoft AD and FSx allowing users to access file system
* private only VPC
* same security as EFS
* can backup to S3
* can utilize Microsofy DFS replication
* filesystems can be a minimum of 300GB and max 64TB
* you can join file systems togetger to achieve 300Petabytes storage
* use FSX file services when you have windows platform
* use FSX for luster when you have large scale high throuhput environment
* every file system encrypted by default ( KMS or you can chooose)
* You need to configure a trust between Microsoft AD and the FSx filesystem

# storage_gateway
* file gateway, volume gateway, tape gateway
* run on virtualization software on-premise
* ideal as a migration solution when moving data onto AWS
* allows onprem extend storage capacity by utilizing AWS
    * TAPE Gateway - managing tape drives. Use iScsi . Virtual tapes stored in s3 and then moved to virtual shelf in glacier 
    * file gateway - smb and nfs - want to extend file server. File server orchestrates between your on-prem and s3 and storage of objects. 1:1 mapping between file stored in file gateway and object in S3. Uses file path as object name in s3. You can see the files in s3 and interact with them. You dont pay for any data going into AWS
    * volume gateway - you can map block storage volumes onto on-prem servers. Cache volume architectures, primary storage on s3 and then cached between s3 and on-prem ( when you have limited on-prem storage). The second is stored volume architecture where you maintain the primary version of your data in the volume gateway and utilize s3 for snapshots
* you can deploy storage gateway into AWS on an EC2 instance and access data natively after migrating in
* also has disaster recovery functionality

# databases_self_managed
* ec2 self managed databases - creating an ec2 , attached an ebs volume and installing a database instance
    * when you want to install a type of database not supported by AWS
    * limitation with this approach 
        * running on a single ec2 instance ( on a single host in a single AZ) - NO RESILENCE ( you could create snapshots and you could provision in another AZ and setup replication)
    * you do have alot more control and granularity. You have root level OS access
    * quicker to shutdown ec2 and provision bigger instance type then increase RDS

# database_RDMS_NOSQL
* rdms - relation db used when the data to be managed has formal and fixed relationships. data is stored as rows and entire rows must be parsed even if individual attrinutes are all thats needed. Reading 1 attribute from 10000 records requires 10000 rows to be read from disk
* tables have schema, every row needs correct attributes and data types
* rdms conforms to ACID ( Atomicity, Consistency, Isolation, Durability) - which reduces ability to gain high performance
* rdms not ideal for dynamic data
* NO/SQL systems use BASE system - meaning basic availability (database works most of the time and sacrifices some of thr perceived availibity for performance and scalability). It has a soft state, writes dont have to be consistent, replicas dont have to be consistent all the time. Known as eventually consistent. You may get data before a write is replicated. 

# database_NOSQL
* different types
    * key value : dynamodb, redis - zero structure in the tables, every row can be entirely different structurally. 
        * useful for caching, anything where rapid retrieval required. 
        * the value in dynamodb is all the non key attributes in the table 
    * document db : Mongo - collections of key value pairs with structure. You operate on documents and there is no relationship between the documents and can be radically different.
    * Column Based : Redshift - for analytics and reporting. Data stored in columns so you can easily look at just one piece of information in a table for 100s of thousands of records without having to look at an entire row for each item in the table. Not suitable for transaction
    * Graph : Neo4j, Amazon Neptune - Suited when relationships between data is key. Like social media. Relationships constantly changing. 

# Elasticache
* in-memory data store
* cheaper then databases as it stores data in-memory and does not need to execute any compute to get the data
* used with db to increase performance
* low latency
* offloads read volume from database
* the application needs to be aware of it 
* can be used to store session state
    * redis
        * supports more complex data types (lists, sets , hashes , array etc). 
        * Key value store
        * Not multithreaded
        * snapshots and backup and restore ( allowing it recover more effectively from failover events)
        * supports replication between nodes - horizontal scaling
        * supports transactions ( group of operations )
        * geo spatial support
        * ability to failover between AZs - automatic failover
    * memcached
        * does not support complex data types. 
        * Has better support for scaling vertically as its supports multi-threaded operation
        * key value store
        * does not support backup and restore
        * does not support replication - does allow multiple instances
        * no transactions
        * no geo
        * choose when running large single instance node


# Amazon_RDS
* you get a database endpoint once provisioned
* requires subnet group
* RDS - Aurora, MySQL, MariaDB, PostgreSQQ, Oracle, Msft SQL Server
* you can provision production or dev.test. Production will provision an active(master) and backup(salve) pair of instances (multi AZ, synchronous replication) - each with its own EBS volume. Replication happens between db instances. If an issue with master the CNAME is switched over to slave, in mormal sitiations you cant hit the slave directly.
* you can suppply your own license or pay for it. 
* ec2 instance family prefixed with DB are dedicated for RDS
* can choose general purpose or provisioned IOPS for storage type
* need to pick vpc and subnet ( can be projected into public realm but not recommended)
* creates new Secruity group
* two types of encryption - TDE transparent data encryption (Oracle), or EBS volume encryption using KMS
* encrytpion only available at creation time
* automatic backups  - 7 days by default if created through Console, 1 day if created through CLI  ( 0 days ( disables) up to a max 35 days)
    * backups - as well as storing a snapshot they also store transaction logs allowing for point in time recovery
* integrates with cloudwatch - you can use standard or enhanced monitoring. You can change the granularity (default 60 seconds, you can also choose 1, 5, 10, 15, 30 seconds)
* payment modes - by default uses on-demand, you can reserved ( all, partial, no front). You can reserve instance for 1 or 3 years ( same as ec2 instamces)
* backups are stored in S3 and replicated across multiple AZs in that region
* when restoring a database you are not restoring into existing database but instead into an entirely new database => any applications connecting to db will need to be 
updated with new CNAME to that database
* replica can be in another aws region or simply in another AZ in shared VPC as db instance
* latency due to asynchronous replication
* you can create multi-tiered setup of read replicas to massively scale the read capacity
* only master node has write access
* to create replicas you need snapshots enabled ( this creation can happen after master was created)
* AWS handles communication between regions even if no VPC peering in place
* read replica can have different database versions
* You can influence database options which normally require root access using parameter and option (feature level functions) groups. Both have default values ( e.g. auto_increment_increment etc. ) which you can override
* if you delete db instance you have option to preserve the backups however they do have a data retention period
* you can stop,reboot , delete
* cloudwatch , cloudwatch logs
* you can adjust config of db after its created (with the exception of encryption type)
* you can change backup retention, and change windows
* you can create replicas but cant pool together like you can with aurora

# Aurora_architecture
* high performance without the cost
* in rds replication happens at instance level not storage volume
* provides mysql (5.6) or postgreql
* 5x performance of mysql, 3x postresql
* all instances share same underlying storage volume ( cluster storage volume across AZs)
* you can choose serverless config if you like, also provisioned, 
* security group defines how you interact with teh aurora database
* you can use authentication with IAM db authentication
* encryption same as other RDS dsitributions
* backtrack - regress without restoring ( additional cost)
* you can have 15 replacas  - all accessing same cluster storage volume - increasing performance
* read replicas can be addressed directly to cope with read heavy workloads
* you can now have multi master instances which allow all to read and write
* you can promote read replica to be master  - this is a good way if you want read replica in another region to become master (useful for disaster recovery )
* provides two endpoints - 1 for the main cluster endpoint which can read and write and a second which maps to all the read only replicas
* you can create groups of instances or access individual instances directly (using custom endpoints)
* with aurora you can store up to 64Tib of data but are only bllled for what you utilize - therefore no upfront charge and no need to provision during setup
* you can use the cluster storage volume architecture for read replicas in the same region as the primary instance however if you need cross region replication then Aurora uses the same replication architecture as RDS
* BACKTRACK - role back/rewind to a previous point in time without creating a new DB cluster ( DB is unavailable during the backtrack process which typically takes a few minutes) - no need for applications to update endpoint
* backtrack handles by cluster storage volume
* using cluster storage volume its possible create a clone really quickly
* you cna scale write capacity with multi master
* in aurora backups are continuous and incremental and stored in s3 ( constantly) - operates on cluster storage volume and no impact on database
* you can restore to any point in time up to 35 days ( quickly )
* parallel query function option - optimization feature. puts queries together that share same structure (long running queries)
* auto scaling replicas - you can select an instance and add auto scaling policy 
    * you can set min and maximum capacity and target metrics ( requires IAM role )

# aurora_global_database
* extension of cross region read replicas
* consists of two aurora clusters in two different regions connected by replication servers in each region ( connected at the storage level)
* improvement on traditional read replicas and less lag
* primary instance as well as sending writes to cluster storage volume, it also sends to replication nodes of replication server platform. The replication server streams logs between local replication server and remote replication server. In the remote region the replication server handles writes to the cluster storage volume where you have lots of read instances performing reads
* better than RDS replication as it allows you to have multiple read instances all talking to same cluster storage volume . If a failure happens in local region you can promote one of the read nodes in the remote region to be the new primary node and effectively failover into a new region
* high throughput, recover quickly (lss than 1 minute), low lag 

# aurora_serverless
* removes need to manage database servers
* provdies database as a service
* implements data API - more suited to lambda etc
* aurora you only pay for storage you use and not what you provision (unlike classic RDS)
* DONT WORRY ABOUT size of ec2 instance
* we do specify the minimum and maximum aurora capacity units (ACU) - influences cist of running cluster
    * 1 ACU - 1 vcpu and 2GB RAM
* its possible to configure pause for cluster - when no access to cluster has occured for a certain amount of time we can pause all the allocated compute. At this point we are only billed for the storage that is used. After 7 days in this state a snapshot is taken and the db is taken down another state where there are no compute units ready to go and snapshots exists which can be used if required
* operates in a vpc ( you can choose same parameter groups)
* you can specify encryption but cant switch off 
* aurora maintains a warm pool of instances ready to swap into an existing serverless cluster as capacity is needed
* connections are managed by a shared proxy layer which brokers connections and stops interruptions due to scaling events or failures
* connections to the databases can be achieved either by using traditional mysql sdks, cli or via the new aws DATA AOU. 
* aurora serverless clusters dont operate active.active instacnes in multiple AZs . Shared storage and warm instance pools results in quick failover
* auto scaling process is completely transparent
* limitation is that aurora serverless operates in only a single AZ - therefore failover results in a different AZ being used and a new ACU using the cluster volume storage ( so not as fast)
* db snapshots can be us*ed as basis for creating Aurora serverless
* data api is not enabled immediately - no longer need to use ec2 instance to interact with data in Aurora database

# athena
* serverless product that allows you to execute SQL like queries on data stored in s3
* your data in s3 can be stored in structure, semi structred and unstructured data formats
* athena lets you create a schema which is overlayed on the data in s3
* when athena runs its doesnt change the data in s3 but overlays your table definitions on s3 giving you access to the data using the athena schema
* uses schema on read technology - does not alter the data ( can be thought of as perspectives)
* no ETL process required
* serverless - only pay based on data you read
* pricing demands on region - 5dollars per terabyte - (you can partition, column format etc)
* you can interact with:
    * cloudtrail logs
    * cloudwatch logs
    * ELB logs
    * VPC flow logs


# dynamodb
* db as a service - regional service
* region specific unless you configure otherwise
* key value store tables
* every row is an item with no fixed schemas
* primary key is only mandatory field in an item - needs to be unique. Other elements in item are attributes . Max size 400kb . All attributes can be different. 
* Primary key (aka pk, hash key, partition key) can be just a hash key or it cna be multipaart primary key ( with pk and sort key which must be unique combination)
* only mandatory values in dynamodb item are pk and sort key if one exists
* attributes are non mandatory values and consist of attribute name and value
* when you read a single attribute for a dynamodb item you actually consume the entire read capacity for the entire item - not able read anything less than 1 item (crucial for cost)
* you are billed based on two aspects - the total size of all data in your table and secondly based on performance demands of the system
* you can specify read and write capacity
    * RCU - each is 4kb of data
    * WCU - each is 1kb of data
* when you read or write to dynamodb you always consume atleast 1 RCU or WCU depending on what you are doing, ( always rounding up for reads and writes)
* reading data
    * scans - returns everything in the table - you cna use filter to narrow range of returned items. you can scan the entire table using more than just the pk, you can use one of the attribute values however when scanning using some non pk or sort key the scan operation will consume entire capacity of the table
    - more efficient than query when you have multipart pk
    * queries - super efficient, you can specify partition key for an item and return all the data for that partition key value ( you are billed for all items for that pk) - you can narrow down based on sort key (single or range reduces costs if there are more than one matching pk value - key to managing performance)
    - using filter can reduce data returned even more however it doesnt actually change the RCU consumed. The sort key is the only way to reduce RCU 

# dynamodb_contd
* partitions underly each table - piece of storage (10gb of data , 1000 wcu,3000, rcu)
* if data in table grows beyond 10gb a partition is added
* if you request additional capacity on table ( higher than 1000wcu, 3000rcu) partition is added
* partitions cannot be removed. 
* when adding items to table dynamodb it uses hash function and takes that value when deciding to choose a partition to place item in (not based on sort key)
* single item is only placed on a single partition therefore maximum performance for all the items will just be the max for a single partition (as they are not replicated). This makes it more crucial to ensure you are spreading items evenly across partitions
* eventually consistent - you can specify if you want immediate or eventual consisteny
* ensure partition key has as many different values as possible
* when you allocate capacity for your dynamodb table its important to remember that that performance has to be shared across all partitions. So if your partitions size grows horizontally your capacity per partition is shrinkingant 
* index - local secondary indexes (share rcu and wcu with table) can be created at tables creation. global secondary indexes can be created at any time. They let you specify additional sort keys
* global secondary indexes are more powerful as they allow you create indexes with different partition and sort keys from the already defined pk. - has its own allocation of read and write capacity
* if using attributes in an index ensure they are projected otherwise its very expensive
* GSI allow you to create really efficient queries using a different perspective of the data 
* eventually consistency consumes half the read capacity of immediatley consistent read from the table
* can do full backups and restores into s3
* restores all the data and configuration and capacity and when restored will be identical to prior version ( state is identical )
* also restores the indexes - key information etc
* allows point in time recovery - needs to be enabled ( 35 days retention)
* you can use encryption (not on by default) - choose between server side encryptio using AWS CMK or KMS
* allows transactions (ATOMIC commits) - both elements of a transaction linked , you cna specify that transaction succeeds only if all elements succeed.
* metrics, ttl values, errors etc available through cloudwatch ( you can create alarms)
* you can purchase reserved capacity if you know long term requirements

# advanced_dynamodb
* auto-scaling - you cna define a read and write capacity auto scaling rule
    * target utilization
    * minimum provisioned capacity for both rcu and wcu
    * maximum provisioned capacity for both rcu and WCU
    * you can choose to also apply same scaling activity to global secondary indexes for both rcu and wcu
    * requires an IAM role to auto scale - (you can use Dynamodb service linked role or custom role for this)
    * suitable for provisioned
* if you dont want to set an upper limit on capacity then on-demand billing is more suitable - it offloads capacity management to Dynamodb. Ideal when its a profit related activity and you dont care what level it goes to when satisfying demand
* adaptive capacity enabled by default
    * when you provision capacity it is spread across partitions. If one partition is particularly hot then you will quickly run into soft capacity limits. With adapative capacity AWS will look at other partitions and if some of the partitions are not in use it allows the hot partition to borrow some of the rcu and wcu capacity. 
* streams
    * you can create a stream for a table which basically surfaces the flow of activity on that table . The stream can store a number of different views (keys only, new image (entire item), old image (entire item before modified), new and old image (both))
    * useful for implementing triggers/like lambda (e.g whenever a stock price changes)
    * you need to enable streams
* TTL - expire item in a dynamodb table - the epoch is expressed as an attribute on the table ,should be a number data type containing time in epoch format. Once timestamp expires the corresponding item is deleted frmo the table in the background. Streams can be used to process the deleted item giving a 24 hour backup window for TTL deleted items. Additional charges and maximum WCU limit may apply
* global tables- replicated tables in AWS regions. Consists of a multi master replication . Enable through global tables tab and enable streams (new and old images type) and it will create a service role it will use to create tables in other regions. 
    * table cannot be populated when you enable global tables functionality. You cant add additional regions once youve populated with data, you can remove regions however. When a region is removed the replica still exists along with the data in that region so it needs to be explicitly deleted. 
* web identify federation - used with mobile applications. 
    * you can restrict access to a particular item (full item or just an attribute) in dynamodb table based on a user id (fine grained access control)
    ```bash

        {
            "Sid" : "FullAccess",
            "Effect" : "Allow",
            "Action" : {
                "dynamoddb:GetItem",
                "dynamodb.Query"
            },
            "Resource" : {
                "arn:dynamodb.tablename",
            },
            "Condition" : {
                "ForAllValues:StringEquals" : {
                    "dynamodb.LeadingKeys" : {
                        "${www.amaon.com:user_id}"
                    },
                }
            },
        }
    ```
    * or A PARTICULAR attribute
      ```bash

        {
             ......
             "Condition" : {
                "ForAllValues:StringEquals" : {
                    "dynamodb.LeadingKeys" : {
                        "${www.amaon.com:user_id}"
                    },
                   "dynamodb:Attributes" : [
                       "id". 
                       "name",
                       ....
                   ]
                   
                },
                "StringEqualsIfExists" : {
                    "dynamodb:Select": "SPECIFIC_ATTRIBUTES"
                }
            },
        }
    ```
* DAX - in memory caching / accelerator 


# amazon_neptune
* graph database
* emphasis on the relationships between entities
* accessible with open source apis - tinkerpop gremlin, rdf sparql
* highly available - inside vpc , encryption at rest KMS
* Across AZs ( atlreadt 3)
* 64TB max storage - up to 15 read replicas
* server side encryption
* knowledge graphs
* fraud detection
* recommedation engine

# QLDB
* quantum ledger database (pre and post states of data)
* a way to audit database.
* has an append only ledger, using cryptography to ensure it cant be comprimised
* fully immutable database
* uses a document storage model - allowing data with complex nested structures to be stored and queried
* ACID based db
* strong transactional consistency - meaning an entire tranasaction completes or it is rolled back. 
* serverless - no IO provisioning
* sql supported
* changes are cryptographically verifiable using an hash chained journal
* when data is initiall added a hash is created of that data, when a new version is added a new hash is created of the current data plus the old hash, forming a chained
* makes tampering or changes immediately detectable and more data added the harder it is to fake this chained
* ideally suited to applications where validifty of data is a priority. ( finance, manufacturing, payroll, coting, insurance etc)
* billed for read , write and data transfers ( also billed for indexing and overall data size)

# documentdb
* uses rds system as backend but uses shared cluster storage volume
* RDMS v document db
    * table = collection
    * row = document (contains json structure collection of key value pairs, can be nested) - document has unique id. Document can have lists, arrays, embedded docs etc
    * column = field
    * pk = objectid
    * index = index
    * view = view
    * nested table = embedded document
    * array = array
* normalization  - remove repeated data out into seperate structures to make it more efficient to store (not needed in document db as we can store complex types inside each document)
* cluster is base entity inside documentdb
* choose size of instances in cluster - can have up to 16 instances ( 1 primary and 15 secondary)
* vpc, security group, subnets
* supports encryption at rest (KMS or default aws/rds)
* default port 27017
* point in time recovery - you specify retention period (35 day) - document db handles a single daily snapshot. It also constantly copies transactions into s3 allowing Point in time recovery
* cloud watch logs -  requires role
* use security groups for network ingress and egress
* you always create a single primary and 1 or more replicas - primary can read and write. Replicas scale read heavy workloads. Creating read replicas is a form of horizontal scaling used to increase read capacity
* you can scale vertically to scale write capacity
* similiar to Aurora it uses cluster storage volume to separate storage from compute. Single storage layer with 6 copies of your data across AZs. Replications and backups happen from the storage layer and not the databases
* highly durable and reliable - backs up data into s3
* you cant restore in place to the same cluster , must be to a new documentdb cluster
* you can restore to a specific Vpc or to the default vpc
* contiunually monitors health , restarts if needed, switches primary node to secondary automatically of failure occurs
* failing instances automatically replaced
* failures in any AZ are rapidly recovered from due to the architecture of storing data in cluster volume storage
* quicker recovery then most database competitors
* need mongodb shell to interact with documentdb
* add document to database via
```bash
    db.inventory.insert ( 
       { 
           "catid" : "0001",
           "desc" : "some desc",
           "details" : {
               "name" : "some name",
               "age" : "some age"
           },
           ......

       }
       )
```
* read all docs in database (even if you assign an id to yoru document, documentdb will assign its own id value)
```bash
    $db.inventory.find({}).pretty()
```
* used when you need document db 

# mapreduce
* data analysis architecture for huge data sets
* suitabale for data which can be modularized and executed in parallel
* high level split data set into smaller bits ,operate on the data at scale and recombine for reporting
* processes huge amounts of data using multiple nodes (compute resources)
* input data broken into splits (determined based on split size)
* split size is important. If splits are too large then less work in parallel. The more splits the more compute nodes we can have
* too many splits results in management overhead
* during map phase data is split and some function is executed on the data in parallel across compute nodes
* during reduce phase first part, schuffle phase,  the data resulting from each map phase is grouped
* then reducer task combines and summarizes into final output set
* s3 a great candidate to store data (input /output)
* where is intermediate data stored, the output from each of the map phases?

# EMR
* AWS implementation of hadoop mapreduce ( runs on EC2 in VPC)
* ecosystem of different software components (runs apache hadoop and apache spark , hive and pig)
* large scale distributed big data computation
* EMR can be launch in a number of ways 
    * 1. create cluster to do a specific piece or work. Either manually or let AWS do it, with data pipeline for example
    * 2. or as a long running cluster for multiple workloads
    * 3. create a cluster with the intent to interactively run commands using tools like hive against the master node
* has three types of nodes (master, task node and core nodes)
    * master node - manages the cluster,. controls distribution of workloads and health of all other nodes
    * core node - 0 or more core nodes. These nodes perform the tasks in map and reduce phase. They act as data nodes. Manage the HDFS filesystem (replication etc). If core node fails potentially you can loose data. Task control functionality managed by core node . You dont want any core nodes failing as it can cause issues with task control and hdfs. 
    * task node - optional, execute compute, no involvement to hdfs, may fail but less risk as no data stored and wont cause impact to wider cluster, only impacts tasks running currently on that node, If task node fails then the task is simply run on another node
* EMR can get input data from s3 and send output data to s3. - keep in mind storage classes based on needs
* Intermediate data can be stored on HDFS or EMRFS only . EMRFS however is backed by s3 backed cluster storage so if a core node goes down you dont loose any data. 
* outside of AWS, HDFS is the only file system data can be stored on ( data replicated between core nodes within the cluster) - If multiple nodes fail you greatly impact performance and durability of cluster. 
* if master node fails the entire cluster will fail as it handles task allocation and health of the cluster
* EMRFS offers persistent storage backed by s3 to be used inside cluster. 
* If we have a failure we have the data in s3. 
* EMR runs cluster in VPC, can be placed in public subnet if you need to access from outside AWS. 
* By default all the nodes in a cluster are stored in the same Subnet in same AZ to ensure fast and efficient communication between nodes. 

# EMR_contd
* when creating EMR cluster you get core set of applications ( you can choose your preferred tooling)
    * core hadoop : hadoop hgangila, hive, hue, mahout, pig, tez
    * hbase: hbase, gangila, hadoop, hive, hue, phoneix, zookepper
    * presto: presto with hadoop hdfs, hive, metastore
    * spark: spark on hadoop YARN , gangila, zeppelin
    * or you can manually install the different suites of software
* you can use AWS GLUE DATA CATALOG for table metadata
* review spark, pig, hive
* minimum size for EMR cluster is single instance which runs master node and core node on same EC2 instance
* ideally you have 1 master and several core on other nodes to scale
* ensure master node is not running on an ec2 family which can be interrupted 
* master node does not need much compute - use M5 (the instance type you select for master is fixed for the life of the cluster. you can switch in and out task and core nodes )
* you can use instance fleet ( a more complex setup) to run your master and core nodes. Each node type has its own instance fleet. Tasks nodes are otpional so task instance fleets are optional. In the fleet you can choose up to 5 instance types and whether they are on-demand or spot. 
* core nodes should be run on-demand instances or sometimes reserved if long running
* secure cluster with security groups and nACLs. Security groups are preferred as they can use logical resource reference

# EMR_performance
* provision EMR cluster in a region as close as possible to the source and destination for the data (same region as s3 bucket), Especially important if using EMRFS as a backend store.
* ec2 instances type selection is important - latest generations,  depending on the type of map/reduce work choose suitable instance family. General purpose instances are usually good enough (m5.4xlarge are a good compromise, anything in this region)
* use cloudwatch to analyse node performance
* master node is the hdfs main node and its other job is to distruibute tasks across core and task nodes so it doesnt require much compute unless only node in cluster
* only use reserved when you know usage long term (1, 2, 3years) - u set up emr cluster with certain type and purchase the reservation separately
* MER by default runs in a single AZ you not only reduce cost with reserved instances but also guarantee capacity in that AZ
* core nodes will be on-demand or reserved but task nodes have some variability and possibly spot node

# kinesis
* designed to accept messages from a potentially huge number of producers (any device that puts data records in kinesis stream)
* puts records in the stream by specifying the stream name, providing a partition key and the data to be added. 
* paritiion key allows kinesis select the particular shard used to ingest the data
* kinesis consumers consume data from the stream - you can have multiple consumers for the same stream
    * consumer types
        * ec2 instances running the kinesis consumer library (kcl)
        * lambda functions set to invoke based on stream data records
        * kinesis firehose
* kinesis streams can load to infinite levels of scale ( volumes of real time data)
* each kinesis stream has atleast 1 shard, add shards to scale, or remove as usage DenyUnEncryptedObjects
* video streams or data streams
    * data stream - 24hr retention period,rolling window , after 24 hr data expired, it can be increased to 7 days (which increases the storage the shard consumers). Data records add to stream and consumed by consumer. 
* performance of a given stream relates to performance of a shard as well as number of shards
    * each shard can handle:
        * 1 MB per second write capacity
        * 1000 written records per second
        * 2 MB per second reads
        * soft limit of 500 shards per stream which can be increased to whatever you require with a support request
* calculating how many shards you need = max(ingestion_in_Kib/1024, read_requirements_in_Kib/2048)
* amount of bandwidth available
    * per producer bandwidth = stream bandwidth/number of producers
    * per consumer bandwidth = stream bandwidth/number of consumers(* enhanced fanout)
* data record can be 1MB in size, 1000 written data records per second per shard. basic entity written to and read from kinesis stream. consists of a sequence number , partition key, and data blob. Data blob can be up to 1mb in size. Not altered in any way by kinesis. The sequence number is allocated by kinesis and is unique within its shard
* sdk chooses partition key if using sdk, otherwise you use
* you can scale kinesis stream by adding shards ( shards split with you increase and joined when you remove)
* you can use kms for server side encryption ( default or own CMK)
* you can enable shard level metrics ( extra cost, kinesis metrics are captured by default)
* kinesis is a public spaced service and does utilize public zoned endpoints. If you have a fleet of ec2 consumers wanting to consume the stream data you need to ensure you have the appropriate networing setup inside the VPC (internet Gateway or Nat Gateway). You can also utilize VPC endpoints. If using Lambda which is also a public based service you dont have any further network changes to make unless Lambda is configured to run in a VPC
* Producers and consumers share the stream bandwidth based on num shards
* You can use enhanced fan-out to guarantee consumers receives their own 2MB per second of read throughput per shard, improving the read performance for multiple consumer use cases. Consumers can opt-in to use enhanced fan-out for an additional cost. These consumers dont share the total shard bandwidth, instead they can have the total shard bandwith. You can configure 5 of these per stream as a soft limit but request extra by logging a support request. 

# kinesis_firehose
* fully managed elastic service to easily deliver realtime data streams ( from kinesis stream or direct Put or CloudWtach Logs, CloudWatch Events, AWS IoT) to destinations such as Amazon s3, Redshift, Elasticsearch,Splunk
* its also allows you to manipulate that data as its being delivered
* producers can PUT the data directly into firehose
* firehose can perform two types of transformations 
    * 1. it can utilize a lambda function ( you need to enable record transformation and select a lambda)
    * 2. convert record format ( translate between record formats, uses openC json serde, output format can be Apache Parquet, Apache ORC, you can reference schemas stored in AWS Glue)
* firehose can deliver into a destination service - s3, redshoft, es, splunk (with s3 you choose bucket and prefix and error prefix for failed transformations)
* firehose does support encryption at rest (if using Direct PUT data is stored on firehose otherwise if using kinesis stream as input data is stored in kinesis stream so any encryption used in the stream is also used as part of the firehose delivery stream)
* used when u need to take data out of kinesis or Iot and place in s3. ( For exmaple when you need to use a serverless query engine(athena which runs against s3 data) to analsyze data - you can use firehose to delivery data into supported destinations )

# kinesis_data_analytics
* source kinesis stream or kinesis firehose
* cna integrate with lambda ( some preprocessing of data before they are used in the data analytics application)
* utilise sql (or apache flink) based applications to apply to real time streaming data
* connect a data source as a link between kinesis data stream and in application input stream (virtual table representing contents of kinesis stream or kinesis firehose)
* once tables created you can run S1L queries against them (in effect running sql queries against data from kinesis stream )
* queries run against the data at the point in time taking retention into consideration
* can be continuous queries or windowed queries
* allows you create real time dashboards and reports
* output of queries go into an in-application output stream  ( another virtual entity , create on a per application basis). Output can be kinesis data firehose or writing data directly to s3. redshift, es etc
* You cna use reference data from s3 as part of teh queries. Inside your in-application virtual tables you can reference the data from s3

# AWS_Quicksight
* service which provides data visualization, it can integrate with other services to obtain data and present it in a visual and interactive way
* suited when collating data from  multiple sources, interact with data visually or when you need to adjust data in an interactive way
* dashboards, monitoring and merticsvisuak indicatio of a fleet of Iot devices
* can interact with Athena, Aurora, Redshift, s3, spark, mariadb, mysql
* can interact with unsupported datasources by using one of the supported integrations as an intermediary

# redshift
* petabyte data warehousing solultion inside AWS
* parallel processing product
* integrates with kinesis, data pipeline, s3
* solutions cna be deployed rapidly and for specific projects
* integrates with lots of aws services
* created initially as a fork of postgresql
* can cope with up to 2 petabytes of data? out of date now? Some instances allow 8petabytes (ds2.8xlarge)
* column based database
* data management based on column arrangement far more efficient then row arrangement
* when creating redshify dn the primary concern is the amount of data you need to process
* cluster contains a number of nodes
    * if one node only then compute and leader are same
    * if multi node you get the number of nodes you specify which act as compute nodes and also the an additional free node which acts as the leader node
* when creating cluster you can only choose from 2 instance types and size choices
    * dc2 instances ( dense compute): dc2.large and dc2.8xlarge
    * ds2 type (dense storage) - includes magnetic disks - used more for storage intense tasks where lots of data to process and speed and compute less important: ds2.large and ds2.8xlarge
* each instacne provides a number of slices or sub nodes/processing units. When the leader breaks the data into individual components it slices the data and nodes either have 2 or 16 slices
* when you load data for example from s3 or kinesis, the lead node takes the data and distributes across each slice on each compute node which each has a dedicated storage allocation
* data is distributed in several ways
    * 1. key dist type 
    * 2. all dist type 
    * 3. even dist type 
    * 4. auto dist type 
* using loading or copying to get data into Rddshift
* in order to utilize a multi slice cluster it is important you have multiple files in s3. If you only pass a single file than it will go to a single slice
* you wnat the files to be a multiple of the number of slices in the cluster
* unload operation used to unload the data back into s3 etc
* by default deployed into default vpc
* can be deployed in custom vpc - it can be public or private facing (if you choose this option you need to make sure it has access to talk to s3 to load and unload data) or configure to use vpc endpoints so it can talk to public services without requiring internet gateway or nat gateway
* you can purchase reservations
* supports encryption, enabled when creating cluster or afterwards ( use KMS and CMKS): aT REST AND IN-TRANSIT
* YOU ARE ABLE RESIZE A CLUSTER ; classic or elastic (Classic mode: you can put the cluster into read only mode, choose a new instance type and have aws create and then move data to new cluster OR Elastic resize where you can change the number of nodes but not the type, this is alot quicker)
* you can modify cluster after creation - change cloudwatch alarams, parameter group, encryption, security groups, enable public or private IP access, enhanced vpc routing, 
* you can define maintenance windows and snapshots. It also provides point in time recovery with constent backups to s3 ( using retention period)
* snapshot -1 is indefinite

# redshift_recovery
* takes periodic snapshots of the cluster every 6 or 8 hours or every 5GB per node whichever happens first
* automatically enabled
* all tables are automatically included in these backup snapshot - you can however set a preference per table to exempt it from backup ( use for staging or non production data)
* you can take manual snapshot
* use s3 for dr strategy for redshift ( if data truly production of nature then you can configure cross-region snapshots to automatically copy yoru automated and manual snapshots to another region. Your data transfer cossts incure are copied to the destination region)
* can perform fiull cluster restore or single table restore
* each slice in redshift replicates its data to another slice(on a different compute node) in the cluster
* when a compute node is allocted and when you view the storage capacity details, the number listed is only what is available to you and not the total available on the node. The total available is about 3 times the amount listed. This supports the replication of slices across compute nodes
* additional nods provide additional performance
* leader is free of charge
* you can copy automatic and manual snapshots to a different region and have independent retention periods

# aws_iot
* things = IOT devices
* IOT devices communicate with IOT device gateway ( over secure channels using JSON onto MQTT topics secured with X509 certificates )
* communication between iot devices and gateway might be Sporadic
* IOT maintains a device shadow which stores the state of the device as last reported. The shadow can be queried rather than communicating directly. The devcie shadow can also be written to, for example to set a desired state which the device will recieve the next time it communicates with the gateway
* IOT shadows allow for asynchronous communication with IOT devices and AWS services
* IOT devices can also publish to topics ( which are account and region specific and are hierarchical) with a constant flow of data
* by default IOT is pub/sub architecture so the sensors will publish to an IOT topic and then any subscribers will receive the update (MQTT industry standard)
* you can define IOT rules to tell aws to react in a particular way to a given sensor depending on the update/messages sent to the topic or from the device gateway (e.g if temperature above certain amount)
    * can react to message using 
        * Kinesis stream
        * cloudwatch alarm state
        * s3
        * dynamodb
        * republish via another IOT rule to another topic
        * lambda
        * step function
* basic ingest allows devices publish directly to rules using $aws/rules/rule0name avoiding costs incurred when using pub/sub

# Elasticsearch
* is an implementation of the ELK stack
* provides access rapidly to the data it stores
* schema-less making it easy scale
* distributed , parallel processing of queries
* you can horizontal scale providing additional throughput 
* stores information as documents ( ideal for storing varied data)
* document is a single line which is analagous to single row in database
* cluster is basic entity of elasticsearch ( 1 or mode nodes)
* can be 3 or 2 AZ.
* replication happens between cluster nodes so more AZs you provision the better resilency, and HA
* nodes in the cluster are data or master instances
* depending on the type of instance you create for your nodes you can add EBS volume or instance store. If you choose EBS storage then multiple storage size per node in the cluster to calculate the total storage available to yoru cluster. Storage settinsg do not apply to any dedicated master nodes in the cluster
* you can choose type of EBS storage , general purpose, provisioned IOPS, magnetic
* data nodes perform work ,searches and return the data and require most compute (cpu, memory and disk)
* msater nodes just perform management
* you interact with the cluster and the cluster handles interactions with all the nodes
* managed service providing an implemenation of the open source elasticsearch api and comes with kibana and logstash
* rapid data retreival (lucene)
* almost real time search
* integrate with cloudwatch logs
* log data is one of the most common use cases for elasticache(kibana)
* ELK stack ( 
    * elasticsearch (store,search and analyse), 
    * Beats and Logstash to ingest and transform data , 
    * kibana to visualize ( used for log visualization and favoured over quicksight(for data) for log or metric visualization). Kibana has discover plugin which allows you explore data, query and save searches, generate visualizations, dashboards which can be shared with other users
* purchase reserved instances if you plan to use for a long duration
* during creation you cna pick a deployment type 9(production (multi AZ), development(one AZ) and test, custom(choose custom topology))
* you can encrypt node to node (TLS) and enable at rest. Configured at setup
* you can take snapshots
* you can create in a VPC or configure for public access
* even if you select vpc it does not specifically run in vpc, instead it is in an isolated network and presentent into vpc using interface endpoint ( which have there own internal IP addresses and can be protected by security group)
* you can utilize cognition for authentication on kibana
* only readon master and data nodes are separated is because the types of functions data nodes execute are more compute and memory intensive then work master node does and separation allows you to allocate appropriate instance types for each use case. Also promotes isolation
* supports indexes - collection of related documents. Indexes can be broken up into shards and spread across nodes
* shards allow us scale out an index over other data nodes. One data node is primary and others are replica copies of the shard ( letting cluster recover if one node fails). Also improves throughput . When a query arrives it can choose bwteen either the master or replica
* create master eligible nodes gives greater resilence. If one master goes down then the eligible masters can decide who takes over. If possible have 3 master nodes and 3 or more data nodes
* if you have the choose to increase cores or slightly increase clock speed always increase cores as elastiache is optimized to run on multiple cores

# cloudwatch
* cloudwatch metrics , logs and cloudwatch alarams
* time ordered set of data points (metrics - a collection of data points) - cpu, objects in s3, IOPS, IOT sensor , 
* metrics have a timestamp, value, unit
* you publish metrics into cloudwatch for a period ( 1 second, 15, 1 minute, 5 minutes), its up to you then how long the data is retained
* if you publish data into cloudwatch for a period less than 60 seconds then they are only available for 3 hours  at that high resolution
* after that cloud watch aggregates the data together for long term storage
    * less than 60 seconds - available for 3 hours in cloudwatch then aggregated and avaialble 15 days
    * less than 300 seconds - available for 3 hours in cloudwatch then aggregated and avaialble 63 days 
    * less than 1 hour seconds - available for 3 hours in cloudwatch then aggregated and avaialble 455 
* metrics grouped together in namepaces (E.g ecs, eks , apigateway etc)
* you can create custom namespaces (aws/ is reserved)
* you can create dashboard containing any visible metrics you like
* you can create alarms to react to states in your metrics
* alarms can be in one of 3 states  
    * 1. OK 
    * 2. alarm
    * 3. insufficient_data
* alarams can take action when in the alarm state such as auto scaling, ec2 actions, or sns notifications
* cloudwatch events is able to take a rule based action which is able to initiate complext actions
* you can view history and adjust thresholds
* alarams allow you to convert mertics into actionable insights
* alarm can send notification to an SNS topic ( cna send email, invoke lambda etc) - spawn auto scaling actions, invoke ec2 actions (start stop etc)
 
# cloudwatch_logs
* starts off with number of key objects
    * log group - container for a group of log streams that share the same retention, monitoring and access control - log group a way to control access to individual log streams. Groups together related stream. Log group is where you specify metric filters and log control and majority of permission management and configuration for cloudwatch logs
    * log stream - sequence of log events that share the same source (a single line in a log file: timestamp which cloudwatch receives the message and raw message which actually comes from some service like ec2 - the timestamp in the message can be different). Log stream is a collection of log events for a given service. message coming in as json
    - you can create metric filters based on text in your log stream (inside a log group). Create the metric filter for example by filtering out occurences of some keyword in the logs. When creating the metric filter choose a metric namespace (similiar to how namespaces exist for ec2 , lambda etc) . This will then pattern match on any log stream in the log group
    - this metric publishes the matches into cloudwatch metrics every time a match is found ( choose the Sum statistic to see total count rather than average. Over time you cna then see trends in the data)

# cloudtrail
* logs events inside aws account
* turned on by default
* logging an api events within the account
* recorded for 90 days
* view cloudtrail event history (contains cloudtrail events) - stores event source, source ip address, username, event name, request id, read only, time, 
* available as a json block
* activity that occured against an account. might be from an IAM user, role (assumed role) or a service (maybe a lambda on your behave, vpc flow logs etc) thats monitored by cloudtrail
* you can completely customize cloudtrail for your own specific requriements by creating a trail
* the trail can direct the system to direct these cloudtrail events to s3, cloudwatch logs or cloudwatch events
* it can integrate with lots of other products and it is done by creating a trail
* you can create lots of trails to deliver to different s3 buckets for example
* you can apply trail to all regions or single region ( important to note this can potentially apply your configuration to all regions so you need to be sure what you are doing)
* trail includes global service events ( such as IAM,route53 ). If you have multiple trails each with these global service events you will have duplication - therefore apply trail to all regions so you only have a single record and deliver to single location
* you can also apply the trail within your organisation ( so every account in your organization gets same ) - and added to any new accounts created
* you can also include management events - which are certain control plane non api actions performer on resources which might occur on your account ( on by default for all read/write events)
* can also track data events - provide insights into resource operations performed on or within a resource. Get and Put requests for S3 and invocations of Lambda functions. You need to have cloudtrail enabled for s3 and lambda. 
* pick destination bucket - this allows us store the event history for longer than the cloudtrail 90 day limit. 
* you can enable encryption for s3 bucket, you can also enable log file verfiication to ensure logs have not been tampered with - ( knows if any logs removed ) - must be limted to s3 bucket , otherwise if iles moved around this validation process will fail
* send sns notification each time a log file is delivered 
* a prefix is uses when creating the s3 bucket - /AWSLOgs/unique org identifier/accoun id/CloudTrail/region
* cloudtrail free apart from storage
* you can configure trail to deliver to cloudwatch logs - by default trails deliver logs to s3
* using cloudwatch logs you have some advanced functionality. Metric filters etc 
* you select new or existing log group - and you need a role to write into cloudwatch 
* when writing cloudtrail logs to cloudwatch (across organization) you need to ensure cloudtrail role has permissions to deliver cloudtrail events to that logs stream for all trails in all aws accounts
```bash

    "Resource": [
        "arn::aws:logs:us-east-1312321312:log-group:CloudTrail/DefaultLogGroup:log-stream:97889789_Cloudtrail_us_east_1*",
        "organization-id"
    ]


```
* each account in the organisation will have its own log stream
* all cloudtrail events not presented as log events making it much easier review, search, create metric filters
* you can then use advanced functionality to stream log group to aws lambda or amazon elasticsearch service. 

# route53_logging
* only works for public zones
* r53 logging integrates with cloudwatch logs so cloudwatch log group is destination for any logging activity
* you can create new log group or use an existing one
* use aws default group name format - /aws/route53/example.com
* you need to grant it permissions to store logs into cloudwatch logs - you can use an existing resource policy or create a new policy (there is a limit on the number of resource policies you can create for each account so it is recommended that you test whether you can use existing policies before you create another one) - configured via role
```bash
    {
        "Effect" :"Allow",
        "Principal" :{
            "Service" :"route53.amazonaws.com",
        },
        "Action" :{
            "logs:CreateLogStream",
            "logs:PutLogEvents",
        },
        "Resource" :"arn:aws:logs:use-east-1:987897897:log-group:/aws/route53/*",
    }
```
* when logging enabled we get one log stream for each of the edge locations which is involved in the DNS infrastructure for the hosted zone which you have enabled logging
* uses an IAM role to add permissions for logging to cloudwatch loggroup

# s3_logging
* s3 server access logging
* server detailed access logging provides logging for all the requests that are made to a bucket
* essential you can log an s3 bucket access logs into another s3 bucket
* the log delivery group needs to be granted access via an entry in the bucketACL
* source bucket and target bucket needs to be in same region
* you can speicify target prefix if you want to use same target for multiple source buckets
* if your enable from console it will enable permissions for you
* In target bucket under Permissions, Access Control List of the bucket under S3 log delivery group needs access to write objects and read bucket permissions 
* every 10-20 mins files delivered.
* cant put into cloudwatch logs as it is legacy logging structure

# aws_systems_manager
* important for managing the following at scale [ ec2 instances, on-prem servers, on-prem virtual machines]
* a collection of products
* manages resources inside an aws account as well as on-prem (physical or virtual) by using an SSM agent (installed on all recently installed AMI that run in AWS)
* you thing you need to do is give the instance permissions to talk to SSM
* for older ec2 instances you may need to install one of the provided packages from AWS to bring your instance to a state where SSM can manage
* for non AWS instances there are extra steps that need to be taken to get working with SSM , called activations
* with SSM you can change unmanaged ec2 and on-prem resources into SSM managed resources
* an ec2 or on-prem server becomes a managed instance by installing the SSM agent and either assigning IAM permissions and an activation code if the compute resource is not an EC2 instance. 
* for instances running inside a VPC they need internet gateway (or VPC endpoint) to access public zones where SSM endpoints operates
* IAM role needs permissions to fully engage with SSM. 
```bash
    "Statement": [
        "Effect":"Allow",
        "Action":[
            "ssm:DescribeAssociation",
            "ssm:GetDocument",
            "ssm:ListAssociations",
            ...
        ],
        "Resource":"*",
    ] 

```
* ssm documents - define actions SSM can perform and they can be used by state manager, run command, automation, They are controlling directives and can be written in YAML or JSON
* ssm functionality ( once instance is a managed instance you cna do a number of things)
    * inventory : lets ssm collect information about the instances ( what software is installed, what configurations are used, network config, services, windows roles, custom inventory, aws components, applications, file, windows registry) (inventory collection can be applied to all instances or ones with specific tag or manual selection)
    * Run Command - execute a document on 1 or more instances. You effect a change in configuration at scale to 100s of ec2 instances if required. Or effect a desired state. 
    * Automation - allows you create automations, workflow, installing software on an instance, performance and configuration, any automation you require. A set of actions essentially which happen on the managed resources. Lets you create a stack role with only SSM permissions and this can be assigned to the automation. You can assign the automation role to someone without assigning the role for the actual instances. 
    * State Manager - a desired state engine. You define the desired state in the form of a systems manager document. A document can be a command document or a policy document. A command document is used by running command and state manager. A policy document defines desired states and is only used by State Managed. A document is associated with one or more managed instances.  
    * Patch Manager - allows how up to date we want instances to be in terms of patches, maintenance windows, scan and install or scan only etc. Fully configurable
* all the services SSM provides are interrelated to achieve desired outcomes

# ssm_parameter_store
* secure storage for configuration data and secrets in a hierarchical and highly resilent way
* supports versioning, can be audited, supports access control
* parameter can be string, list of strings, or secure string
* when creating secure string you use KMS to manage encryption using CMK or allow SSM use default key
* when giving ec2 or lambda or any other service access to your secure params be sure give them access to both param store and the KMS key used to encrypt
* you can use hierarchical nature to choose whether you want specific value or all values under a particular path. E.g /prod will return all child paths. /prod/connections/db will only return values at that path
* parameter store allows you distribute parameters at scale to thousands of ec2 instances, lambdas, auto scaling groups etc
* public zone endpoint
* integrates with many AWS services including code build and cloudformation templates
* serverless resilent and scalable

# ElasticBeanstalk
* aws has three deployment services: Elasticbeanstalk , Cloudformation and Opswork
* platform as a service  - handles all of the associated infrastructure required to run your application - you worry about application only
* application is the foundational element for Elasticbeanstalk - a container of environments, versions, environment configurations
* Environment: an isolated environment , the infrastructure ElasticBeanstalk manages on your behalf (web server or worker) and onto which you provision your application
    * web server - run a website, application, web api that serves http requests
    * worker - application that processes long running workloads on demand or performs tasks on schedule
    * when creating an environment you need to select the platform you want provisioned
        * docker - multi container, running on linux 3
        * go
        * JAVA
        * NODE.JS
        * PHP
        * PYTHON - preconfigured docker
        * RUBY
        * TOMCAT
        * .NET
        * GLASSFISH - preconfigured
* Application version: a distinct version of application code (app bundle) which can be deployed into an environment
* you have a number of options when you configure an environment (low cost (no load balancer, single instance), high availablity (has a load balancer, multi nodes, 1-4 across AZ), custom configuration)
* elasticbeanstalk is based on cloudformation so when you create environments it is running cloudformation stack in the background
* application versions represent code and one can be deployed to an application environment (the code itself can be stored in s3, can be a zip file, a war file etc, it cna even integrate with github)
* every application environment has its own endpoint url
* you can create additional environments with different platforms inside the same Elasticbeanstalk Application
* Elasticbeanstalk gives you the power to swap applicaton environment urls allowing for blue/green deployment allowing you have 2 versions of your application running independently you caa deploy new version into one environment and swap urls. If the new version works then continue to use that or swap URLS back again 
* provides resilent way to do application deployment
* rapid failover between versions
* if you have multiple instances in one environment you can deploy new application in a number of ways
    * all at once - existing version if overwritten
    * immutable - new environment provisioned with new configuration. Once running the old one is destroyed and the URL is swapped
* emvironment configuration changes , like updates to instance numbers or types can be done as rolling update to prevent downtime of your application instances
* you can deploy databases with elasticbeanstalk however they are tied to the lifecycle of the application environment and will be destroyed if the environment is destroyed
* any databases should be provisioned outside Elasticbeanstalk
* You can save the configuration of an elasticbeanstalk environment into yaml. You cna use this configuration to restore the environment at another point
* eb extensions - inside the environment version source you can add a folder caled ebextensions and in that folder include files for the configuration of elasticbeanstalk. For example to provision an SQS queue of SNS topic to provision as part of your environment. These extension files are mini cloudformation templates which can be used to influence the services provisioned as part of elasticbeanstalk environment creation

# Opsworks
* deployment platform 
* sits between cloudformation which gives ultimate flexibility and elasticbeanstalk which entirely manages provisioning of infrastructure
* removes alot of admin overhead without losing too much flexibility
* works with chef automate and puppet enterprise
* built around the idea of a stack - stack is a top level construct in Opsworks
* stacks consist of layers and layers are aligned to application tiers
* stack is global configuration for an entire application
* OpsWork and chef in general operate around the concept of a cookbook
* stacks are created based on chef 12 (windows or linux) or 11 (linux)
* opsworks is a global service and you dont seletc the region when using it
* stack options
    * you pick the region it goes into
    * vpc
    * subnet
    * you can use custom chef cookbooks - point at repo
    * default OS/AMI
    * set SSH key to access EC2 provisioned by OpsWorks
    * choose EBS backed (slower to start and more expensive) or instance store instances to provision
    * select instance profile - gives the instances permissions it needs to interact with various services
* you might have a layer for RDS, one for ECS, one for ELBs etc
* you can create layers which integrate with existing rds or ecs instances ( providing auth and address information automatically to the rest of the stack)
* alot of configuration settings happen at the layer level - like auto healing, 
* on the layer you define recipes that impact different instances in that layer (e.g recipes for setupm configure, deploy, undeploy, shutdown)
* layer configure network, security, ebs volumes, cloudwatch logs, rols, tags
* can create 3 instance types
    * 24/7 - on always unless you stop them (great for base load)
    * time based - you can control start and stop for different time periods (great for time variance load, busy days of the week, sale period,. this instance type can supplement 24/7)
    * load based - control instances coming on line if cpu above a certain percentage (you dont know what requirments will be so you set targets )
* for a given layer you can add additional instances
* instances are inside layers and are effected by recipes in those layers
* Apllications: in opswork an application is an entity that points at source code you want to deploy or run on an applictaion server. It also contains some other config
    * code for application doesnt exist within Opswork, you point opsworks at a repository (git 9 you can specify ssh key to use), s3, http)
    * you can register database and provide authentication information
    * you can add environment variables
    * configure domain settings and ssl
* Once application defined you can use Deployment recipe for a given instance and that will deploy aplication code to an instance. 
* opsworks can monitor all the various layers and instances across the stack
* you can manage permissions at stack level using IAM roles to grant particular access to interact with Opsworks stack
    * you can deny users access to the stack, read only access, access to deploy only, access to manage, or access to show stack
* supports tagging
* uses chef architecture


# aws_data_pipeline
* serverless product that lets you create workflow style data migration and data transformation pipelines
* base entity is a pipeline with a set of work/tasks
* create a pipeline using various options including cli, other shell activities, pre configure or custom templates (from dynamodb, elastic map reduce, rds, redshift)
* for dynamodb set a source table and an output s3 folder. Also specify a read throughput value to prevent performance impact on dynamodb table. Set region of dynamodb table
* specify a schedule or on activation for the pipeline to run 
* enable logging to an s3 bucket if required
* specify the IAM role or use defualt provided service role
* specify tags if required
* data pipeline can utilize different aws services to carry out tasks. For example for data intensive tasks it can use EMR to execute task in parallel. 
* data pipeline handles spinning up the EMR cluster, once the task is complete the cluster is torn down and no longer used
* data pipeline can perform large scale migrations of data ( export the data from dynamodb in the first pipeline and in a subsequent pipeline choose template ti import dynamodb backup data from s3)
* with data pipeline you can create really complex and hierarchical structure with lots of decision steps and preconditions to automate alot of your business migration logic

# aws_disaster_recovery
* overall goal is to provision resources in your DR region to match your prod region ( cloudformation lends itself to do this)
* backup and restore - RTO/RPO: Hours, low priority use cases ,S3 , storage gateway costs relatively low
* pilot light (minimal version of the environment is alway runing in the dr area - you can use cloudformation to create the stack) - RTO/RPO: 10s of minutes, core services , scale in repsone to DR events, cost little higher 
* warm standby (secondary instance runs in background to primary, data is mirrored at regular intervals, at times both servers may be out of sync) - RTO/RPO: Minutes, business critical services, more expensive
* multi-site (running across region, route 53 routing prod 80% and dr 20% , data is replicated) - RTO/RPO: Near real-time, auto failover of environments in AWS, cost most
* with RTO - recovery time objective we are worried about how much time before we need the system restored
* WITH RPO - recovery point objective we are worried about how much data can we afford to loose , how far back can we restore the system
* cloudformation can create the stack in the disaster recovery region ( multi site is running at all time)
* warm standup - your entire application is running but in a scaled down configuration - so in DR scenario your are scaling up entire dr environment ( similiar to pilot light)
* pilot light - always have minimal version of aplication in DR region, like a database. If an DR happens you scale up your db and provision rest of the infrastructure using CF , use custom AMIs
* when executing cloudformation template during DR scenario it is crucial AMIs listed in template are up to date and exists. Using lambda this can be achieved
    * lambda function can lookup AMIs
* cross stack references - 

# snowball
* 3 product 
* snowball 
    * storage appliances provided by AWS which can store 50TB or 80TB of data. Economical when transferring more than 10TB between on-prem and AWS or vice-versa. Data encrypted in transit to and fron the snowball.
    * loaded by storage interfaces
    * shipped back to AWS and loaded into S3
    * used for larger quantities of data above 10TB
    * process of getting snowball and shipping back to AWS faster than efective transfer rates using internet
* snowball edge
    * similar to snowball but also provide local compute services allowing them to run processing at the edge such as lambda functions and instances. Used when data needs to be processed or analyzed during the upload ( remote locations with poor connectivity)
        * snowball edge storage optimized - 100TB
        * snowball edge comput optimized - normal storage
        * snowball edge with gpu - normal storage
    * up to 100TB per device
    * can use locally to run IOT devices with greengrass
    * operating from some remote location and need to perform some analysis on your data before shipping to AWS
* snowmobile
    * mobile datacenter
    * can be driven to your data center , connected and loaded with huge quantities of data before returning and loading into AWS
    * used for data center migrations
    * or when 10PB of more needs to be migrated from a single location
    * for less than 10PB or when multiple locations are involved - use 1 or more snowball/snowball edge 
    * each snowmobile can store 100PB and they can be used in parallel
* storage gateway is an alternative to use if operating below the 10TB mark or if you need to do over time progressively
* snowball encrypted at rest and in transit - uses KMS (you manage the keys)

# SQS
* managed message queue
* allows you decouple or integrate applications
* messages between servers are retiieved through polling
    * long polling - allows sqs service wait until a message is available in a queue before sending a response.less api calls (1-10 seconds)
    * short polling - you ask the queue for any messages currently visible, can return no messages, lots of api calls
* messages have a limit of 256kb of text in any format (larger messages use s3)
* two queue types
    * fifo - designed where order is important, where duplicates cant be tolerated, Limited to 300 operations per second, 3000 messages per second under optima conditions with batching. Have performance ceiling
    * standard - guarantee delivery atleast once but no guarantee of order . Can scale to almost unlimited level of performance
    * visibility timeout - how long message is invisible after it has been polled ( if sqs doesnt recieve a delete operation for a particular message after a certain amount of time it will pop back onto the queue and someone else can consume)  -allows for retries 
* workers traditionally will poll a queue to retrieve waiting messages for processing. 
* lambda functions can now replace worker instances to poll and process messages
* auto scaling can be applied based off of queue size so that is a component of your application has an increase in demand the number of worker instances can increase. 
* aws services used for loosely coupled systems are SWF and SQS
* SQS settings
    * default visibility timeout - length of time in seconds that a message recieved from a queue will be invisible to other recieving components
    * message retention period - amount of time that SQS will retain a message if it does not get deleted
    * maximum message size - 256kb is hard upper limit but it can be adjusted
    * delivery delay - amount of time to delay the first delivery of all messages added to this queue
    * receive message wait time - upper limit of 20 seconds for this long polling value
    * use redrive policy - messages that cant be processed can be redirect to a secondary queue
    * dead letter queue - must be existing queue name
    * maximum receives - between 1 -1000
    * you can encrypt with SSE (cmk using KMS)
* use receiptHandle to delete messages from the SQS queue
* monitoring shows umber messages in the queue, messages sent , recieved etc allowing you scale and process effectively
* not designed for multiple consumers, you can rely messages, or have multple consumers consuming same message ( kinesis good for replay and multiple consumers)

# SNS
* notifications system
* its not a queue
* use lambda for true elasticity
* durable across regions, not dependent on AZs,  - its highly available ,higly resilent
* event driven compute
* when used with SQS can implement fan out pattern- allowing each queue to perform unique and independent processing
* coordinates and manages the sending and delivery of messages to subscribers
* can use SNS to recieve notifications when events occur in our AWS environment
* integrated with many AWS services
* with ckloudwatch and sns, a full environment monitoring solution can be created that notifies admins of alerts, capacity issues, downtime, changes in the environment and more
* can be used for mobile push messages
* contains topic, subcriber and publisher
    * topic - object to which you publish messages ( max 256kb). subcribers subcriber to topics to recieve messages
    * subscriber - an endpoint a message is sent to, can be an api endpoint. Message are sent to subscribers simultaneously. (http, https, email, sqs, application, lambda, sms)
    * publisher - the entity that triggers the sending of a message - e.g application, s3 event, cloudwatch alarm

# AWS_MQ
* AWS MQ exists inside VPC and only accessible outside if you configure it that way
* SQS is a 1:1 architecture (queue)
* SNS is 1:many (notifications product)
* AWS MQ - based on Apache Active MQ product 
    * Not an AWS developed services and therefore not accessed with AWS CLI
    * use when you require a standards complaint message broker
    * when you need to use protocols like AMQP, MQTT, OpenWire, STOMP or an existing broker on-prem
    * if you need compatibilty with JMS API
    * can focus as queue or 
* SNS and SQS have public zone endpoints AWS MQ does not
* AWS MQ can be deployed as single instance or highly available par (active/standby)
* AWS MQ supports topics and queues and a third entity called virtual topics ( analogous to architecture of SNS fan out to SQS queues)
* AWS MQ also supports network of brokers, across regions - global messaging service
* Use MQ when you have a complex topology of message ( stock processing , audit, analysis, etc), you need ordered messages, reliability, and need to interact based on industry standard APIs
* not controllable with aws security permissions or APIS, it does however integrate with cloudwatch

# aws_stepfunctions1
* workflow services in a serverless way
* main entity is a state machine, controls the flow of the workflow ( orchestrates movement between states)
* states exist in state machine
    * task state - works via an activity like an Lambda (or ec2, ecs, sqs queue, ses, sns) 
    * choice state - allows for loops etc
    * fail or succeed state
    * pass state - pass data between states
    * wait state - wait for a certain number of seconds
    * parallel state
* execution can last anywhere up to 1 year
* states can allow interactions with humans

# saml_federated_sso
* security assertion markup language
* 3 entities involved
    * user - has an account at the IDP (maybe their employer)
    * Idp ( identify provider) - the organization that holds the list of identities
    * service provider - target service (maybe AWS)
* when user attempts to go to service provider endpoint IDP kicks in an validates the user is who they say they are and are Authenticated. The IDP then constructs a message for that user and communicates to the service provdier
* the IDp sends this message to deferated software running on the service provider
* the sp then uses its federated software to ensure request came from a trusted IDP and creates session of user in target system 
* this activity is completelt transparent to the user
* its reusable - 


# vpc_subnetting
* 10.0.0.0/16 local route
* if subnet routed to internet gateway it is known as public subnet (must have an Ip or elastic IP address)
* subnet without internet gateway is a private subnet
* if subnet doesnt have a route table to the public internet but has traffic routed to virtual private gateway for a site to site VPN connection the subnet is a VPN only subnet. 
* you can extend your VPC to Amazons local zones (for s3 etc) by creating a new subnet that has a local zone assignment. When you create a subnet in a local zone the vpc is also extended in that local zone
* you must provision public IP for use in local zones
* when creating a vpc you must specify a CIDR block range which must be within /16 or smaller
* the cidr block of a subnet can be the same as the cidr block for VPC or a subset of the CIDR block  for the VPC   
* the allowed block size is between /16 and /28
* cidr blocks cannot overlap
* a subnet is a range of ip addresses, all devices in the same subnet can communicate directly with one another without going through any routers
* 10.0.0.1: Reserved by AWS for the VPC router.
* 10.0.0.2: Reserved by AWS. The IP address of the DNS server is the base of the VPC network range plus two
* 10.0.0.3: Reserved by AWS for future use.
* 10.0.0.255: Network broadcast address. We do not support broadcast in a VPC, therefore we reserve this address.


# vpc_endpoint
* by default security groups outbound allows all access
* privately connect vpc to supported AWS services and VPC endpoint services powered by private link without requiring an internet gateway, nat device, vpn connection or aws direct connect . Instances in your VPC do not require public IP  addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network
* gateway and interface endpoint
* gateway endpoints use route prefixes in your route table to direct traffic meant for S3 or Dynamodb to the Gateway Endpoints 
* interface endpoints (Elastic network interface). It uses DNS record to direct your traffic to the private IP address of the interface.
* endpoint policies:
    * when you create an interface endpoint, you can associate security groups with the endpoint network interface that is created in your vpc, if you do not specify a security group the defualt security group for your vpc is automatically associated with the endpoint network interface. You must ensure that the rules for the security group allow communication between the endpoint network interface and the resources in your VPC that communicates with the service
    * gateway endpoint - if security group for some reason blocks outbound than you need to create rule using gateway interface prefix list allowing communication between vpc and service specified in your endpoint. Use service prefix list ID as destination in the outbound rule
* Endpoint connections cannot be extended out of a VPC. Resources on the other side of a VPN connection, VPC peering connection, transit gateway, AWS Direct Connect connection, or ClassicLink connection in your VPC cannot use the endpoint to communicate with resources in the endpoint service.

# readinglist

- [OSI model](https://en.wikipedia.org/wiki/OSI_model)
- https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html
- https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html
- https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html
- https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2-instance-metadata.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html#example-bucket-policies-use-case-8
- https://aws.amazon.com/blogs/security/iam-policies-and-bucket-policies-and-acls-oh-my-controlling-access-to-s3-resources/
- https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/useconsolidatedbilling-discounts.html
- https://docs.aws.amazon.com/general/latest/gr/aws-general.pdf#aws-service-information
- https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html
- https://aws.amazon.com/premiumsupport/plans/
- https://docs.aws.amazon.com/servicecatalog/latest/adminguide/getstarted-iamenduser.html
- https://aws.amazon.com/ec2/pricing/
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-reserved-instances.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html
- https://github.com/open-guides/og-aws#billing-and-cost-management
- https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_saml.html https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_oidc_cognito.html
- https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html
- https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic.html
- https://www.theprohack.com/2012/01/ip-subnetting-easy-way.html
- https://console.aws.amazon.com/ram/home#Setting
- https://docs.aws.amazon.com/ram/latest/userguide/working-with-az-ids.html
- https://docs.aws.amazon.com/ram/latest/userguide/what-is.html
- https://docs.aws.amazon.com/vpc/latest/userguide/vpc-sharing.html
- https://en.wikipedia.org/wiki/Ephemeral_port
- https://linuxacademy.com/blog/linux/connect-to-amazon-ec2-using-putty-private-key-on-windows/
- https://www.crucial.com.au/blog/2011/04/15/ipv6-subnet-cheat-sheet-and-ipv6-cheat-sheet-reference/
- https://community.cisco.com/t5/networking-documents/ipv6-subnetting-overview-and-case-study/ta-p/3125702
- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resolver.html
- https://d1.awsstatic.com/whitepapers/building-a-scalable-and-secure-multi-vpc-aws-network-infrastructure.pdf
- https://aws.amazon.com/about-aws/whats-new/2019/12/aws-transit-gateway-supports-inter-region-peering/
- https://docs.aws.amazon.com/vpc/latest/tgw/what-is-transit-gateway.html
- https://en.wikipedia.org/wiki/FIPS_140-2
- https://docs.aws.amazon.com/kms/latest/developerguide/importing-keys.html
- https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html#enveloping
- https://aws.amazon.com/blogs/security/how-to-protect-the-integrity-of-your-encrypted-data-by-using-aws-key-management-service-and-encryptioncontext/
- https://docs.aws.amazon.com/kms/latest/developerguide/grants.html
- https://aws.amazon.com/kms/features/#compliance
- https://docs.aws.amazon.com/cloudhsm/latest/userguide/initialize-cluster.html
- https://docs.aws.amazon.com/acm/latest/userguide/acm-concepts.html
- https://aws.amazon.com/shield/features/
- https://docs.aws.amazon.com/waf/latest/developerguide/aws-shield-use-case.html
- https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html
- http://www.brendangregg.com/blog/2017-11-29/aws-ec2-virtualization-2017.html
- https://aws.amazon.com/blogs/aws/ec2-instance-history/
- https://aws.amazon.com/ec2/instance-types/
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/burstable-performance-instances.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html
- https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/install-CloudWatch-Agent-on-EC2-Instance-fleet.html
- https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Agent-Configuration-File-Details.html
- https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/create-cloudwatch-agent-configuration-file.html
- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/using_awslogs.html
- https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html
- https://docs.aws.amazon.com/lambda/latest/dg/runtimes-custom.html
- https://docs.aws.amazon.com/lambda/latest/dg/runtimes-walkthrough.html
- https://docs.aws.amazon.com/lambda/latest/dg/configuration-layers.html#configuration-layers-path
- https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-caching.html
- https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started-http-integrations.html
- https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started-aws-proxy.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-scheduled-instances.html
- https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/spot-fleet.html
- https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-termination.html
- https://aws.amazon.com/elasticloadbalancing/features/#compare
- https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html
- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/listener-authenticate-users.html
- https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/introduction.html
- https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/high_availability_origin_failover.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/secure-connections-supported-viewer-protocols-ciphers.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/cnames-and-https-requirements.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-signed-urls.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/georestrictions.html#georestrictions-cloudfront
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/field-level-encryption.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ConfiguringCaching.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-event-structure.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-requirements-limits.html
- https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/AccessLogs.html
- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html
- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/traffic-flow.html
- https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/traffic-policies.html
- https://aws.amazon.com/premiumsupport/knowledge-center/multivalue-versus-simple-policies/
- https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html#ConsistencyModel
- https://docs.aws.amazon.com/AmazonS3/latest/dev/ListingKeysHierarchy.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/BucketRestrictions.html
- https://aws.amazon.com/s3/storage-classes/
- https://docs.aws.amazon.com/AmazonS3/latest/dev/PresignedUrlUploadObject.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/optimizing-performance.html
- https://docs.aws.amazon.com/AmazonS3/latest/user-guide/enable-transfer-acceleration.html
- https://docs.aws.amazon.com/amazonglacier/latest/dev/data-retrieval-policy.html
- https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html#transfer-acceleration-requirements
- https://docs.aws.amazon.com/amazonglacier/latest/dev/retrieving-vault-info.html
- https://docs.aws.amazon.com/amazonglacier/latest/dev/vault-inventory.html
- https://docs.aws.amazon.com/amazonglacier/latest/dev/vault-lock.html
- https://docs.aws.amazon.com/amazonglacier/latest/dev/working-with-archives.html
- https://docs.aws.amazon.com/efs/latest/ug/performance.html
- https://docs.aws.amazon.com/efs/latest/ug/performance-tips.html
- https://docs.aws.amazon.com/efs/latest/ug/using-amazon-efs-utils.html
- https://docs.aws.amazon.com/fsx/latest/WindowsGuide/using-file-shares.html
- https://docs.aws.amazon.com/fsx/latest/WindowsGuide/high-availability-multiAZ.html
- https://docs.aws.amazon.com/fsx/latest/WindowsGuide/group-file-systems.html
- https://docs.aws.amazon.com/fsx/latest/WindowsGuide/limits.html
- https://docs.aws.amazon.com/storagegateway/latest/userguide/HardwareAppliance.html
- https://docs.aws.amazon.com/storagegateway/latest/userguide/StorageGatewayConcepts.html
- https://neo4j.com/blog/acid-vs-base-consistency-models-explained/
- https://www.digitalocean.com/community/tutorials/a-comparison-of-nosql-database-management-systems-and-models
- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.html#UsingWithRDS.IAMDBAuth.Availability
- https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.Enabling.html
- https://aws.amazon.com/premiumsupport/knowledge-center/users-connect-rds-iam/
- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-serverless.how-it-works.html
- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/data-api.html
- https://aws.amazon.com/about-aws/whats-new/2019/08/amazon-aurora-multimaster-now-generally-available/
- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Replication.html
- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-serverless.how-it-works.html
- https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/data-api.html
- https://docs.aws.amazon.com/athena/latest/ug/querying-AWS-service-logs.html
- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-indexes-general.html
- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadConsistency.html
- https://docs.aws.amazon.com/documentdb/latest/developerguide/document-database-documents-understanding.html
- https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-release-components.html
- https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-instances-guidelines.html
- https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-instances-guidelines.html
- https://docs.aws.amazon.com/kinesisanalytics/latest/dev/continuous-queries-concepts.html
- https://docs.aws.amazon.com/kinesisanalytics/latest/dev/windowed-sql.html
- https://docs.aws.amazon.com/kinesisanalytics/latest/dev/examples.html
- https://docs.aws.amazon.com/redshift/latest/mgmt/enhanced-vpc-routing.html
- https://docs.aws.amazon.com/redshift/latest/dg/c_choosing_dist_sort.html
- https://docs.aws.amazon.com/awscloudtrail/latest/userguide/creating-an-organizational-trail-prepare.html
- https://docs.aws.amazon.com/awscloudtrail/latest/userguide/creating-an-organizational-trail-prepare.html
- https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.managing.db.html
- https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.RDS.html
- https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions.html
- https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environment-cfg-manifest.html
- https://docs.aws.amazon.com/opsworks/latest/userguide/workinginstances-autohealing.html
- https://docs.aws.amazon.com/opsworks/latest/userguide/opsworks-security-users.html
- https://docs.aws.amazon.com/opsworks/latest/userguide/workingcookbook-installingcustom-components-recipes.html
- https://docs.aws.amazon.com/opsworks/latest/userguide/workingstacks.html
- https://docs.aws.amazon.com/opsworks/latest/userguide/workinglayers.html
- https://docs.aws.amazon.com/opsworks/latest/userguide/workinginstances.html
- https://docs.aws.amazon.com/opsworks/latest/userguide/workingapps.html
https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-how-pipeline-definition.html
https://docs.aws.amazon.com/datapipeline/latest/DeveloperGuide/dp-concepts-datanodes.html
https://docs.aws.amazon.com/snowball/latest/ug/whatissnowball.html
https://docs.aws.amazon.com/snowball/latest/developer-guide/how-it-works.html
https://docs.aws.amazon.com/snowball/latest/developer-guide/BestPractices.html
https://docs.aws.amazon.com/snowball/latest/developer-guide/device-differences.html