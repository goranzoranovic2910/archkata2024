### ADR 07: Split AI Tips, Anonymization, and Matching Services

- **Title**: Split AI tips, Anonymization, and Matching services
- **Status**: Accepted
- **Context**:  
  ClearView’s system provides several key functionalities: **AI-driven tips** to help candidates improve their resumes and applications, **anonymization** to remove bias from resumes, and **skill matching services** to match candidates with job postings based on their skills. Initially, these functionalities could be tightly coupled within the same service. However, to simplify the architecture and improve scalability, the decision has been made to decouple these services, allowing them to operate independently. This separation ensures that the **AI tips service**, **anonymization service**, and the **matching service** can be scaled, maintained, and tested independently, reducing the risk of interference between these functionalities.

- **Decision**:  
  The **AI tips**, **anonymization**, and **matching services** will be split into three independent services:
  1. **AI Tips Service**: Responsible for generating candidate-specific tips and suggestions based on the content of their resumes and job applications. This service leverages AI models to analyze resumes and provide feedback on how candidates can improve their profiles to better match job descriptions.
  2. **Anonymization Service**: Responsible for removing personal and bias-inducing details from candidate resumes, using LLMs to intelligently anonymize the data while maintaining a compelling, coherent presentation. This service ensures that employers receive only anonymized resumes.
  3. **Matching Service**: Responsible for matching candidates to job postings based on their skills and the job requirements. This service uses algorithms like cosine similarity or LLM-based models to match skills between candidates and job ads, returning a match score.

  Decoupling these services ensures that each can evolve independently and allows for better separation of concerns. The AI tips service focuses on candidate improvement, the anonymization service ensures bias-free resumes, and the matching service focuses on pairing candidates with jobs.

- **Consequences**:
  - **Positive**:
    - **Simplified Scaling**: Each service can be scaled independently based on demand. For instance, the AI tips service may require more resources if candidate interaction increases, while the anonymization service may scale based on resume submissions.
    - **Improved Separation of Concerns**: Decoupling ensures that the functionality of providing AI tips, anonymizing resumes, and skill matching are isolated from each other, improving modularity and separation of concerns.
    - **Easier Maintenance**: Each service can be maintained and updated independently, reducing the risk of changes in one service affecting the other services.
    - **Better Testability**: Independent services are easier to test in isolation, improving the reliability and robustness of each service without the overhead of testing interactions between multiple concerns.

  - **Negative**:
    - **Increased Complexity in Integration**: Splitting the services introduces the need for careful orchestration and communication between them. For example, if AI tips, anonymization, and matching logic need to interact, the integration could become complex.
    - **Dependency Management**: Managing dependencies between the services (e.g., anonymization feeding into matching) will require additional coordination, which could introduce latency and performance challenges.
    - **Service Orchestration Overhead**: Running three separate services requires careful orchestration to ensure they operate seamlessly, potentially increasing operational overhead in terms of monitoring, scaling, and error handling.
