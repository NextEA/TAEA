#  Why Microservices?
An in-depth discussion of microservices is beyond scope of this article, but here are some of the benefits that Tailspin hopes to get by moving to a microservices architecture:

*  **Application upgrades**. Services can be deployed independently, so you can take an incremental approach to upgrading an application.
*  **Resiliency and fault isolation**. If a service fails, other services continue to run.
*  **Scalability**. Services can be scaled independently.
*  **Flexibility**. Services are designed around business scenarios, not technology stacks, making it easier to migrate services to new technologies, frameworks, or data stores.
*  **Agile development**. Individual services have less code than a monolithic application, making the code base easier to understand, reason about, and test.
*  **Small, focused teams**. Because the application is broken down into many small services, each service can be built by a small focused team.

#  Why Service Fabric?
Service Fabric is a good fit for a microservices architecture, because most of the features needed in a distributed system are built into Service Fabric, including:

*  **Cluster management**. Service Fabric automatically handles node failover, health monitoring, and other cluster management functions.
*  **Horizontal scaling**. When you add nodes to a Service Fabric cluster, the application automatically scales, as services are distributed across the new nodes.
*  **Service discovery**. Service Fabric provides a discovery service that can resolve the endpoint for a named service.
*  **Stateless and stateful services**. Stateful services use reliable collections, which can take the place of a cache or queue, and can be partitioned.
*  **Application lifecycle management**. Services can be upgraded independently and without application downtime.
*  **Service orchestration** across a cluster of machines.
*  **Higher density** for optimizing resource consumption. A single node can host multiple services.

Service Fabric is used by various Microsoft services, including Azure SQL Database, Cosmos DB, Azure Event Hubs, and others, making it a proven platform for building distributed cloud applications. 

**Reference**: https://docs.microsoft.com/en-us/azure/architecture/service-fabric/migrate-from-cloud-services
