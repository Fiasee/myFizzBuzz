# Fizzbuzz
<h3>FizzBuzz as a service deployed using Terraform on EKS</h3>

Follow the steps outlined here for a smooth deployment (assuming kubectl and aws-iam-authenticator have been installed:

1. Clone the repo

2. Update your own ip address inside master.tf by replacing A.B.C.D

3. Configure your AWS credentials using a set of IAM credentials with access to create AutoScaling, EC2, EKS, and IAM resources. 

4. Run the below commands after cloning the repo (provide region to be deployed in if prompted);
   - <h4>Terraform init</h4>
   - <h4>Terraform plan </h4>
   - <h4>Terraform apply </h4>

5. Once the cluster has been deployed, configure kubectl to talk to the EKS master cluster
   
   To configure Kubectl, update kube-config using the awscli command below to attach kubectl to the cluster;</n>
   <h4>aws eks update-kubeconfig --name {clustername} --aws_region {region} </h4>
    
6. Establish communication between the EKS master cluster and the worker nodes
   
   <h4>terraform output config_map_aws_auth > config-map.yaml</h4>
   <h4>kubectl apply -f config-map.yaml</h4>
   
   Now, <h4>kubectl get nodes</h4> will return the nodes in the cluster 
   
 7. Deploy the fizzbuzz app;
 
    - the below command will deploy the app;
      <h4>kubectl create -f .</h4>
    - get the external dns address of the app by running;
      <h4>kubectl get svc</h4>
    
    
   
   
   


