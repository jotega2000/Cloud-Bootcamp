# Week 3 System Design — Study Notes

| Concept | Key takeaway |
|---|---|
| Monolithic architecture | A single deployable application can be simple initially but tightly coupled. |
| Microservices | Independently deployable services introduce distributed-systems complexity. |
| Serverless | AWS manages underlying compute infrastructure; limits and service-specific billing still apply. |
| Three-tier architecture | Presentation, application logic, and data are separated. |
| API Gateway | Manages API endpoints, authorization integrations, throttling, and routing. |
| Load balancer | Distributes requests among healthy targets. |
| Vertical scaling | Increase resources of one server/database instance; upper limits apply. |
| Horizontal scaling | Add instances to distribute load; design for stateless sessions. |
| EBS | Block storage commonly attached to EC2. |
| S3 | Object storage for media, backups, and static assets. |
| EFS | Shared network file storage. |
| Caching | Reduce latency and repeated origin/database work. |
| CDN | Cache content near viewers to reduce delivery latency. |

## Case studies
- **CloudShop:** EC2-based versus serverless e-commerce architecture.
- **CloudStream:** Event-driven video ingest, transcoding, moderation, and CDN delivery.

These notes summarize studied concepts, not lab deployment evidence.
