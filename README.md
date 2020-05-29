# internal DNS
* 1. Create hosted zone
* 2. Assocaite with VPC , select type Private hosted zone
* 3. Create record set using private IP address of EC2
* 4. Use nslookup calling record set name and verify name resolution

# Flow logs
* Can be enabled at three levels (VPC, subnet and resource). Collects metadata about the networking interface traffic. Does not log request body. Creates log file for each ENI. Does not log metadata requests in EC2 (these requests are isolated inside EC2 instance)

# SSH into EC2 instance
* download key pair
* chmod 600
* connect using ec2-user

# sharing resources across aws account
* use AZ ID which is the physical id of the AZ. The AZ name on the other hand cna be different between accounts although underneath the hood it points at same physical infrastructure. Therefore choose AZ Id

# VPC Router
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

# routing from on-prem to VPC
* Use VPC inbound endpoint
* highly available
* resolves internal only DNS names
* Lets on-prem resources connect to the inbound endpoint which routes to Route53 resolver and resolves to any of the internal only DNS

# routing from vpc to on-prem
* use VPC outbound endpoint
* create rules which decide how to forward DNS requests for specific target IP addresses which might be on-prem
* when routing between VPC and on-premise networks inbound/outbound endpoints are the recommended approach

# configuring on-prem dns with DHCP
* create dhcp options set using domain name and name server IP address
* select the EC2 and edit dhcp option set
* restart the ec2 isntance
* when the instance restarts it will automtically use the dhcp option set over route 53 to connect to on-prem DNS server

# nat gateway
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

# DNS EC2
* resolver + 2. DNS server address also know as R53 resolver and only accessible withing the VPC
* Public DNS - resolves to ipv4 public address when called from outside AWS. When called internally it resolves to the internal DNS
Private DNS - internal network interface of EC2 and not accessible from outside AWS


# EGRESS GW
* for ipv6. 
* Each IPVC resource automatically gets its own ipv6 public address
* Cant use NAT gateways with ipv6
* Egress GW allows ipv6 service speak to public internet
* By default ipvc not allocated cidr blocks in VPC creation

# EGress GW creation
* 1. need ipv6 cidr block allocation to vpc
* 2. need ipv6 allocation to subnet
* 3. need to allocate ipv6 to the instance
* 4. need egress only gateway  and attached to VPC


# Network wildcards
* IPv4 0.0.0.0/0
* IPV6 ::/0

# Using NAT 
* 1. Create Nat GW
* 2. Associate subnet ( private subnets in AZ)
* 3. Create Route table for each AZ and associate with private subnets in each AZ
* 4. Associate NAT in each AZ with private subnets

# NACL
* Network ACL's do not apply when communicating between EC2s in the same subnet

# internet gateway
* type of NAT that uses static NAT 

# bastion host
* Communicates with outside world using IGW which handles translation between internal address and public IP
* Has public subnet
* Public IP
* Configured to accept public traffic
* Allows connections from bastion host into private network subnets
* You can use more complicated security to  link your corporate security provider
* You can restrict based on specific ssh key or IP address

# private subnet
* cant communicate with public internet or public zone services like S3 , Cloudwatch, dynamoDB, starts

# public subnet 
* Has internet gateway
* Has route table pointing at internet gateway
* add 0.0.0.0/0 to IGW represents lowest prefix and all traffic
* Modify subnet association in route table and addd desired subnets.
* Doing this removes the default table association for each subnet
* Subnet cant only have 1 route table associated with it
* Option to auto-assign IP address in VPC for new resources (ec2)

# NACL 
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

# vpc flow logs
* can take 5-15 minutes to show up in cloudwatch logs after traffic and log created
* when writing to an S3 bucket AWS automatically updates the bucket policy to allow VPC flow logs to write to the bucket
* VPC Flow logs can write to several sources from cloudwatch to S3
* Use Athena to run queries against flow logs stored in S3

# vpc gateway endpoints
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

# vpc interface endpoint
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

# vpc peering
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

# vpc peering cross region
* You need the vpc id of the remote VPC
* You cant refer to security group so create subnet rule allowing all traffic 10.0.0.0/16
* does not support ipv6
* security group logical reference does not work
* private dns hostnames can be resolved but must be enabled
* Uses AWS private backbone ( has some latency)
* Fuly encrypted

# vpc peering 
* routing is not transitive
* You can enable requestor and acceptor DNS resolution. Which allows each VPC to resolve DNS of requestor VPC hosts to priavte IP addresses

# vpn site to site
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


# Route table order of precedence
* routing - local route always takes priority
* routes with the highest prefix (cidr range) are favored 
* if two routes with identical network then any static routes take precedence over propagted
* direct connect always preferred over VPn
* static vpn favored over dynamic
* finally dynamic vpn


