# ⚖️ Catálogo de Regras de Negócio (RN)

Lista de regras imutáveis que garantem a consistência lógica e financeira do sistema.

| ID | Nome da Regra | Descrição Técnica | Tratamento de Erro |
| :--- | :--- | :--- | :--- |
| **RN-001** | **Blindagem de Saldo** | O saldo (`currentXP`) de um membro jamais pode ser menor que zero. | Se uma transação resultar em valor negativo, bloquear a ação no Front e rejeitar no Back (Security Rules). |
| **RN-002** | **Estorno Automático** | Se uma solicitação de compra (`status: PENDING`) for rejeitada (`REJECTED`) ou cancelada, o valor `amount` deve ser somado de volta ao `currentXP` do membro. | Criar transação do tipo `REFUND` para histórico auditável. |
| **RN-003** | **Privacidade Cruzada** | Um membro com role `MEMBER` só pode ler documentos `tasks` onde seu ID esteja no array `assignedTo` OU onde o array contenha `ALL`. | Bloqueio via Firestore Security Rules. |
| **RN-004** | **Unicidade de Convite** | O `inviteCode` não pode ser duplicado em todo o banco de dados. | Verificar existência antes de salvar. Se existir, gerar outro recursivamente. |
| **RN-005** | **Imutabilidade de Histórico** | Registros na coleção `transactions` nunca podem ser editados ou excluídos, apenas criados. | Regra de segurança: `allow update, delete: if false`. |
