# Task-1

1. Create key pair

C\> aws ec2 create-key-pair --key-name mykey --query 'KeyMaterial' --output text > mykey.pem

2. Create a security group

C:\>aws ec2 create-security-group --group-name MySecurityGroup --description "security group for cli" --vpc-id vpc-af54b6c4

2.1 Write Firewall rule in Security Group

c:\>aws ec2 authorize-security-group-ingress --group-name MySecurityGroup --protocol tcp --port 22 --cidr 0.0.0.0/0

Where, 0.0.0.0/0 to allow public access, To Restrict public access provide Ip-address of the system from which the instance to be accessed.

3. Launch an instance using the above created key pair and security group.

C:\>aws ec2 run-instances --image-id  ami-0e306788ff2473ccb --count 1 --instance-type t2.micro --key-name mykey  --security-group-ids sg-0d12af00eaf27538b --subnet-id subnet-d1ebe0b9

4. Create an EBS volume of 1 GB.

C:\>aws ec2 create-volume --volume-type gp2 --size 1 --availability-zone ap-south-1a

* Before Attachment: -

No alt text provided for this image
5. Attach the EBS volume to the instance.

C:\>aws ec2 attach-volume --volume-id vol-03fad6d4d0b9a0fe2 --instance-id i-0360fd35bb67346ba --device /dev/xvdb
