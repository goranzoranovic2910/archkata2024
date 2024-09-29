### ADR 04: One REST API with Multiple Endpoints

- **Title**: One REST API with multiple endpoints
- **Status**: Accepted
- **Context**:  
  ClearView’s system spans multiple domains, including candidate management, employer management, job matching, and reporting. Initially, a separate REST API could be designed for each domain to create a clear separation of concerns. However, this introduces overhead in managing multiple services, increasing operational complexity and maintenance. To simplify the architecture and reduce the operational overhead, a decision has been made to consolidate all functionalities into a single REST API with multiple endpoints, where each endpoint handles a specific domain-related function (e.g., candidate, employer, matching, reporting).

- **Decision**:  
  ClearView will use **one REST API** that contains multiple endpoints, each corresponding to a different domain within the system. The REST API will be designed with clear resource paths for:
  1. **Candidate Management Endpoints**: For operations like candidate registration, profile management, resume submission, and skill extraction.
  2. **Employer Management Endpoints**: For managing employer profiles, job postings, and candidate applications.
  3. **Matching Endpoints**: For performing skill matching between candidates and job ads, and returning match scores.
  4. **Administrator Endpoints**: For administrative tasks, such as marking candidates as hired, managing users, and accessing reporting data.
  5. **Reporting Endpoints**: For generating and retrieving reports on system performance, candidate-job matches, and business metrics.

  This approach consolidates domain-specific functionalities into a single API, providing a unified interface for all operations within ClearView.

- **Consequences**:
  - **Positive**:
    - **Simplified Architecture**: Having a single REST API with multiple endpoints reduces the number of API services that need to be developed, deployed, and managed, resulting in simpler DevOps processes.
    - **Reduced Overhead**: Maintaining only one REST API decreases the operational burden, as there are fewer services to monitor, scale, and secure.
    - **Unified Access**: The unified REST API provides a single point of access for all system interactions, which can simplify client-side development (e.g., frontends or external integrations).
    - **Flexibility for Expansion**: New domains or endpoints can be added to the existing API without the need to introduce new services, improving flexibility and adaptability.

  - **Negative**:
    - **API Complexity**: Over time, the single REST API may grow large and complex as more endpoints and functionalities are added, making it harder to maintain clear boundaries between domains. This could lead to challenges in maintaining a clean API structure.
    - **Service Boundaries**: By consolidating all domains into a single API, there’s a risk of blurring domain boundaries, which could introduce unintended dependencies between services that were initially designed to be independent.
    - **Scaling Challenges**: A single API may create performance bottlenecks if it is responsible for too many functionalities. While horizontal scaling can help, it may introduce latency as the API grows.
    - **Reduced Flexibility for Large Teams**: Larger development teams may find it more challenging to work on a shared API codebase without conflicts or delays in deployment.