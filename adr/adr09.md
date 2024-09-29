### ADR 09: Matching Once per Job Ad Deadline

- **Title**: Matching once per Job Ad deadline
- **Status**: Accepted
- **Context**:  
  ClearView’s system is designed to match candidates with job ads based on skills and other criteria. Initially, a real-time matching approach could be used, where candidate-job matching is continuously updated as new candidates apply or job ads are modified. However, real-time matching introduces significant overhead in terms of processing power, costs, and system complexity. Employers typically review candidates only at the end of a job posting’s lifecycle, making real-time matching less critical. To simplify the matching process and reduce operational costs, the decision has been made to perform matching **once per Job Ad deadline**, aligning with employer expectations.

- **Decision**:  
  ClearView will perform **candidate-job matching once per job ad deadline**, meaning the system will process and generate candidate matches only when a job ad closes or reaches its deadline. The steps involved include:
  1. **Candidate Application Collection**: Candidates apply throughout the job ad's lifecycle.
  2. **Batch Matching at Deadline**: Once the job ad reaches its deadline, the system will process all applications and generate matches, ranking candidates based on skill matching algorithms.
  3. **Employer Review**: Employers will receive the best-matched candidates in a batch, rather than in real-time as applications come in.

  This decision significantly reduces the need for continuous processing and ensures that resources are only used when needed, thereby optimizing cost and system efficiency.

- **Consequences**:
  - **Positive**:
    - **Reduced Processing Costs**: By performing matching only once per job ad deadline, the system dramatically reduces processing overhead. Resources are used efficiently, only when required, leading to lower operational costs.
    - **Simplified Pipelines**: The matching pipeline becomes simpler, as it no longer requires real-time or continuous updates. Processing happens in batch mode at predictable intervals (when job ads reach their deadline).
    - **Alignment with Employer Behavior**: Employers typically review candidates at the end of a job ad's lifecycle, so this approach aligns with their expectations, providing them with a list of matched candidates in one go.
    - **Optional On-Demand Matching**: If real-time feedback or matching is needed, the **Matching API** can be invoked on-demand, providing flexibility for certain employers or job ads that require immediate results.

  - **Negative**:
    - **Delayed Feedback for Candidates**: Candidates applying early in the job ad's lifecycle may have to wait until the job ad closes before receiving feedback on their application status, which could impact candidate experience.
    - **Less Responsive to Job and Candidate Availability**: The system becomes less responsive to changes in candidate availability (e.g., candidates withdrawing applications) or job ad modifications (e.g., employers updating job requirements mid-cycle). These changes won’t be reflected until the next matching run at the job ad deadline.
    - **Potential for Overload at Deadline**: If a large number of job ads reach their deadline simultaneously, there could be a surge in processing load. This will require monitoring and scaling infrastructure to ensure deadlines are handled efficiently.
    - **Decreased Real-Time Adaptability**: While the system is more cost-effective, it sacrifices the ability to continuously adapt to new candidates or changes in job ads in real-time.