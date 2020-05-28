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

