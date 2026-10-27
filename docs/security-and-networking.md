# Security and Networking

## Intended security-group relationships

| Source | Destination | Allowed traffic |
|---|---|---|
| Intended web entry path | ALB security group | HTTP/HTTPS as configured |
| ALB security group | EC2 security group | Application listener port only |
| EC2 security group | RDS security group | Database port only |

## Routing
- Public subnets: VPC-local route plus default route to the Internet Gateway.
- Private application subnets: VPC-local route and a NAT route only if outbound internet access is needed.
- Database subnets: no direct route to an Internet Gateway.
- NAT Gateways allow outbound connections initiated from private subnets; they do not provide unsolicited inbound access.

## Administration
Use an EC2 IAM instance profile with least privilege. Configure Systems Manager connectivity and use Session Manager rather than opening SSH to the internet.

## Secrets
Never commit AWS access keys, credentials, private keys, `.env` files, or account-specific secrets.

These are design intentions, not evidence that the resources have been deployed or validated.
