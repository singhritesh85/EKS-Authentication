# EKS IRSA

EKS IRSA stands for **Elastic Kubernetes Service IAM Role Service Account**. It is used to provide access to kubernetes Pods so that it can access AWS serivces.
<br> <br/>
```
1. An IAM Policy should be created which allows to access the respective AWS Service.
2. Create an IAM Role with Trusted Entity Type as Web Identity using Identity Provider of EKS OIDC and Audience as sts.amazonaws.com. 
```
