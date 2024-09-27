# Clear View Solution
 


## Equi Hire Architects Team

- Uros Milivojevic
- Marjan Slavkovski
- Rastko Djordjevic
- Goran Zoranovic

## Table of contents

TODO:

## Company overview (optional)

Diversity Cyber Council (https://www.diversitycybercouncil.com/) is a 501c3 Non-Profit that serves under-represented demographics in the tech industry by facilitating education, training, and staffing opportunities to establish a sustainable and diverse talent pipeline to the workforce.

## Requirements (link to the problem description and requirements we figured out in communication and discussions)

High level requirements are listed in these documents:
- https://docs.google.com/document/d/1jCHMAvgzqaYaAp09br12OC4ozpVXZR3s9ezgEqncZ9U/edit#heading=h.jsoimuz95gvo

Additionally, through communication with stakeholders we found few other requirements:

- Cost is important aspect and we should aim to reduce it.
- Big volumes of users are not expected so scalability is not very important.
- There is a possibility of potential adding new AI features in the future, but it is not hard requirement.
- System will be maintained by current Diversity Cyber Council IT team

## Assumptions
## Identifying architecture characteristics 

Taking into account all requirements we decided that 3 main characteristics for our solution should be: **Cost, Interoperability and Simplicity.**

Besides these we consider *Fault-tolerance, Evolvabilty, Scalability, Testability, Workflow and Abstraction.*

*Reliablity* is also important as one of composite characteristis.


<img src="worksheets/architecture_characteristis.png">

After careful consideration, we have decided that Service-Based architecture is one that best fits our requirements.

There were other styles which could be also good options like microkernel, microservices or event-driven, however, cost and simplicity were the main characteristics which made the difference.

<img src="worksheets/architecture_styles.png">


|ADR # |	Title |	Why |	Trade-offs |
|------|----------|-----|--------------|	
|01 |	Chosen architecture characteristics: cost, interoperability, simplicity, fault-tolerance, and evolvability |	Prioritized cost, interoperability, simplicity, fault-tolerance, and evolvability based on problem statement.| 	May require trade-offs between simplicity and evolvability over time, potentially limiting flexibility as requirements grow. |	
|02 |	Service-Based Architecture selected	|Service-based architecture chosen to align with prioritized characteristics (cost, fault-tolerance, scalability).| 	Increased complexity in service orchestration and operational overhead compared to a monolithic approach. This level of complexity is needed to allow enough evolvability of system. Reduced scalability compared to microservices of event-driven architecture to optimize more for cost and expected scale.|	


## Domain analysis (ER diagram and schema partitioning and ADRs listed)
## Architecture
### Top level architecture 

<img src="diagrams/full_architecture.png">

- ClearView Frontend - top layer using REST APIs which are hiding complexity of the system below.

- ClearView REST API - Top level abstraction to be used for integration with HR apps. Clear view can have its own front end hooking up to this layer.

- Candidate Endpoint - REST API component covering methods needed for Candidate flow.

- Employer Endpoint - REST API component covering methods for Employer flow.

- Administrator Endpoint - REST API component covering methods for Admin flow.

- Reporting Endpoint - REST API component covering methods needed for Monthly reporting.

- AI Tips Service - Service providing tips for the Candidate resume.

- Matching Service - Service making actual matches based on skills extracted from job ads and resumes.

- Resume/Ads File Storage - Storage used for 
files.

- ClearView database - Relational database for rest of the data.

- External services (Payment processor and Survey Provider)


#### Architecture Decision Records

Here is the list of all ADRs we made during the process to came up with architecture we designed. Full ADRs can be found through links in the table.


|ADR #| 	Title| 	Why |	Trade-offs 	|
|------|----------|-----|--------------|	
|01 |	Chosen architecture characteristics: cost, interoperability, simplicity, fault-tolerance, and evolvability |	Prioritized cost, interoperability, simplicity, fault-tolerance, and evolvability based on problem statement.| 	May require trade-offs between simplicity and evolvability over time, potentially limiting flexibility as requirements grow. |	
|02 |	Service-Based Architecture selected	|Service-based architecture chosen to align with prioritized characteristics (cost, fault-tolerance, scalability).| 	Increased complexity in service orchestration and operational overhead compared to a monolithic approach. This level of complexity is needed to allow enough evolvability of system.Reduced scalability compared to microservices of event-driven architecture to optimize more for cost and expected scale.|		
|03 |	One REST API with multiple endpoints |	Simplifies architecture by having a single API with various endpoints for different functionalities. |	Can lead to large, complex APIs over time, making it harder to maintain clear boundaries between services.Reducing number of REST API services to one instead of multiple (one for each domain).	|
|04 |	One relational database and one file-storage DB |	Simplifies maintenance by reducing the number of databases, combining multiple domains into one relational DB.| Resumes need separate file storage.	May compromise modularity and separation of concerns between domains, leading to potential scaling or data management challenges later. However big scalability is not expected so we feel comfortable in making this decision.	|
|05 |	Organize components per domain| 	Organizes ClearView components into domain-specific groups (candidate, employer, matching, etc.) to separate concerns effectively and improve maintainability and testability.|	Requires managing inter-domain communication and potentially increasing complexity if domains grow interdependent. 	|
|06 |	Split database by schema to decouple domains and improve security|	Improves fault-tolerance and security by separating candidate, employer, matching, and analytics data into schemas. |	More complex database management, requiring careful handling of schema-specific optimizations and inter-schema queries. |	
|07 |	Analytics as part of regular database| 	Simplifies architecture by embedding analytics within the regular database, avoiding real-time analytics complexity. |	May limit future analytics capabilities if real-time or advanced analytics are needed, and could add extra load to the operational database. However, it should be fairly easy to move this data to separate database if needed.|	
|08 |	Split AI tips and matching services |	Decouples AI tips and matching services, making the system simpler and easier to scale independently.  |	Requires coordination between services and careful orchestration of dependencies if they need to interact, adding complexity in integration. On the other hand we improve separation of concerns, maintaining and testability.|	
|09 	|Matching once per Job Ad deadline 	|Matches candidates once per job ad deadline, aligning with employer expectations and simplifying processing pipelines. |	Delays real-time candidate matching and feedback loops, making the system less responsive to changes in candidate or job availability during the job lifecycle. However, it dramatically reduces costs of processing. If needed, processing can be invoked through Matching API on demand.	|
|10 |	Configurable top N candidates for employers |	Allows employers to see the top N candidates, making "N" configurable, ensuring scalability and reducing DB overload. 	|Complexity in configuring "N" dynamically across jobs; potential risk if "N" is set too high or too low for specific job listings, affecting employer satisfaction.|
|11 |	Use lightweight authentication (OAuth2, Shiro) |	Implements simple and lightweight authentication to reduce complexity while securing access to services. |	May require upgrades to a more robust solution if security or user management needs increase, adding migration overhead later. 	|


### Candidate Endpoint
### Employer Endpoint
### Administrator Endpoint
### AI Tips service
### Matching service
### Database
### ER diagram
### Schema considerations
### File Storage
### External services
### Payment processor
ADR and decision
### Survey
ADR and decision
### Additional considerations
#### Evolvability
#### Scalability
#### Business model (Premium)
....
### Appendix (additional materials, investigated options etc.)