# vpn v direct connect
* vpn can be configured in a matter of minutes
* vpn is cheap
* vpn per hour cost/data charge ( higher than direct connect)
* vpn do use encryption end to end and there is a cost for using this
* vpn performance limited by internet under higher loads

# direct connect
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

# direct connect public VIF 
* operate in a single region
* capable of accessing public zone endpoints ( s3 etc in any region)
* cant use public VIF to access the internet
* direct connect public VIF still better than the public internet in terms of latency even if you are making requests internationally 
* customer publi VLAN

# direct connect private VIF
* limited to regions - can only connect to virtual private gateway in the same region
* one option is to layer a VPN connection over your direct connect infrastructure giving access to public and private gateways
* 1:1 relationship between Private VIF and customer private VLAN

# direct connect gateway (new)
* allows you to create direct connect gateway which can abstract details of each private VIF from customer private VLAN. This allows customer to connect to VIFs across any VPC and any region by relying on BGP in the Direct Connect Gateway
* customer only connects with Direct COnnect Gateway and doesnt need to worry about each private VIF
* not transitive device ( supported VPCs cannot communicate unless explicitly peered)

# AWS Transit Gateway
* Adds additional capability over virtual private gateway ad vpc peers
* we can connect vpc peers and vpn to Transit Gateway which provides transitive behavior ( hub and spoke)
* Transit gateway has multiple route tables allowing complex routing hierarchies to be defined from true hub and spoke to edge consolidation and anywhere in between
* Can link different networks in different AWS accounts
* Now supports Direct Connect (introducing a new virtual interface called the transit virtual interface to support connectivity to AWS Transit Gateway)
* vpn and vpc attachments are placed in AZs, adding routing to that AZ. You can add support for each AZ in the VPC
* Supports peering connections between Gateways in many AWS regions
* Support DNS resolution
* Can have default route table assoication and propagation

# Creating Transit Gateway
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

# connect ec2 instance to s3 bucket 
* for public subnet use internet gateway
* from private subnet use VPC enpoint in preference to NAT gateway
* vpc endpoint connects directy to se as it doesnt use public internet so better latency also
* subnet is public when it has a route to IGW

# create vpc endpoint between ec2 and s3
* create new endpoint
* select s3 service names
* select vpc 
* configure route tables by selecting private route table id associated with private subnet which you want to update
* Choose the default policy
* Create and verify route table associated with private subnet making sure prefix list (with ip addresses S3 uses) for VPC endpoint is added . Also double check route table associated with correct subnets

# peering across regions
* use VPC id for peering target ( acceptor)
* setup route table
* plugin route for requestor vpc in other region and select peering connection
* do the same for public route table in requestor vpc
* add route with destination IP of vpc in remote region and select peering connection
* chair key pair between regions ( create key pair in acceptor vpc , download the key pair, then in requestor vpc import key pair under network and security section of ec2 by providing public key)
* create ec2 instance in requestor vpc and choose existing key pair when launching
* use ssh -A to propagate SSH key between acceptor EC2 and requestr EC2 in different regions. Privatley connected and not using public internet

# aws security ( KMS )
* CMK - capable encrypt up to 4k data
* CMK represents one or more backing keys ( like a shortcut)
* regional service
* CMK never leaves the service therefore never leave the region, never leave KMS , never leave hardware
* CMK are stored securely internally and you only interact via apis 
* Access to the CMK managed through policy
* Key alias - like a shortcut. Regional based so aliases can be same name in different regions but underneath they will refer to different cmks
* CMK keys are only used for encrypting data up to 4K and this works fine for some services in AWS like SNS, Elasticache however for larger data sets normally you give KMS your CMK and ask it to generate a data encryption key.
* Data encryption key returns encrypted and unencrypted data key. You use the unencrypted data key to encrypt the data and then discard that key. To decrypt the data you send KMS the encrypted data key abnd ask it to look after decryption. 

# kms commands
* aws kms create-key --description "sample" --region us-east-1
* aws kms create-alias --target-key-id eqeqeqweq  --alias-name "alias/sample" --region us-east-1
* aws kms generate-data-key --key-id alias/sample --key-spec AUES_256 --region us-east-1 (returns plaintext and ciphertext version of data key bsae64 encoded)
* need to based64 decode keys before use ( cat plaintext | base64 --decode)
* encrypt using plaintext key - (echo "test data" | openssl enc -e -aes256 -k fileb://whereyousavedplaintextstring
* ask kms to decrypt data
    * decode the encrypted version of data key (cat encrypted_datakey | base64 --decode)
    * aws kms decrypt --ciphertext-blob filen://./decodedkey --region us-east-1
    * the response from kms then needs to be decoded also => (echo "returned decoded string" | base64 --decode > secret.txt)
    * then use open ssl and the decoded plaintext decryption key to view data ( cat secret.txt | openssl enc -d -aes256 -k fileb://decoded_datakey)
