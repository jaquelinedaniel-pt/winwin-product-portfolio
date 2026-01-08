# 🪙 Lógica Econômica e Fluxo de Estorno (Refund)

Este diagrama detalha o algoritmo de segurança do saldo, focando no tratamento de exceções (Rejeição de Compra) para garantir que nenhum XP seja perdido injustamente (Regra de Negócio RN-002).

## Fluxo de Compra Segura
O sistema utiliza um modelo de "Débito Otimista com Compensação". O XP é debitado na intenção de compra, mas estornado automaticamente caso a validação parental falhe.

```mermaid
flowchart TD
    A["Início: Filho quer 'Sorvete' (100 XP)"] --> B{"Tem Saldo Suficiente?"}
    
    B -- "Não" --> C["Bloqueia Botão / Erro"]
    B -- "Sim" --> D["Debita 100 XP Imediatamente"]
    
    D --> E["Cria Solicitação 'PENDING_PURCHASE'"]
    E --> F["Notifica Pai"]

    F --> G{"Pai Aprova?"}

    G -- "SIM (Compra Válida)" --> H["Gera Voucher 'Sorvete'"]
    H --> I["Filho recebe QR Code/Voucher"]
    I --> J["Fim: XP gasto corretamente"]

    G -- "NÃO (Compra Negada)" --> K["Cancela Solicitação"]
    K --> L["ESTORNO: Credita +100 XP de volta"]
    L --> M["Notifica Filho: 'Compra Cancelada'"]
    M --> N["Fim: Saldo Restaurado"]
    
    %% Estilização
    style D fill:#f39c12,color:white
    style L fill:#e74c3c,color:white
    style H fill:#27ae60,color:white
