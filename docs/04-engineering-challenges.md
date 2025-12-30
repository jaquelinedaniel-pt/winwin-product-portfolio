# 🔧 Desafios de Engenharia & Post-Mortems

> **Contexto:** Documentação de incidentes críticos, análise de causa raiz e soluções implementadas nas versões 2.0 e 2.5.
> **Metodologia:** Análise de Logs, Reprodução de Erro e Refatoração Escalável.

## 1. Incidente: O "Bug de Corrida" (Race Condition)
**Severidade:** Alta (Integridade de Dados / Confiança do Usuário)
* **Sintoma:** Usuários recebiam pontuação negativa injustamente logo após o reset semanal.
* **Causa Raiz:** Conflito de latência entre o Auditor Local (Client-side) e o Timestamp do Servidor (Server-side). O auditor processava a punição milissegundos antes da confirmação de reset do servidor.
* **Solução (Fix):** Implementação de atualização otimista com `new Date()` (Tempo Local) para garantir sincronia imediata entre o status da tarefa e a verificação de auditoria.

## 2. Desafio de Escala: Limite de Lotes (Batch Overflow)
**Severidade:** Média (Bloqueio Operacional)
* **O Problema:** O Firebase impõe um limite rígido de 500 operações por transação (`WriteBatch`). Com o crescimento do histórico de uso, a função de limpeza tentava processar 600+ itens, causando falha silenciosa.
* **Solução Arquitetural:** Implementação de algoritmo de **Chunking (Paginação)**.
    * O sistema agora divide as operações em lotes seguros de 400 itens.
    * Processa e envia (`commit`) sequencialmente, permitindo escalabilidade infinita do histórico sem estourar a memória ou limites da API.

## 3. Feature: Algoritmo "Clean Slate" (Faxina Inteligente)
Para garantir a saúde da performance do app e reduzir a carga cognitiva do usuário, desenvolvemos uma lógica de saneamento de dados:
* **Expurgo (Hard Delete):** Remove permanentemente falhas antigas, clones e solicitações já processadas.
* **Reciclagem (Soft Reset):** Mantém a estrutura das tarefas diárias, resetando apenas os metadados de conclusão para o novo ciclo.
