# IAM-Role based Authorization

**When you Authorize an IAM User directly to access the AWS EKS cluster and after the employee left the organization then entry for that User's ARN is still present in configmap aws-auth which is present in namespace kube-system.** 
