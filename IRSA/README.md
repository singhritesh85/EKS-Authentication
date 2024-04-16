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

(a) First of all open console for IAM and open Identity Providers as shown in the screenshot below

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/8d8abf50-6bc2-425b-a55c-f44aedc36dde)

(b) Identity Provide with the same OIDC as of EKS has been created when you will create the EKS using terraform script https://github.com/singhritesh85/terraform-eks-withaddons.git as shown in the screenshot below

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/d3ae0690-18d7-4730-8720-e7bab806e449)

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/387c00c0-4b55-46eb-814a-d24e84c25387)

(c) Create IAM Role as shown in the screenshot attached below

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/4d5deced-efc1-45dc-9182-52c6e58c8400)

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/b5932743-8bf3-4cc2-a4da-19d7b9821aa0)

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/489238bb-b206-49ee-9bd4-4970e2906810)

(d) Edit the Trust Relationship of IAM Role as shown in the screenshot attached below

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/1be1cb76-42d2-4848-8eab-d241a5b3e10f)

Add the suffix in the second line of StringEquals to sub instead of aud of the first line and system:serviceaccount:demo:app. where demo is the namespace into which the serviceaccount will be created and app is the name of the serviceaccount.

(e) Finally create the namespace demo, serviceaccount app, deployment prahar in the namespace demo and use the created serviceaccount app in it and using this service acccount access the file index.html present in s3 bucket. 

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/30097c9f-82e5-4c97-9e9f-50b0da9a9019)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/12f261dc-538d-4ff1-9f3b-57139ad361bf)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/886d6838-831e-43ea-9e2b-17135cfde356)
<br> <br/>

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/f595213b-a564-4623-8070-3ae20810dd2a)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/68a72e04-54fe-4299-b368-57ad985a29bc)




