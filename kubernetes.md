## EKS
### AWS_VPC_K8S_CNI_EXTERNALSNAT
EKS 的網路問題，由於 AWS EKS 的 SNAT 幫 VPC 中的 private IP 轉成 internet gateway IP  
在沒有 internet gateway 的情況下，導致連線有問題  
- [The case of the missing packet: An EKS migration tale](https://yashmehrotra.com/post/2020-03-16-case-of-missing-packet/)
- [External source network address translation (SNAT)](https://docs.aws.amazon.com/eks/latest/userguide/external-snat.html)
- [amazon-vpc-cni-k8s](https://github.com/aws/amazon-vpc-cni-k8s)

