# Provide EKS Authentication to IAM Users

IAM Users can be authenticated to provide EKS Cluster Access. We can create IAM User and add them to the group in aws-auth configmap present in kube-system namspace of the EKS cluster. The system:masters group represents the cluster-admin.
<br> <br/>
Here I have created two users named as user1(Any test user) and rajesh(EKS Administrator) and as a best practice I have added these users to the group group1 and admin-group respectively.
Two IAM policies had been created AmazonEKSNodesAndWorkloadsViewPolicy and EKSAdminPolicy. Attach these policies to the group group1 and admin-group respectively as show in the screenshot attached below.

<br> <br/>
IAM Policy for AmazonEKSNodesAndWorkloadsViewPolicy
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/d9c03a76-a3da-426b-ad8b-2252497a7ac8)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/258c418c-2a29-4cc5-aa7f-cfe72e92d9eb)

<br><br/>
IAM Policy for EKSAdminPolicy
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/074750dd-05ff-4fca-a0f0-c86d899f5567)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/6eb43d38-381c-464d-bec3-555e36746ff5)

<br><br/>
Two groups, attached policy to each group and users attached to each group is as shown in the sreenshot attached below
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/545a846f-7c49-4b3e-a687-ee30e965c608)
<br><br/>
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/789a1c60-fcc2-49d5-aa75-acc5b26f8aa1)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/f4fcdea0-32d0-454e-871b-be97c1c70e54)
<br><br/>




