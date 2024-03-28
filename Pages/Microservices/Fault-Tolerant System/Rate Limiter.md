# Rate Limiter

- Rate limiting controls the flow of requests to prevent overwhelming components and causing failures due to overload.
- It can be implemented at various levels (e.g., API gateway, service level) based on requirements.
  - **API Gateway Level**: Many modern architectures use an API gateway as the entry point for all incoming requests to backend services. Implementing rate limiting at this level allows for centralized control and is effective in protecting backend services from getting overwhelmed.
  - **Service Level**: In microservices architectures, rate limiting can also be applied at the individual service level, providing fine-grained control over the load each service can handle. This is useful for services with varying performance characteristics or importance.
  - **Application Level**: Within an application, rate limiting can be applied to specific functionalities or endpoints, protecting critical sections of an application from being overloaded.
  - **Network Level**: Rate limiting can be enforced by network devices (e.g., routers, firewalls) to control the flow of traffic entering or leaving a network segment.

## **Strategies for Rate Limiting**

- **Fixed Window**: Limits the number of requests in a fixed time window (e.g., 1000 requests per hour). This is simple to implement but can allow bursts of traffic at the boundary of time windows.
- **Sliding Log**: Records timestamps of each request and dynamically adjusts the rate limit based on the request pattern over time. It's more complex but prevents bursts at the edges of time windows.
- **Token Bucket**: Allows a certain number of requests in a given time frame, replenishing "tokens" at a steady rate. This method smooths out bursts over time.
- **Leaky Bucket**: Similar to the token bucket but enforces a more steady output rate, smoothing out incoming bursts of requests by queueing them.

## **Considerations**

- **Graceful Handling of Limit Exceeding**: When a request exceeds the rate limit, it's crucial to handle it gracefully, typically by responding with a **`429 Too Many Requests`** HTTP status code and possibly including retry information.
- **Configurability**: Rate limits should be configurable to adjust to changing requirements without code changes.
- **Distributed Systems**: In distributed architectures, ensuring consistent rate limiting across multiple instances or nodes can be challenging. Solutions like distributed caching or centralized rate limiting services can help.
- **Monitoring and Alerting**: It's essential to monitor rate-limited endpoints or services and alert administrators if the limits are hit too frequently, as it may indicate issues with the service capacity or an attack.
