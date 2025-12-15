# ☁️ AWS - Amazon Web Services

## 🎯 Services Essentiels DevOps

### Compute
- **EC2** : Serveurs virtuels
- **Lambda** : Serverless functions
- **ECS/EKS** : Container orchestration

### Storage
- **S3** : Object storage
- **EBS** : Block storage (disques EC2)
- **EFS** : File storage partagé

### Database
- **RDS** : Bases relationnelles managées
- **DynamoDB** : NoSQL managé
- **ElastiCache** : Redis/Memcached

### Networking
- **VPC** : Réseau privé virtuel  
- **Route 53** : DNS
- **CloudFront** : CDN
- **ELB** : Load Balancing

### DevOps Tools
- **CodePipeline** : CI/CD
- **CodeBuild** : Build service
- **CodeDeploy** : Déploiement automatisé
- **CloudFormation** : Infrastructure as Code

### Monitoring
- **CloudWatch** : Logs + Métriques
- **X-Ray** : Distributed tracing

---

## 📚 Parcours 3 Semaines

### Semaine 1 : Fondamentaux
- [01: Compte AWS + IAM](./exercices/01-compte-iam)
- [02: EC2 Basics](./exercices/02-ec2)
- [03: S3 Storage](./exercices/03-s3)
- [04: VPC Networking](./exercices/04-vpc)

### Semaine 2 : Services Avancés
- [05: RDS Database](./exercices/05-rds)
- [06: Load Balancer](./exercices/06-elb)
- [07: Auto Scaling](./exercices/07-autoscaling)
- [08: CloudFormation](./exercices/08-cloudformation)

### Semaine 3 : Production
- [09: CI/CD avec CodePipeline](./exercices/09-cicd)
- [10: Monitoring CloudWatch](./exercices/10-cloudwatch)
- [11: Lambda Serverless](./exercices/11-lambda)
- [Projet: App 3-Tiers](./projet-final)

---

## 🛠️ AWS CLI Commandes Essentielles

```bash
# Configuration
aws configure

# EC2
aws ec2 describe-instances
aws ec2 run-instances --image-id ami-xxx --instance-type t2.micro

# S3
aws s3 ls
aws s3 cp file.txt s3://mon-bucket/
aws s3 sync ./local s3://mon-bucket/

# IAM
aws iam list-users
aws iam create-user --user-name devops-user

# CloudFormation
aws cloudformation create-stack --stack-name mystack --template-body file://template.yaml
aws cloudformation describe-stacks
```

---

## 🎓 Certification AWS Solutions Architect Associate

**Préparation post-semaine 3**  
**Coût :** $150  
[Plus d'infos](https://aws.amazon.com/certification/certified-solutions-architect-associate/)

---

**Voir aussi :** [Azure](../AZURE/README.md) | [GCP](../GCP/README.md)
