### ADR 10: Configurable Top N Candidates for Employers

- **Title**: Configurable top N candidates for employers
- **Status**: Accepted
- **Context**:  
  ClearView’s system matches candidates to job postings based on skills and other criteria. When employers review the results of the matching process, they need to see a manageable number of top candidates rather than an overwhelming list of all applicants. By making the number of top candidates (`N`) configurable, employers can decide how many candidates they want to review per job posting. This approach ensures flexibility, reduces the load on the database by avoiding the need to retrieve and store large result sets, and helps maintain system scalability.

- **Decision**:  
  ClearView will allow employers to configure the number of top candidates (`N`) they wish to see for each job posting. This "N" will be:
  1. **Configurable Per Job Posting**: Employers will be able to set the number of candidates they want to review for each job posting, ensuring flexibility for different types of job listings.
  2. **Scalable Matching Results**: The system will retrieve and store only the top N candidates for each job ad, reducing the amount of data stored in the database and improving performance.
  3. **Defaults and Limits**: There will be default values for "N" (e.g., top 10 candidates) and reasonable upper limits to prevent performance degradation if too many candidates are requested.

  This configurable approach provides scalability while keeping the system flexible enough to meet the varying needs of employers.

- **Consequences**:
  - **Positive**:
    - **Scalability**: Limiting the number of candidates returned for each job posting helps ensure that the system remains scalable, reducing the load on the database and improving performance by avoiding the retrieval of large candidate lists.
    - **Employer Flexibility**: Allowing "N" to be configurable per job posting provides flexibility for employers. For more specialized or high-importance jobs, they can request a larger pool of candidates, while for others, they may only want to see a small number of top matches.
    - **Performance Optimization**: By only fetching the top N candidates, the system optimizes performance, reducing the volume of data transferred and processed during the matching process.
    - **Database Efficiency**: By storing only the top N candidates in the database, the overall data footprint is reduced, improving database efficiency and lowering the risk of database overload during high-load periods.

  - **Negative**:
    - **Complexity in Configuring "N"**: Dynamically configuring the number of candidates per job posting introduces some complexity in how this is managed across different employers and jobs. This configuration must be implemented in a way that is intuitive and easy for employers to use.
    - **Risk of Misconfiguration**: If "N" is set too high or too low for specific job listings, it could lead to employer dissatisfaction. For instance, setting "N" too low may cause employers to miss out on potential matches, while setting it too high may overwhelm them with too many candidates.
    - **Need for Guardrails**: Limits will need to be set on the maximum value of "N" to ensure system performance is not degraded by an excessive number of candidates being requested for a single job posting.
    - **Inconsistent Experience**: Employers may have inconsistent experiences if "N" is configured differently for similar job types, leading to variability in the quality and number of candidates reviewed.
