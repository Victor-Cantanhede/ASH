# 🚀 Autonomous Software House Ecosystem

> **Template de Ecossistema Multiagente Autônomo com Spec-Driven Development (SDD), NestJS, Next.js App Router, PostgreSQL 16, Prisma ORM e Verificação Playwright.**

---

## 🌟 Visão Geral

Este repositório é um **motor limpo de Software House Autônoma** para o **Antigravity**. 
Ele contém exclusivamente a inteligência operacional (regras, skills e subagentes) dentro da pasta `.gemini/`. 

Nenhum arquivo de código ou projeto existe previamente aqui. O repositório é uma folha em branco: **todo o software (`specs/`, `apps/api`, `apps/web`, banco de dados, Docker e testes) é gerado do zero pelos agentes** assim que você enviar o primeiro prompt no chat do VS Code.

```
┌────────────────────────────────────────────────────────────────────────┐
│                        PIPELINE DOS 7 AGENTES                          │
├─────────────────┬─────────────────┬─────────────────┬──────────────────┤
│ 01. INTERVIEWER │ 02. ARCHITECT   │ 03. DESIGNER    │ 04. FULLSTACK    │
│ Descoberta sem  │ Modelo ER, DTOs │ 4 Estados de UI │ NestJS + Next.js │
│ tecnicalidades  │ e OpenAPI 3.0   │ e Design Tokens │ Migrações seguras│
├─────────────────┼─────────────────┼─────────────────┼──────────────────┤
│ 05. AUDITOR     │ 06. QA E2E      │ 07. RELEASE     │ 00. ORQUESTRADOR │
│ Rastreabilidade │ Playwright      │ 1-Click Scripts │ Loop autônomo    │
│ e Veto db push  │ Zero Erros 500  │ e HANDOFF.md    │ sem pausas       │
└─────────────────┴─────────────────┴─────────────────┴──────────────────┘
```

---

## 🛡️ As Regras Pétreas Invioláveis

1. **Zero Tolerance para `prisma db push`:** Todas as alterações estruturais de banco de dados devem obrigatoriamente ser migradas via `npx prisma migrate dev --name <nome>` no ambiente local e `npx prisma migrate deploy` em produção.
2. **Spec-Driven Development (SDD):** Toda implementação se baseia exclusivamente nos artefatos da pasta `specs/` (gerados a partir da entrevista inicial):
   - `specs/functional.spec.md` (Requisitos, personas e regras de negócio)
   - `specs/database.spec.mermaid` (Diagrama ER e integridade referencial)
   - `specs/api.spec.yaml` (Contrato OpenAPI 3.0 completo)
   - `specs/ui-ux.spec.md` (Design tokens e os 4 estados obrigatórios de UI)
   - `specs/acceptance.spec.feature` (Cenários BDD Gherkin para o Playwright)
3. **Autonomia Contínua:** Após a validação da entrevista humanizada pelo usuário, o ciclo multiagente executa em loop contínuo sem pausas ou perguntas triviais até a entrega final.
4. **Os 4 Estados Obrigatórios de Tela:** Toda interface dinâmica implementa explicitamente:
   - **Loading State:** Skeletons animados (sem layout shift).
   - **Empty State:** Ilustração com mensagem amigável e ação primária (CTA).
   - **Error State:** Alerta descritivo com botão de nova tentativa (*Retry*).
   - **Success Feedback:** Toast afirmativo imediato para mutações.
5. **QA com Tolerância Zero a Falhas:** Playwright 100% verde com reprovação imediata diante de qualquer `console.error` ou respostas de rede `5xx`.

---

## 📂 Estrutura Inicial do Repositório (Engine Puro)

```text
autonomous-software-house/
├── .gemini/
│   ├── rules/
│   │   └── 00-autonomous-orchestrator.md     # Regra mestra lida automaticamente pelo Antigravity
│   └── skills/
│       └── auto-software-house/
│           ├── SKILL.md                      # Definição e ciclo de vida da skill
│           └── agents/                       # Definições dos 7 agentes especialistas
│               ├── 01_client_interviewer.md
│               ├── 02_system_architect.md
│               ├── 03_ui_ux_designer.md
│               ├── 04_fullstack_dev.md
│               ├── 05_anti_hallucination.md
│               ├── 06_qa_playwright.md
│               └── 07_release_manager.md
├── .gitignore
└── README.md                                 # Este guia
```

> **Nota:** As pastas `specs/`, `apps/api`, `apps/web`, `docker-compose.yml`, `run.bat` e `HANDOFF.md` serão criadas **dinamicamente pelos próprios agentes** durante a execução do projeto solicitado.

---

## ⚡ Como Usar no VS Code com o Antigravity

### Passo 1: Abrir a Pasta no VS Code
Abra a pasta do projeto no VS Code:
```bash
code C:\Users\victo\dev\autonomous-software-house
```

### Passo 2: Abrir o Chat do Antigravity
Abra o chat integrado do Antigravity no painel do VS Code.

### Passo 3: Enviar o Primeiro Prompt
Basta solicitar a criação do software que você deseja, por exemplo:
```text
Quero criar um sistema completo para gestão de uma barbearia com agendamentos e controle financeiro.
```
*(Ou use `/goal Crie um sistema de barbearia completo` para execução profunda).*

O agente **01_client_interviewer** assumirá o chat fazendo as perguntas de negócio em linguagem humanizada. Ao responder, os demais agentes assumirão a geração de specs, arquitetura, código NestJS/Next.js, auditoria anti-alucinação, testes com Playwright e entrega turnkey.
