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