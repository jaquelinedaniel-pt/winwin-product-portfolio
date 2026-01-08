# 📊 Matriz de Rastreabilidade de Requisitos (RTM)

Esta matriz mapeia os Requisitos Funcionais (RF) e Não-Funcionais (RNF) aos seus respectivos componentes de código e status de validação (QA).

| ID Req. | Descrição Resumida | Componente (Código) | Caso de Teste (QA) | Status |
| :--- | :--- | :--- | :--- | :--- |
| **RF-001** | Cadastro de Família | `authContext.tsx` | Criar nova conta e verificar coleção `families`. | ✅ Aprovado |
| **RF-003** | Perfil Gerenciado (Kids) | `AddMemberModal.js` | Adicionar filho sem email e verificar flag `isManaged`. | ✅ Aprovado |
| **RF-005** | Criação de Tarefas | `CreateTaskForm.js` | Admin cria tarefa e define valor de XP. | ✅ Aprovado |
| **RF-007** | Aprovação de Tarefa | `TaskItem.js` | Fluxo Check -> Approve -> XP Credit. | ✅ Aprovado |
| **RF-009** | Compra na Loja | `ShopScreen.js` | Clicar em comprar e verificar débito imediato. | ✅ Aprovado |
| **RF-010** | Lógica de Estorno | `useEconomy.ts` | Rejeitar compra pendente e verificar retorno do saldo. | ✅ Aprovado |
| **RNF-003** | Design System (Dark) | `tailwind.config.js` | Verificar contraste e cores (Tema Navy/Orange). | ✅ Aprovado |
