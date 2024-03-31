# Scalability
As the system grows the performance starts to degrade unless we adapt it to deal with that growth.
Scalability is the property of a system to handle a growing amount of load by adding resources to the system.
## How can a system Grow?
1. **User Base**: More users started using the system, leading to increased number of requests.
2. **Features**: Introducing new functionality to expand the system
3. **Data Volume**: Growth in the amount of data the system stores and manages.
4. **Complexity**: The system's architecture evolves to accommodate new features, scale, or integrations, resulting in additional components and dependencies.
5. **Geographic Reach**: Serve users in new regions or countries.
## How to Scale a system?
1. **Vertical Scaling (Scale up)**: Add power resource, increase ram, cpu.
2. **Horizontal Scaling (Scale out)**: Add more machines to spread the workload.
3. **Load Balancing**: Distribute traffic
4. **Caching**: Store frequently accessed data in-memory (RAM)
5. **Microservices Architecture**: Independent services that can be scaled independently.
6. Other ways: CDN, Partitioning, Asynchronous communication, Auto-Scaling, Multi-region Deployment. 