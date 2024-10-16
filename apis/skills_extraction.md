[Back](/README.md)

# Skills extraction

Example :
``` json
{ 
    "Java": "Expert", 
    "SQL": "Intermediate", 
}
```

``` mermaid
graph TD
    C[Matching Endpoint]
    B[AI Skill Matching]
    D[(ClearView Matching Schema)]
    C --> |invoke| A
    C --> |invoke| B
    B --> D
    C --> D
    subgraph Matching Service
        C
        B
        subgraph A[Skill Extraction]
            E[Resume/Ad Processing]
            F[Skill Identification]
            E --> F
        end
        A --> D
    end
    H[AI Services]
    I[(Resume/Ads File Storage)]
    E --> |read| I
    F --> |request| H
    H --> |response| F
```

Class diagram

``` mermaid
classDiagram
    %% Skill Extraction Component
    class SkillExtractor {
        +extractSkills(documentId: string) CategorizedSkills
    }

    class ResumeAdProcessor {
        +processDocument(documentId: string) ProcessedDocument
    }

    class SkillIdentifier {
        +identifySkills(processedDocument: ProcessedDocument) IdentifiedSkills
    }

    %% External Services
    class AIService {
        +extractSkills(text: string) Promise~ExtractedSkills~
    }

    class FileStorage {
        +getDocument(documentId: string) RawDocument
    }

    %% Relationships (vertical flow)
    SkillExtractor --> ResumeAdProcessor : uses
    ResumeAdProcessor --> FileStorage : uses
    SkillExtractor --> SkillIdentifier : uses
    SkillIdentifier --> AIService : uses
```