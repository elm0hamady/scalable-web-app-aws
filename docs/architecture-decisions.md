# Architecture Decisions

## Two Availability Zones
The ALB and application Auto Scaling Group span two Availability Zones to reduce dependence on a single zone.

## Network separation
The ALB is public-facing. EC2 instances and RDS are private and should not receive direct inbound internet traffic.

## Scaling
A Launch Template standardizes EC2 configuration. The Auto Scaling Group maintains desired capacity and can scale using a policy such as target tracking. Scaling behavior must be tested after deployment before being described as verified.

## Database
RDS is placed in private database subnets. Multi-AZ is included in the proposed design when required by the project specification.

## Static content and edge protection
S3 stores static assets and CloudFront caches eligible content. AWS WAF is associated with the CloudFront distribution in this design. Dynamic requests use the ALB origin.

## Cost control
The repository documents the architecture; it does not require deploying every component. Check current regional prices and clean up billable resources after any optional demonstration.
