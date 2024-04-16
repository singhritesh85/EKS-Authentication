# EKS IRSA

EKS IRSA stands for **Elastic Kubernetes Service IAM Role Service Account**. It is used to provide access to kubernetes Pods so that it can access AWS serivces.
<br> <br/>
```
1. An IAM Policy should be created which allows to access the respective AWS Service.
2. Create an IAM Role with Trusted Entity Type as Web Identity using Identity Provider of EKS OIDC and Audience as sts.amazonaws.com. 
```
Here I have created an IAM Policy with the Name S3BucketAccessK8S as shown in the screenshot below

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/9c1c6ca6-62ee-43a8-8650-9d90e8b2c8b7)

An IAM Role has been created with the name S3BucketAccessK8SRole as shown in the screen shot attached below

```
(a) First of all open console for IAM and open Identity Providers as shown in the screenshot below

    ![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/95ff4e89-0a71-4c74-9392-309e9d38fa7c)


```
