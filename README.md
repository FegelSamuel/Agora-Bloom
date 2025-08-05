# Agora-Bloom
## Workflow diagram
It can be assumed that every rounded (or every node at the bottom) runs on an Amazon EC2 instance.
```mermaid
flowchart TD;
  F(Forum)
  O[Some third-party LLM API] --> H(General Purpose Helpdesk)
  A[AWS S3 Bucket] --> F
  D[Database] --> F
  N[In-House Neural Network] --> R(Plant Recommendation System)
  S[Data Sets] --> N
```

## Tech Stack Dependency Chart
```mermaid
flowchart LR;
  R(React)
  P(Prisma ORM)
  S(SQLite3 or Postgres)
  N(Next.js Server)
  F(Forum)
  C(Plant Recommendation System)
  G(AI-Powered Helpdesk)

  N --> F
  N --> C
  R --> G
  R --> F
  R --> C
  N --> R
  P --> N
  S --> P
```

## EER Diagram
v1.0.0
```mermaid
erDiagram
    User ||--o{ Post : writes
    User ||--o{ Comment : writes
    User ||--o{ ForumSubscription : subscribes_to
    User ||--o{ ForumMod : moderates
    User ||--o{ Forum : creates
    Forum ||--o{ ForumSubscription : has
    Forum ||--o{ ForumMod : has
    Forum ||--o{ Post : contains
    Post ||--o{ Comment : has

    User {
        string id PK
        string email
        string firstName
        string lastName
        string profilePicture
        enum   role
    }

    Forum {
        string id PK
        string ownerID
        string title
    }

    ForumMod {
        string id PK
        string userID
        string forumID
    }

    ForumSubscription {
        string id PK
        string userID
        string forumID
    }

    Post {
        string id PK
        string userID
        string forumID
        string title
        string media
        string text
    }

    Comment {
        string id PK
        string userID
        string postID
        string media
    }
```
