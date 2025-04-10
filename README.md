# LSC
## Installation

### aws 
```script
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

### kubectl
```script
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

### helm
```script
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

## EKS config 
Cluster and node group was created through GUI \
Credential from aws academy copied to ~/.aws/credentials
```script
aws configure set default.region us-east-1
aws configure set default.output table
aws eks describe-cluster --region us-east-1 --name lsc_cluster --query cluster.status
aws eks --region us-east-1 update-kubeconfig --name lsc_cluster
```

## Apply deployment, service, pvc and job 
```script
kubectl apply -f development.yaml
kubectl apply -f pvc.yaml
kubectl apply -f service.yaml
kubectl apply -f job.yaml

# get external ip of service
kubectl get svc lsc-service
```
