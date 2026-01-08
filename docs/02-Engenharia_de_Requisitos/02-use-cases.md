# ⚙️ Casos de Uso (Use Cases)

Detalhamento dos fluxos principais do sistema para validação de regras de negócio.

## UC-01: Ciclo de Vida da Tarefa
* **Atores:** Admin (Pai), Membro (Filho).
* **Pré-condição:** Admin e Membro vinculados na mesma família.

1.  **Admin** cria tarefa "Lavar Louça" (50 XP) atribuída ao Membro.
2.  **Membro** visualiza a tarefa na aba "Missões".
3.  **Membro** executa a ação física e marca o checkbox no App.
4.  **Sistema** altera status para `PENDING_APPROVAL` (Amarelo).
5.  **Admin** recebe notificação visual na Home/Dashboard.
6.  **Admin** valida a execução e clica em "Aprovar".
7.  **Sistema** altera status para `DONE` (Verde) e credita +50 XP na carteira do Membro.

## UC-02: Fluxo de Compra e Estorno (Refund Logic)
* **Atores:** Membro, Admin.
* **Regra de Negócio:** Saldo não pode ficar negativo.

1.  **Membro** acessa Loja e clica em "Comprar Sorvete" (Custo: 100 XP).
2.  **Sistema** verifica saldo (`currentPoints >= price`).
    * *Se insuficiente:* Bloqueia ação.
    * *Se suficiente:* Debita 100 XP imediatamente (Congelamento).
3.  **Sistema** cria solicitação de compra.
4.  **Admin** visualiza solicitação e decide recusar (motivo externo).
5.  **Admin** clica em "Recusar".
6.  **Sistema** executa transação de Estorno: Devolve 100 XP para a carteira do Membro e marca solicitação como cancelada.

## UC-03: Onboarding de Filho Adulto (Linked Account)
* **Atores:** Admin, Novo Usuário.

1.  **Admin** acessa Perfil > "Convidar Membro" e gera o código (ex: `ABC-123`).
2.  **Novo Usuário** baixa o app em seu dispositivo pessoal.
3.  **Novo Usuário** faz login com Google Auth.
4.  **Sistema** pergunta: "Criar Família ou Entrar?". Usuário escolhe "Entrar".
5.  **Novo Usuário** digita o código `ABC-123`.
6.  **Sistema** vincula o `auth.uid` do usuário ao perfil correspondente na família do Admin.
