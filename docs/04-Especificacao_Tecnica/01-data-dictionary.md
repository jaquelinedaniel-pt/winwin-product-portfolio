# 📚 Dicionário de Dados (Data Dictionary)

Especificação técnica dos campos para garantir integridade no Firestore (NoSQL).

## 1. Collection: FAMILIES (`families`)
[cite_start]Entidade raiz que agrupa os membros e configurações do núcleo familiar[cite: 5].

| Campo | Tipo | Obrigatório | Descrição | Regra de Validação |
| :--- | :--- | :--- | :--- | :--- |
| **id** | String (UUID) | Sim | Identificador único da família. | Gerado pelo Firebase. |
| **ownerId** | String | Sim | UID do Pai/Mãe criador. | Deve existir em `auth`. |
| **familyName** | String | Sim | Nome de exibição. | Máx. 30 caracteres. |
| **inviteCode** | String | Não | Código para convite. | [cite_start]6 chars, Uppercase, Único[cite: 6]. |
| **createdAt** | Timestamp | Sim | Data de criação. | Server Timestamp. |

## 2. Sub-collection: MEMBERS (`families/{id}/members`)
[cite_start]Perfis individuais vinculados a uma família[cite: 7].

| Campo | Tipo | Obrigatório | Descrição | Regra de Validação |
| :--- | :--- | :--- | :--- | :--- |
| **displayName** | String | Sim | Nome do filho/pai. | Máx. 20 chars. |
| **role** | Enum | Sim | Papel no sistema. | [cite_start]`ADMIN` ou `MEMBER`[cite: 8]. |
| **isManaged** | Boolean | Sim | Se é perfil infantil (sem login). | `true` ou `false`. |
| **currentXP** | Number | Sim | Saldo atual de experiência. | Min: 0 (Não pode ser negativo). |
| **linkedAuthId** | String | Não | Vínculo com login externo. | Apenas se `isManaged = false`. |

## 3. Sub-collection: TASKS (`families/{id}/tasks`)
[cite_start]Unidade de trabalho atribuída aos membros[cite: 9].

| Campo | Tipo | Obrigatório | Descrição | Regra de Validação |
| :--- | :--- | :--- | :--- | :--- |
| **title** | String | Sim | O que deve ser feito. | Min 3 chars, Máx 50. |
| **xpReward** | Integer | Sim | Valor da recompensa. | Min: 1, Máx: 1000. |
| **status** | Enum | Sim | Estado atual do ciclo. | [cite_start]`TODO`, `PENDING`, `DONE`[cite: 10]. |
| **recurrence** | Array | Não | Dias da semana ativos. | Ex: `['MON', 'FRI']`. |
| **assignedTo** | Array | Sim | IDs dos responsáveis. | Não pode ser vazio. |
