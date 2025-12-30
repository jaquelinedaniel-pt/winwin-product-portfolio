> 🚧 **Nota:** Este é um projeto comercial (Proprietário). O código-fonte é privado.
> Este repositório serve como documentação técnica da arquitetura, decisões de engenharia e roadmap de produto.

# 🏆 WinWin - Plataforma de Gamificação Comportamental (V2.0)

> **Arquitetura mobile focada em engajamento, retenção e modificação de hábitos através de sistemas de recompensa.**

<img width="1920" height="1080" alt="Blue and Purple Gradient 3D Modern Tech Payment Mobile App Presentation" src="https://github.com/user-attachments/assets/aedf10d7-1a52-4618-8767-2bedd21ac8d9" /> 

## 🎯 Visão Geral

O **WinWin** é uma solução mobile (Android/iOS) desenhada para resolver o problema de baixa adesão a processos rotineiros. Utilizando princípios de Behavioral Economics (Economia Comportamental), o app separa o esforço (XP - Status) do poder de compra (Moedas - Ativo Financeiro), criando um ecossistema sustentável de motivação.

Caso de Uso Atual: Aplicação no nicho familiar (Gestão de Tarefas Domésticas).

Escalabilidade: A lógica de negócio é agnóstica, podendo ser adaptada para gestão de equipas corporativas ou programas de fidelidade.

**Versão Atual:** 2.0 (Com Auditoria Automática e Gestão de Exceções)

---

## 📚 Documentação Estratégica (Portfólio de PO)

Como Product Owner, a documentação deste projeto foi estruturada para refletir decisões estratégicas de mercado e viabilidade técnica.

### 1. [🎯 Visão do Produto & Business Case](./docs/01-product-vision.md)
> **O que você vai encontrar:** Definição do problema, proposta de valor, matriz de riscos e estratégia de monetização.

### 2. [⚙️ Decisões de Arquitetura & Custo](./docs/02-technical-strategy.md)
> **O que você vai encontrar:** O algoritmo "Lazy Audit" (Serverless) desenhado para custo zero e a estratégia "Dual-Token".

### 3. [🛡️ Relatório de Qualidade (QA)](./docs/03-quality-assurance.md)
> **O que você vai encontrar:** Critérios de aceite, matriz de testes e validação de segurança e privacidade.

---

## 🛠️ Tecnologias & Arquitetura

Projeto desenvolvido com foco em **Performance Real-time** e **Robustez de Dados**.

| Categoria | Stack |
| :--- | :--- |
| **Mobile Core** | React Native, Expo, NativeWind (TailwindCSS) |
| **Backend** | Firebase (Serverless), Cloud Firestore (NoSQL) |
| **State Management** | Context API com *Stable Identity Pattern* |
| **Deploy** | EAS Build (Android APK), Vercel (PWA/iOS) |

---

## 🚀 Funcionalidades da V2.0

### 1. O "Grande Auditor" (Lógica de Auto-Fail)
Implementação de um algoritmo de **"Lazy Audit"** no cliente. Ao abrir o app, o sistema verifica tarefas obrigatórias pendentes de dias anteriores.
* **Punição Automática:** Se uma tarefa obrigatória não foi feita ontem, o sistema gera um log de falha no histórico e aplica uma multa (débito de moedas) automaticamente.
* **Justiça:** Tarefas extras ou opcionais são isentas de punição.

### 2. Solicitações Extras (Fluxo de Aprovação)
Canal de comunicação onde os filhos podem propor "Missões Extras" (ex: "Lavei o carro").
* **Fluxo:** Solicitação -> Análise do Admin -> Aprovação (Crédito imediato) ou Recusa (Com feedback justificado).

### 3. Economia Dual-Token Refatorada
Separação total das entidades financeiras para evitar desmotivação:
* **⭐ XP (Nível):** Acumulador histórico imutável.
* **🪙 Moedas (Saldo):** Ativo transacional para troca na Loja.

### 4. Compatibilidade Web/Mobile
Adaptação da interface e dos métodos de interação (`Alert` vs `window.confirm`) para garantir funcionamento pleno tanto em APKs Android quanto em navegadores iOS (PWA).

---

## 🧠 Decisões de Arquitetura & Resolução de Problemas

### Desafio 1: Race Condition no Logout
**Problema:** O app crashava ao tentar ler dados de usuário durante o processo de *unmount* do componente de autenticação.
**Solução:** Implementação do **Stable Identity Pattern** no `FamilyContext`, utilizando referências (`useRef`) para manter um cache temporário do perfil durante a transição de logout.

### Desafio 2: Auditoria sem Backend (Cron Jobs)
**Problema:** Necessidade de verificar falhas diárias sem custo de servidor dedicado rodando 24h.
**Solução:** Desenvolvimento de lógica de verificação baseada em eventos de abertura do app (`useEffect`), comparando *timestamps* de última atualização com a data corrente para processar lotes de atualizações (`WriteBatch`) retroativas.

---

## 📸 Galeria

| Painel de Missões | Auditoria de Falhas | Loja de Recompensas |
 <img width="1920" height="1536" alt="788shots_so (1)" src="https://github.com/user-attachments/assets/7015965b-618e-4cd1-a913-7d36861d7fe0" /> <img width="1920" height="1536" alt="736shots_so" src="https://github.com/user-attachments/assets/c4e2028b-9b22-4d12-919c-ca25e80a4614" /> <img width="1920" height="1536" alt="664shots_so" src="https://github.com/user-attachments/assets/7dcc3dce-c7b8-40a4-8abe-4bb85f149f8d" /> <img width="1920" height="1536" alt="562shots_so" src="https://github.com/user-attachments/assets/365d3e23-1fcb-4319-97af-dfbe749448a1" /> <img width="1920" height="1536" alt="84shots_so" src="https://github.com/user-attachments/assets/ffd57a34-2127-4d58-96a4-6f2185fccfd4" /> <img width="1920" height="1536" alt="190shots_so" src="https://github.com/user-attachments/assets/64fa8cd2-553c-4eef-b83d-4c7ce8819d30" />


---
## 👩‍💻 Sobre a Product Owner

<div align="center">
  <h3>Jaqueline Daniel</h3>
  <p><strong>Product Owner | Business Analyst & Strategist</strong></p>
  <p>15 anos de experiência transformando complexidade operacional em produtos digitais de alto valor.</p>
   
  <p>
    <a href="https://www.linkedin.com/in/jaquelinedaniel-pt" target="_blank">
      <img src="https://img.shields.io/badge/-Conectar_no_LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank">
    </a> 
    <a href="https://jaquelinedaniel.pt" target="_blank">
      <img src="https://img.shields.io/badge/-Ver_Portfolio_Executivo-0f172a?style=for-the-badge&logo=react&logoColor=FFD700" target="_blank">
    </a>
  </p>
</div>

---
## 🚀 Como Rodar (Conceitual)

*Este é um projeto de código fechado (proprietário). Abaixo descrevo o ambiente de execução.*

O projeto utiliza o **Expo** para desenvolvimento ágil.
```bash
# Instalação de dependências
npm install

# Execução em modo Túnel (para testes em rede física)
npx expo start --tunnel
