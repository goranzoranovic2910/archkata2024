
### ADR 13: Use Cosine Similarity for Initial Implementation with Flexibility for LLM Matching

- **Title**: Use Cosine Similarity for Initial Implementation with Flexibility for LLM Matching
- **Status**: Accepted
- **Context**:  
  The ClearView system needs to match candidates with job postings based on skills extracted from resumes and job descriptions. There are various approaches to skill matching, with **Cosine Similarity** being one of the most cost-effective and predictable solutions. **Cosine Similarity** allows us to compute the similarity between the candidate's skills and the job posting’s required skills using vectorized representations. While this method is highly efficient and meets the current system requirements, more advanced approaches, such as **LLM-based matching**, could offer enhanced matching capabilities in the future by leveraging the power of natural language models to understand context and skill nuances better.

  To balance cost, performance, and flexibility, we will start with **Cosine Similarity** as the default matching algorithm but design the system in a way that allows us to switch to more advanced matching strategies, such as **LLM-based matching**, as the system evolves.

- **Decision**:  
  ClearView will implement **Cosine Similarity** as the default skill-matching algorithm for the initial version of the system due to its cost-efficiency, predictability, and performance:
  1. **Cosine Similarity** will be used to calculate the similarity between a candidate's skills and the job’s required skills, generating a match score between 0-100%.
  2. The system will be designed with the flexibility to switch to or enhance the matching logic with **LLM-based matching** (e.g., GPT or BERT) when needed. This ensures that the system can evolve and adopt more sophisticated models if required by future use cases or as matching accuracy becomes a higher priority.

  This approach balances the current need for low-cost, high-performance matching while ensuring that the system can adapt to future improvements in matching strategies without requiring major architectural changes.

- **Consequences**:
  - **Positive**:
    - **Cost-Efficiency**: Cosine Similarity is computationally efficient, making it cheaper to run, especially as the system scales. It also has lower infrastructure requirements compared to LLM-based models.
    - **Predictable Performance**: Cosine Similarity provides consistent and predictable performance with minimal tuning, allowing for fast and reliable matching at scale.
    - **System Flexibility**: By designing the system with flexibility for future integration of LLM-based matching, ClearView ensures that it can adopt more advanced matching strategies as the system evolves without having to redesign the matching engine from scratch.
    - **Fast Implementation**: Cosine Similarity is simpler to implement compared to LLM-based models, allowing for faster time to market and reducing the complexity of the initial system.

  - **Negative**:
    - **Limited Contextual Understanding**: Cosine Similarity, while efficient, does not understand the deeper context or relationships between skills and jobs as well as LLMs might. It relies on exact or near-exact matching, which may result in missed opportunities for semantically similar skills (e.g., “software engineer” vs. “developer”).
    - **Switching Costs**: While the system is designed to support future integration of LLMs, switching to an LLM-based model will still involve infrastructure costs, tuning, and retraining, which could introduce technical debt or downtime during the transition.
    - **Not Optimal for All Use Cases**: Cosine Similarity may not perform well in more complex matching scenarios where skills need to be inferred from the context, such as with resumes that describe responsibilities indirectly or use non-standard terminology.
    - **LLM Costs**: If ClearView transitions to LLM-based matching in the future, the costs of running these models (e.g., GPT, BERT) are significantly higher, both in terms of computation and latency, which could impact overall system performance and costs.