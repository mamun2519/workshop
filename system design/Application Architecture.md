## Application Architecture

- Monolithic
- 2-Tier
- N-Tier
- Modular Monolith
- MicroServices
- Event Driven
- Cloud-native
- ServerLess ETC

### 1. Monolithic

- user Interface
- Business logic
- Data interface
- Database

### Key Characteristics

- Single Codebase
- Centralized deployment
- shared database
- tight coupling

## Application Scalability

**Scaling is system design**

⇒ scaling in system design refers to the ability of a system to handle increased load or demand while maintaining or improving its performance.

**Performance vs scaling**

**performance**

- Low latency
- high throughput
  - concurrency
  - capacity
- capacity

**Scalability**

- subset of performance
- High throughput
- scale both up and down

### There are two types of scaling

- Vertical
- Horizontal

**Vertical Scaling**

⇒ vertical scaling also known as scaling up or scaling vertically refer to the process of increasing the capacity of a single server or recourse in order to handle a large load or improve performance.

**example ⇒ server starts 2 core 4GB then increases 16 core 64 GB**

**How do we achieve vertical scaling?**

- add more CPU
- add more memory
- increase storage capacity
- upgrade to a more powerful server

**Cons /problem of vertical scaling**

- Limited Scalability
- Downtime for upgrades
- Higher cost for high-performance needs
- single point of failure

**When to use vertical scaling**

- vertical scaling is suitable when the workload is well-suited to a single powerful machine.
- its viable option for applications with predicated resource needs.
- in secaneraios where simplicity and upgrades of are crucial.

**Horizontal Scaling**
Horizontal Scaling also known as scaling out, involves adding more machines or nodes to a system to distribute the load and increase its overall capacity.

**Cons /problem of Horizontal scaling**

- Improved Scalability
- Cost effective
- redundancy and fault tolerance
- Easy to add capacity

**How To achieve Horizontal Scaling**

- Load balancing
- clustering
- containerization
- auto-scaling

**Issue with This Architecture**

- Two Different Ip Addresses
- Two Different Databases
- Two Different Storages
- How client will decided which route to go?

**Cons /problem of Horizontal Scaling**

- complexity
- inter-Node commination
- Data Consistency

**Scalability Principles**

- Decentralization
- Independence

**Decentralization**

⇒ One component is responsible for all the work. if one component is responsible for all the work it is called monolithic. Monolithic is an anti-pattern for scalability.

**Key Aspects of decentralization**

- Distribution of components
- Data distribution
- load Distribution

**Advantages of decentralization**

- Improved Scalability
- Fault Tolerance
- Flexibility

**Key Aspects of Independence**

- Loose Coupling
- Isolation of concerns
- Services Oriented Architure

**Advantages of independence**

- Easier Maintenance
- Scalability
- Parallel Development

**Scalability Architecture Starts with Module**

### Load Balancer

⇒ a load balancer is a device or software application that distributes incoming network traffic across multiple services or resources.

**Key Functions of Load Balancers**
