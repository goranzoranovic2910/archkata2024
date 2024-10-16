### ADR 05: Split Database by Schema to Decouple Domains and Improve Security

- **Title**: Split database by schema to decouple domains and improve security
- **Status**: Accepted
- **Context**:  
  ClearView’s system handles sensitive and domain-specific data, including candidate profiles, employer job postings, matching results, and analytics. By default, all of this data would be stored in a single relational database. To enhance both fault-tolerance and security, and to ensure clear separation of concerns, a decision has been made to split the database into **multiple schemas**. Each schema will be responsible for managing data specific to one domain, ensuring that candidate, employer, matching, and analytics data are isolated from each other. This schema separation will also improve security, as different access controls can be applied to each schema.

- **Decision**:  
  ClearView’s relational database will be divided into distinct **schemas**, each handling data specific to a domain:
  1. **Candidate Schema**: Manages candidate profiles, resumes, and skill extractions. This schema will have access controls to protect candidate data.
  2. **Employer Schema**: Stores employer profiles, job postings, and related data.
  3. **Matching Schema**: Contains job-candidate matching results, including the data generated from skill matching algorithms.
  4. **Analytics Schema**: Stores aggregated and historical data used for reporting and analytics purposes.

  By separating data into these schemas, we improve the system's overall security and fault tolerance, making it easier to manage access and maintain data integrity across the system.

- **Consequences**:
  - **Positive**:
    - **Improved Security**: By separating data into different schemas, we can apply fine-grained access controls, ensuring that only authorized services and users can access sensitive data in each domain. For example, candidate data will be isolated from employer data, reducing the risk of unauthorized access.
    - **Enhanced Fault-Tolerance**: Decoupling data into domain-specific schemas ensures that failures or issues in one domain (e.g., the matching service) do not affect other domains (e.g., candidate or employer data). This helps maintain system reliability and fault-tolerance.
    - **Data Isolation**: Each schema is responsible for managing a specific domain’s data, reducing the risk of accidental data overlap or interference between domains. This simplifies auditing and ensures better data integrity.
    - **Clear Separation of Concerns**: Separating data by schema aligns with domain-driven design principles, allowing each domain’s data model to evolve independently, with fewer cross-domain dependencies.

  - **Negative**:
    - **Increased Complexity**: Managing multiple schemas introduces additional complexity, particularly in handling database optimizations and managing queries that span multiple schemas. Schema-specific optimizations will need to be carefully designed to ensure performance is maintained.
    - **Cross-Schema Queries**: Inter-schema queries, such as those required to join data between the candidate and matching schemas, can be more complex and may impact performance. Special care must be taken to optimize these cross-schema interactions.
    - **Operational Overhead**: Schema management will require more sophisticated tooling and processes, including database migrations, backups, and monitoring. Ensuring consistency and security across schemas adds operational overhead.
    - **Maintenance Complexity**: Over time, managing separate schemas may lead to increased administrative burden, especially when dealing with schema evolution, versioning, and updates.
