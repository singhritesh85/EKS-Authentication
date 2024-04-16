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
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/5fe17880-9bc2-4959-9abd-1b07a2c4ab71)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/bd5aa39b-73b2-4997-a666-dbabb5eb5107)

<br> <br/>
Create Role and Role-Binding which will be utilized for the test-user user1. Another user rajesh will be attached to group system:masters in aws-auth configmap of kube-system namespace. The cluster administrator will be directly attached to system:masters group.
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/09420d79-7d50-4e51-88ba-26bb56cf1e24)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/1e3d91b8-137b-4807-bc2d-7b585215f3c6)

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/201a3a19-1fee-4b65-9729-08167fffe5dc)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/f1a56c8b-0251-4564-8889-d1c1d74df41b)
<br><br/>
Initially the configmap is as shown in the screenshot attached below
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/944d7259-5417-4b61-9c47-a8fd95099d4f)
<br><br/>
configmap aws-auth present in namespace kube-system will be edited
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/90caebe0-c969-46b9-b403-979d3929199e)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/5479e330-2fe6-4d42-b940-f735879d4159)
<br> <br/>
Now users user1 and rajesh will have the restricted and cluster-admin access as shown in the screenshots attached below
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/24f3a465-9927-46d2-8eb0-dc993b5db42c)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/74088dbf-058b-4d9b-8ac8-7e6fc5bac9cc)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/748370d3-82a7-463e-80ed-ee2316bd6b1d)


![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/c3e322c7-db21-435b-9e83-4aad1d64b8ec)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/47236b75-f1e8-4c94-9a94-68af408d6bf1)







