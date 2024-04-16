# IAM-Role based Authorization

**When you Authorize an IAM User directly to access the AWS EKS cluster and after the employee left the organization then entry for that User's ARN is still present in the configmap aws-auth which is present in the namespace kube-system.** 

```
1. Here my intention is to create two users named as demo-user(any test user with restricted access) and rakesh(a cluster administrator) and provide them their respective authorization using IAM Role.
2. create IAM user group named as demo-group and admin-group and IAM Policy named as AmazonEKSNodesAndWorkloadsViewPolicy and AmazonEKSAdminPolicy. Create two IAM Roles AmazonEKSNodesAndWorkloadsViewRole and AmazonEKSAdminRole.
3. As a best practice attach users demo-user and rakesh to IAM User Group demo-group and admin-group respectively.
4. Create Assume Role Policy AmazonEKSAssumeEKSNodesAndWorkloadsViewPolicy and AmazonEKSAssumeEKSAdminPolicy for the IAM Role AmazonEKSNodesAndWorkloadsViewRole and AmazonEKSAdminRole as the Resource respectively.
5. You can create Role, RoleBinding, ClusterRole and ClusterRoleBinding as per your requirement.
6. group system:masters represents cluster-administrator.
7. It is Important to note here after providing credentials (Access Key and Secret Key) using aws configure, create profile in ~/.aws/config file as shown below
[root@rakesh-system ~]# cat ~/.aws/config
[default]
region = us-east-2
output = json
[profile rakesh]
role_arn = arn:aws:iam::027330342406:role/AmazonEKSAdminRole
source_profile = default 
```

![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/011e77bc-c6a6-4ef0-bdae-0c05e824815b)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/b1ef94e9-36a9-460a-b596-17a5c2bc3e4a)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/469074b0-9f79-4c28-b239-fab347b02273)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/47632f1b-3bb8-4179-a68a-5a1cfd43ea5a)

<br><br/>
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/2daeb19c-0071-4b1e-b528-e2d19aa4d7c9)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/dfad6336-f516-4169-9b57-c260b22dfb5a)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/58782fef-cf4a-4e5f-a4cd-13b361d7aa30)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/edfbe8f0-7a7a-489c-bfc4-34cdc053053d)

<br> <br/>
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/17ed618d-14fb-48ee-a692-601314f495de)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/b47745e0-8645-47fd-9d57-a6f13b5e6441)

Screenshots Attached below for IAM User, IAM User Group and attached IAM Policy.
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/3de0f783-ec40-47ef-9511-60a3e0e03bcc)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/408edc52-3de2-4fca-8332-9beb898fcddb)

<br> <br/>
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/aa33cf5c-56fb-4090-a6a1-15ecd784980e)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/7b025611-c5a9-4fcd-b06e-13174a4f9457)

<br> <br/>
**Entry for Configmap aws-auth in namespace kube-system has been done as shown in the screenshot below**
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/d7b8a234-4cbe-45c8-a373-d19515585ee5)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/28d25bcf-a9f0-4b15-8da8-6f6dea76ed8e)


**Authenticate and Authorize your system to access the EKS cluster.**
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/1af0e600-37c8-4c44-8e3c-8f93a5625c92)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/a0240a83-b610-4034-af77-e11d9d0815d7)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/f164c906-6e85-49fc-8b42-057604d68e41)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/bcbed4b3-09e0-4c62-909d-be4a7d7599b8)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/e9e23c3c-d0fc-4b10-871a-c8f67eaaf744)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/86c24373-507f-4117-ba90-46d361ff8d06)

<br> <br/>
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/df3a4d9a-0368-46ce-9edc-36c084fd0474)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/51d52c45-0917-4158-afea-6c239edbf2cb)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/3573d723-b79e-4fdd-b43f-034a882e82c5)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/5f275a03-b88f-41c2-b24e-b991f1de4f4b)

**How to Access EKS Cluster from the AWS Console for these Users**
<br><br/>
Open the URL and provide Account ID, Username and Password and login into the AWS Console.
Then open a new tab and open "Link to switch roles in console" (URL which was shared with you), these URLs shared for IAM Roles AmazonEKSNodesAndWorkloadsViewPolicy and AmazonEKSAdminPolicy.
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/5a960710-fe79-4069-b63b-559ba8b039fd)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/0282f9f4-e1ce-4f53-8f34-47879b22798b)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/967d6ca2-49fb-4ca4-84fb-e48dbbd581fa)

<br> <br/>
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/92788b1c-3031-4c3f-9c8b-8f285535b6be)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/0642f610-b25b-4348-a83d-459b4acd7875)
![image](https://github.com/singhritesh85/EKS-Authentication/assets/56765895/97a68fde-42d7-4b1c-9852-256238fd4f39)




