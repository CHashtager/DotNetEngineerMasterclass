# Fallback

- Fallback mechanisms provide alternative operations or degraded functionality when a component fails or becomes unavailable.
- Examples include returning cached data, default values, or alternative services.

## **Purpose of Fallback Mechanisms**

- **Resilience:** Enhance the system's ability to withstand failures by providing alternatives when primary operations fail.
- **User Experience:** Maintain a usable system and prevent complete service disruption, thereby preserving user trust and satisfaction.

## **Examples of Fallback Mechanisms**

- Returning Cached Data
  - **Scenario:** When a live data source is unavailable, the system can return previously cached data.
  - **Benefits:** This allows users to access stale but still potentially useful data, which is particularly valuable in read-heavy applications where data freshness is not critical for every operation.
- Using Default Values
  - **Scenario:** If a service responsible for providing personalized content fails, the system can fall back to default or generic content.
  - **Benefits:** Ensures that the application continues to provide content, maintaining engagement even though the personalized experience is temporarily unavailable.
- Alternative Services (Secondary Services)
  - **Scenario:** When the primary service is down, requests are routed to a secondary service that can offer a similar functionality.
  - **Benefits:** Keeps the system operational, though the alternative service may offer slower performance or reduced features compared to the primary service.
- Degraded Functionality
  - **Scenario:** In case of failure in non-critical components, the system may disable certain features while keeping the core functionality running.
  - **Benefits:** Focuses resources on maintaining essential services, ensuring that the system remains useful for the majority of tasks.
- Throttling
  - **Scenario:** During peak loads or partial outages, the system may limit the number of requests it handles, prioritizing critical operations.
  - **Benefits:** Prevents system overload and ensures that available resources are allocated to the most important functions.
- Circuit Breaker Pattern
  - **Scenario:** Automatically detecting failures and preventing the application from performing operations that are likely to fail, thereby protecting the system from further damage.
  - **Benefits:** Allows the system to detect patterns of failures and temporarily disable functionality, providing time for recovery and reducing the load on the failing system components.

## **Design Considerations**

- **Timeliness of Cached Data:** Evaluate the acceptability of serving stale data and the impact on user experience.
- **Default Values and User Expectations:** Ensure that default or generic responses are relevant and meaningful to users.
- **Alternative Service Costs:** Consider the costs and limitations of maintaining and switching to secondary services.
- **Monitoring and Alerts:** Implement comprehensive monitoring to detect when fallback mechanisms are triggered, allowing for prompt investigation and remediation.
