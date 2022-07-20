# wordpress_eks_with_rds
## Deploy WordPress Pod in EKS with RDS
Idea & Tutorial Credit to https://www.linkedin.com/pulse/wordpress-deployment-aws-eks-cluster-mysql-rds-using-khanday

Prerequisites and Testing Environment! AWS Account, Cli, EKS, kubectl, eksctl and RDS

Create a new cluster and node in EKS

- eksctl create cluster -f cluster-create.yaml
- Connect with your cluster - aws eks update-kubeconfig --name your-clutser --region ap-southeast-1
- Check all resources are ready - kubectl get all
- Create a RDS for wordpress - kubectl apply -f create-rds.yaml

Once RDS is ready, deploy a new pod for WordPress site

- kubectl apply -f wordpress-site.yaml
- Expose your service with ELB - kubectl expose deployment/wordpress --port 80 --target-port 80 --name wordpress-service --type LoadBalancer


After that, browse your ELB url, configure the required settings in WordPress dashboard for your website. 

That's it. Enjoy!!
