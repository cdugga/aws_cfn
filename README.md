# internal DNS
1. Create hosted zone
2. Assocaite with VPC , select type Private hosted zone
3. Create record set using private IP address of EC2
4. Use nslookup calling record set name and verify name resolution

# Flow logs
Can be enabled at three levels (VPC, subnet and resource). Collects metadata about the networking interface traffic. Does not log request body. Creates log file for each ENI. Does not log metadata requests in EC2 (these requests are isolated inside EC2 instance)

# SSH into EC2 instance
download key pair
chmod 600
connect using ec2-user

# sharing resources across aws account
use AZ ID which is the physical id of the AZ. The AZ name on the other hand cna be different between accounts although underneath the hood it points at same physical infrastructure. Therefore choose AZ Id

# VPC Router
has default router which occupies single IP address ( network +1 address)
E.g if IPv4 cidr block is 10.10.80.0/20 then router is 10.10.80.1
VPC router highly available
Route table defines how subnet handles traffic when it arrives at interface
Every VPC has a main route table
Subents which do not have a custom route table are assoicated with the default VPC route table
One route table assigned per VPC
Every route table starts with local route which can't be changed or deleted
All resources created within VPC can communicate unless network ACLS used
Route tables are processed in order of precedence. The higher the CIDR range

# routing from on-prem to VPC
Use VPC inbound endpoint
highly available
resolves internal only DNS names
Lets on-prem resources connect to the inbound endpoint which routes to Route53 resolver and resolves to any of the internal only DNS

# routing from vpc to on-prem
use VPC outbound endpoint
create rules which decide how to forward DNS requests for specific target IP addresses which might be on-prem
when routing between VPC and on-premise networks inbound/outbound endpoints are the recommended approach

# configuring on-prem dns with DHCP
create dhcp options set using domain name and name server IP address
select the EC2 and edit dhcp option set
restart the ec2 isntance
when the instance restarts it will automtically use the dhcp option set over route 53 to connect to on-prem DNS server

# nat gateway
allows 10s or 100s of machines access the internet with same IP address. Eases congestion in IPv4 address space. 
Cant use Nat gateway with ipv6
nat gateway has a public IP address
When NAT receives request from internal IP it converts to its public IP but does'nt allow conversion in teh other direction
Its a managed service
resides in public subnethas elastic IP address ( which is static)
Not highly available so for HA you need to create instance in each AZ
NAT GW allows you to connect to public internet, S3, DynamoDB, 
Does not allow port forward
Does network address translation and keeps record

# DNS EC2
resolver + 2. DNS server address also know as R53 resolver and only accessible withing the VPC
Public DNS - resolves to ipv4 public address when called from outside AWS. When called internally it resolves to the internal DNS
Private DNS - internal network interface of EC2 and not accessible from outside AWS


# EGRESS GW
for ipv6. 
Each IPVC resource automatically gets its own ipv6 public address
Cant use NAT gateways with ipv6
Egress GW allows ipv6 service speak to public internet
By default ipvc not allocated cidr blocks in VPC creation

# EGress GW creation
1. need ipv6 cidr block allocation to vpc
2. need ipv6 allocation to subnet
3. need to allocate ipv6 to the instance
4. need egress only gateway  and attached to VPC


# Network wildcards
IPv4 0.0.0.0/0
IPV6 ::/0

# Using NAT 
1. Create Nat GW
2. Associate subnet ( private subnets in AZ)
3. Create Route table for each AZ and associate with private subnets in each AZ
4. Associate NAT in each AZ with private subnets

# NACL
Network ACL's do not apply when communicating between EC2s in the same subnet

# internet gateway
type of NAT that uses static NAT 

# bastion host
Communicates with outside world using IGW which handles translation between internal address and public IP
Has public subnet
Public IP
Configured to accept public traffic
Allows connections from bastion host into private network subnets
You can use more complicated security to  link your corporate security provider
You can restrict based on specific ssh key or IP address

# private subnet
cant communicate with public internet or public zone services like S3 , Cloudwatch, dynamoDB, starts

