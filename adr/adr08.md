### ADR 08: Split AI Tips and Matching Services

- **Title**: Split AI tips and matching services
- **Status**: Accepted
- **Context**:  
  ClearView’s system needs to provide two key functionalities: **AI-driven tips** to help candidates improve their resumes and applications, and **skill matching services** to match candidates with job postings based on their skills. Initially, these functionalities could be tightly coupled within the same service. However, to simplify the architecture and improve scalability, the decision has been made to decouple these services, allowing them to operate independently. This separation ensures that the **AI tips service** and the **matching service** can be scaled, maintained, and tested independently, reducing the risk of interference between the two functionalities.

- **Decision**:  
  The **AI tips** service and the **matching service** will be split into two independent services:
  1. **AI Tips Service**: Responsible for generating candidate-specific tips and suggestions based on the content of their resumes and job applications. This service leverages AI models to analyze resumes and provide feedback on how candidates can improve their profiles to better match job descriptions.
  2. **Matching Service**: Responsible for matching candidates to job postings based on their skills and the job requirements. This service uses algorithms like cosine similarity or LLM-based models to match skills between candidates and job ads, returning a match score.

  Decoupling these services ensures that each can evolve independently and allows for better separation of concerns. The AI tips service focuses on candidate improvement, while the matching service focuses on pairing candidates with jobs.

- **Consequences**:
  - **Positive**:
    - **Simplified Scaling**: Each service can be scaled independently based on demand. For instance, the AI tips service may require more resources if candidate interaction increases, while the matching service may need to scale separately based on job postings.
    - **Improved Separation of Concerns**: Decoupling ensures that the functionality of providing AI tips is isolated from the skill-matching logic, improving modularity and separation of concerns.
    - **Easier Maintenance**: Both services can be maintained and updated independently, reducing the risk of changes in one service affecting the other.
    - **Better Testability**: Independent services are easier to test in isolation, improving the reliability and robustness of each service without the overhead of testing interactions between two distinct concerns.

  - **Negative**:
    - **Increased Complexity in Integration**: Splitting the services introduces the need for careful orchestration and communication between them. For example, if AI tips are ever to be used in conjunction with matching logic, the integration could become complex.
    - **Dependency Management**: If the services need to interact in the future (e.g., using AI tips to influence matching), managing dependencies between the two services will require additional coordination, which could introduce challenges in terms of latency and performance.
    - **Service Orchestration Overhead**: Running two separate services requires careful orchestration to ensure they operate seamlessly, potentially increasing operational overhead in terms of monitoring, scaling, and error handling.