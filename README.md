
# AWS Solutions Architect Professional - Notes
> Preparation notes for the AWS Certified Solutions Architect Professional examination

---

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