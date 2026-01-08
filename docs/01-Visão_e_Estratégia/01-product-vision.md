# 🔭 Visão do Produto e Escopo de Negócio (DRS)

> **Documento de Referência:** DRS - Documento de Requisitos de Software [v1.0]
> **Status:** MVP Validado / Release Candidate 1

## 1. Visão do Produto
O **WinWin** é uma plataforma SaaS Mobile voltada para a gestão familiar gamificada.
O sistema atua como um intermediário digital entre Pais (Gestores) e Filhos (Jogadores), transformando a execução de tarefas domésticas e comportamentais em ativos digitais (XP/Moedas), promovendo educação financeira e redução de conflitos familiares.

## 2. O Problema de Negócio
A gestão manual de tarefas e recompensas em ambientes familiares tende a gerar atrito, falta de consistência e percepção de injustiça. O WinWin resolve isso introduzindo um "juiz imparcial" (o sistema) e uma economia clara baseada em mérito.

## 3. Escopo do Projeto
O sistema abrange quatro pilares funcionais principais:
1.  **Núcleos Digitais:** Criação de famílias multi-tenant.
2.  **Gestão de Ativos:** Atribuição e validação de tarefas (Work).
3.  **Auditoria:** Validação de provas via foto/check (Quality Assurance).
4.  **Economia Fechada:** Gestão de saldo virtual e marketplace de recompensas (Rewards).

## 4. Arquitetura da Solução
Para atender aos requisitos de disponibilidade e segurança, optou-se por uma arquitetura Serverless:
* **Modelo:** Híbrido (Multi-Tenant Familiar).
* **Frontend:** React Native (Expo SDK 53) com NativeWind.
* **Backend:** Firebase (Firestore NoSQL + Authentication).
* **Segurança:** Regras de Firestore (Security Rules) baseadas em `familyId` e `linkedAuthId`.
