# 🗄️ Diagrama de Entidade-Relacionamento (ERD)

Este documento modela a estrutura de dados NoSQL (Firestore) utilizada para garantir a integridade das relações familiares e a separação de perfis.

## Estrutura de Dados
O banco opera em um modelo hierárquico onde a `FAMILY` é a entidade raiz (Tenant), garantindo isolamento de dados entre diferentes núcleos familiares.

```mermaid
erDiagram
    FAMILY ||--|{ MEMBER : "possui"
    FAMILY ||--|{ TASK : "lista"
    FAMILY ||--|{ REWARD : "oferece"
    MEMBER ||--o{ TRANSACTION : "tem histórico"
    MEMBER ||--o{ VOUCHER : "possui"

    FAMILY {
        string id PK
        string ownerId "Admin UID"
        string inviteCode "Ex: WIN-9090"
        string name
    }

    MEMBER {
        string memberId PK
        string familyId FK
        string displayName
        boolean isManaged "True=Criança / False=Adulto"
        string linkedAuthId "UID do Google (ou Null)"
        int currentXP
        string avatar
    }

    TASK {
        string taskId PK
        string title
        int xpReward
        string status "TODO | PENDING | DONE"
        string[] assignedTo "Array de MemberIDs"
        string frequency "DAILY | WEEKLY"
    }

    TRANSACTION {
        string id PK
        string type "EARN | SPEND | REFUND"
        int amount
        timestamp date
    }


    style H fill:#27ae60,color:white
```
