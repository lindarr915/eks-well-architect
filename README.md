# EKS Well Architect Review 

### Operational Excellence 

* You provision EKS cluster and nodes using Infrastructure as Code templates 
* You deploy Kubernetes resources using versioned manifest files, preferred stored in a Git Repo.
* The application deployment of newer version is via an automated CI/CD tool  
* You proactively review the usage of why humans need `kubectl` access for production environment, address the  concerns using automation with CI/CD pipelines and deprecate the use of human access. 

### Centralized monitoring and logging

* You are centrally capturing EKS control plane logs and use GuardDuty in EKS to view suspicious events.
* Your are collecting worker nodes metrics
* You are centrally capturing and storing log messages from your workload or pods.
* You are collecting metrics exposed by your application, and store them in Prometheus or CloudWatch 
* You have a dashboard to  provides a summary view of a service’s core metrics
* You have alarms to notify the teams if the service is not meet SLO 

### Security

* Your EKS Cluster Endpoints are private; if public, restrict access with allowlist IPs
* You implement the principle of least privilege and enforce separation of duties  with appropriate authorization for each namespace within the EKS cluster.  
* You  restrict access to `kube-system` namespace as the function of super  administrators only
* You use a dedicated IAM role to create clusters which is not used to perform routine actions on the cluster
* You use  separate production EKS clusters from non-production EKS clusters on an  account level.
* You have a process that supports  the secure ingestion and vulnerability scanning of container images
* You have tools or process to review security configurations and prevent pod privilege escalation
* You have strict control of SSH or SSM access to worker node. Accessing to worker node is a break-glass action is not done on a daily basis. 
* You use IAM Role for Service Account instead of using static credentials or environment variables in the container.  
* You leverage AWS Secrets &  Configuration Provider or EKS secrets encryption to manage secrets in EKS

### Reliability

* You deliberately spread out application replicas to different worker node in different availability zones for redundancy
* You leverage Kubernetes  liveness, start-up or readiness probes to detect software failures in your  Pods and automatically replace them with new replicas
* You leverage pod disruptio n  budgets for critical workloads to limit the number of pods of a replicated  application that are down simultaneously from voluntary disruptions
* You have  an ongoing upgrade plan for your clusters in EKS.
* You have  a test environment to test and validate cluster upgrades

### Performance 

* You use limits and requests on all pod definitions to control resource allocation
* You use Horizontal Pod  Autoscaler to use CPU utilization or custom metrics to scale out pods.

## Reference

https://aws.github.io/aws-eks-best-practices/

