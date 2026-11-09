# Network Architecture Diagram

```mermaid
graph TD
    Internet((Internet)) --> Nginx[Reverse Proxy <br/> Nginx]
    Nginx --> WebApp[Sample Web App]
    Nginx --> Monitor[Monitoring]
    WebApp --> DB[(PostgreSQL)]
```