# public subnet 
Has internet gateway
Has route table pointing at internet gateway
add 0.0.0.0/0 to IGW represents lowest prefix and all traffic
Modify subnet association in route table and addd desired subnets.
Doing this removes the default table association for each subnet
Subnet cant only have 1 route table associated with it
Option to auto-assign IP address in VPC for new resources (ec2)

# NACL 
can only deal with individual IP addresses or CIDR block ranges and not resources names like security groups
NACL do not impact resources in same subnet
You can assoicate NACL with multiple subnets
Each subnet can only have a single NACL
If two identical rules exist but DENY exists then DENY will be acted 
Rules processed in order of priority
NACL handles responses using ephemeral port ranges
Request and response are handled independently 
It is stateless - cant differentiate if request is a response or the initial request
Outbound requests when internal request is destined for outside subnet boundary
NACL operate in space around a subnet
Every VPC has a default acl and is associated with any subnet in that vpc that does not have its own ACL
By default NACL allows all traffic in both directions

# vpc flow logs
cant take 5-15 minutes to show up in cloudwatch logs after traffic and log created
when writing to an S3 bucket AWS automatically updates the bucket policy to allow VPC flow logs to write to the bucket
VPC Flow logs can write to several sources from cloudwatch to S3
Use Athena to run queries against flow logs stored in S3

# vpc gateway endpoints
10GB per second bandwidth
s3 and dynamodb only
NEED TO BE INSIDE vpc TO UTILIZE
gateway and 
gateway endpoints exist inside VPC ( not inside subnet)
can be referenced route table
tied to a service and vpc
you can associate polices with gateway endpoints
you can restrict policies of resources so they can only be accessed by a particular VPCendpoint
They appear in route table with pl-79878979 (unique number) ( prefix list which is a representation of all the IP addresses at this public endpoint (so s3 for example) - the public address space for the service in that region)
With gateway endpoint you can provide access to services running in the aws public area without giving access to the wider internet
Using gateway endpoints you can create completely private storage for a specific VPC
Can be secured using policies not security groups

# vpc interface endpoint
10GB per second bandwidth
Support majority of AWS public services
Utlize DNS or private DNS
ENI'services
different to gateway endpoints as they do not have entry in route table
instead puts phsyical entity in specific subnet
They occupy a subnet as a physical object/ network interface
They are not highly available so need to create across all AZs 
Uses private link to provision
Create endpoint network interfaces inside your VPC
Can carry traffic to remote vendor or remote VPC over secure private communication channel
Can be secured using security groups ( interface endpoints are network level devices)
Interface endpoints comes with its own set of DNS names - which resolves to internally IP address. 
    There are DNS names for each AZ and also one for the regio
By default hostnames resolve to the public IP addresses of SQS, s3 etc 
You can enable private DNS names to utilize the Route 53 resolver which once enabled means Route 53 will respond when any of teh public hostnames are called by returning the internal DNS names. This means you do not need to modify any of your applications using the public hostnames when you want to enforce use of the interface endpoint

# vpc peering
accounts limit blast radius, isolated
connect vpc's with peering
highly performant , resilent and easy to implement solution to link VPC at network level
3 steps to make VPC peering work
    1. Create Peer, requires invite and accept. This creates VPC peer object between 2 accounts (requestor is where VPC is created. Need to make sure no overalpping cidr blocks. peering request needs to be accepted)
    2. Configure route tables of any subnets at either end of the VPC connection (which you want to participate in the peering connection) to allow communication between VPCs. By default subnet will only have local route (10.0.0.0/16). Need to add the cidr range for the remote VPC and then select peering connection and select the new peering connection. Do the same in the remote VPC
    3. Configure security entities (ensure none of the NACL prevent the peering connection). Configure security groups around instances you are connecting to and check rules. One option is to create a rule that allows all traffic from cidr block of remote VPC.
    ** If the peering connection is in the same region then we can reference the remote security group in the local vpc security group when creating inbound rules ( this is a logical reference). This can also be done for security groups in different accounts using the security group identfiier and the aws account number. This process however does not work across regions
Every VPC peer gets unique id