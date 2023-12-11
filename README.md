# Vprofile Deployment in Kubernetes

First: Create a kubernetes cluster with kOps
<br>
`kops create cluster --name=your-cluster-name --state=s3://your-s3-bucket --zones=us-east-1a --node-count=2 --node-size=t3.small --control-plane-size=t3.medium --dns-zone=your-dns-hosted-zone --node-volume-size=8 --control-plane-colume-size=8`
<br>
`kops update cluster --name=your-cluster-name --state=s3://your-s3-bucket --yes`
<br>
Then validate your cluster creation with
<br>
`kops validate cluster --state=s3://your-s3-bucket`
<br>
Your cluster should be ready before proceeding
<br> <br>
Second: Create an EBS volume
<br>
`aws ec2 create-volume --availability-zone=us-east-1a --size=3 --volume-type=gp2`
<br>
This volume will be used to store the MySQL data
