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
