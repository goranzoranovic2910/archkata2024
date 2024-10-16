Detailed Domain Model of the system.

``` mermaid
classDiagram
    %% Customer Group
    class Candidate
    class Resume
    class Tip
    class Job

    %% Candidate and Company Group
    class Skill

    %% Company Group
    class Company
    class Matching

    %% Administration Group
    class Payment

    %% Reporting Group
    class BusinessReport
    class ServiceReport

    %% Surveys Group
    class Survey

    %% Relationships
    Candidate "1" -- "0..1" Resume : has
    Resume "1" -- "*" Tip : has
    
    
    Candidate "1" -- "*" Skill : possesses
    
    Company "1" -- "*" Job : posts
    Job "1" -- "*" Skill : requires
    Company "1" -- "*" Matching : uses
    Candidate "1" -- "*" Matching : participates in
    Job "1" -- "*" Matching : involved in
    Company "1" -- "*" Payment : makes
    Payment "1" -- "1" Resume : unlocks
    BusinessReport "1" -- "*" Company : analyzes
    ServiceReport "1" -- "*" Candidate : analyzes
    ServiceReport "1" -- "*" Company : analyzes
    Survey "1" -- "*" Candidate : taken by
    Survey "1" -- "*" Company : conducted by
```
