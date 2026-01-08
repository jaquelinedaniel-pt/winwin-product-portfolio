# 🎯 Estratégia de Priorização (Metodologia MoSCoW)

Este documento detalha a matriz de prioridades utilizada para definir o escopo do MVP V3.0, garantindo a entrega de valor contínuo e foco no Core Loop do produto.

## 🟢 MUST HAVE (Essencial / O Core Atual)
*Funcionalidades críticas sem as quais o produto não atende ao seu propósito básico.*

* **Autenticação Híbrida:** Login Google para Pais/Jovens e Perfis Gerenciados (sem login) para crianças.
* **Estrutura Familiar:** Vínculo de múltiplos usuários sob um único `familyId`.
* **Ciclo de Tarefas (CRUD):** Criar, Editar, Concluir, Aprovar, Rejeitar.
* **Economia Fechada:** Carteira de XP individual, Loja de Recompensas, Débito e Estorno automático.
* **Segurança de Dados (Privacy):** Isolamento lógico (Filho A não vê tarefas do Filho B).

## 🟡 SHOULD HAVE (Importante / Próxima Sprint)
*Funcionalidades importantes, mas que não impedem o lançamento inicial.*

* **Notificações Push:** Alertas de "Nova Tarefa" e "Aprovação Pendente" (Código pronto, aguardando deploy).
* **Upload de Provas:** Envio de evidência fotográfica ao concluir a tarefa.
* **Streaks (Ofensiva):** Contador de dias seguidos para aumentar a retenção.

## 🟠 COULD HAVE (Desejável / Roadmap Futuro)
*Funcionalidades que geram valor extra, mas possuem menor prioridade estratégica no momento.*

* **Leaderboard:** Ranking semanal competitivo entre irmãos.
* **Season Pass:** Mecânica de "Zerar XP" mensalmente em troca de prêmios maiores.
* **Modo Offline Robusto:** Sincronização complexa de dados sem internet.

## 🔴 WON'T HAVE (Fora de Escopo)
*Itens deliberadamente excluídos desta fase para manter o foco e reduzir riscos.*

* **Pagamentos Reais:** Integração com gateways bancários ou cartão de crédito.
* **Integração IoT:** Conexão com assistentes de voz (Alexa/Google Home).
