# internal DNS
1. Create hosted zone
2. Assocaite with VPC , select type Private hosted zone
3. Create record set using private IP address of EC2
4. Use nslookup calling record set name and verify name resolution

# Flow logs
Can be enabled at three levels (VPC, subnet and resource). Collects metadata about the networking interface traffic. Does not log request body. Creates log file for each ENI. Does not log metadata requests in EC2 (these requests are isolated inside EC2 instance)
