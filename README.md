# Pós Disciplina 05 - Ferramentas de IA para UX e UI

## Introdução
Este repositório contém todos os projetos desenvolvidos durante a disciplina **Ferramentas de IA para UX e UI**, abordando desde fundamentos de engenharia de requisitos com IA até implementações avançadas de aplicações full-stack com IA integrada.

Cada módulo foi desenvolvido para demonstrar na prática como as ferramentas de IA transformam o ciclo de desenvolvimento de software, desde o refinamento de requisitos e design de sistemas até automação de testes e integração de lógica de IA em aplicações cliente-servidor. O repositório explora desde o uso de LLMs para engenharia de requisitos até desenvolvimento AI-Native em frontend, orquestração de agentes, automação E2E e integração de IA em arquiteturas full-stack, utilizando TypeScript como linguagem principal.

## Módulos

### Módulo 01: Engenharia de Requisitos e Design de Sistemas com IA

#### **Projeto:** [Engenharia de Requisitos](module-01)

**Tecnologias utilizadas:**
- **Google Gemini** - Plataforma de IA para refinamento técnico via Google AI Studio
- **Mermaid.js** - Biblioteca para diagramação automatizada de fluxos
- **JSON Prompts** - Padrão para instruções estruturadas e controle de comportamento do modelo
- **Google AI Studio** - Ambiente para execução dos prompts estruturados

**Conceitos abordados:**
- Refinamento técnico e redução de variabilidade na engenharia
- Engenharia de prompt com controle de temperature e safety
- Uso de Mermaid.js para conversão automática de lógica em diagramas visuais
- Data Discovery: análise e sanitização estruturada de feedback de usuários

**Aplicação prática:**
- Projeto de refinamento de requisitos que transforma briefing bruto em fluxos lógicos e mapeamento de edge cases
- Destilação de insights técnicos a partir de grandes volumes de feedback não estruturado
- Uso do Google AI Studio para execução de prompts estruturados
- Exportação de dados para aplicação em backlog técnico e priorização

### Módulo 02: O Ecossistema AI-Native no Frontend

#### **Projeto:** [Pix App](module-02)

**Tecnologias utilizadas:**
- **Angular 21** - Framework frontend com integração de AI tools
- **Google Gemini** - Assistente de IA integrado ao CLI do Angular para geração de código e melhores práticas
- **TypeScript** - Linguagem de tipagem estática para desenvolvimento robusto
- **CSS** - Estilização do aplicativo

**Conceitos abordados:**
- Desenvolvimento AI-Native no Frontend
- Integração de ferramentas de IA no ciclo de vida do desenvolvimento (CLI AI-powered)
- Implementação de fluxos de pagamento (Pix) com auxílio de IA
- Aplicação de padrões modernos de arquitetura Angular
- Adicionado MPC do Angular para ajudar no desenvolvimento e pegar as melhores práticas atuais.

**Aplicação prática:**
- Desenvolvimento de um aplicativo de pagamentos (Pix App) utilizando a abordagem AI-Native
- Automação da criação de componentes e serviços via CLI com suporte do Gemini
- Implementação de interfaces responsivas e fluxos de usuário otimizados por IA
- Validação de melhores práticas de desenvolvimento frontend através de sugestões de IA

**Comandos executados**:
```bash
npx @angular/cli@21 new pix-app sstyles css --rounting true
  - Selecionar AI tools: Gemini
npm ci
npm start
```

### Módulo 03: Orquestração de Agentes Locais e Nuvem

#### **Projeto:** [Cfp Platform](module-03)

**Tecnologias utilizadas:**
- **Nx 22** - Monorepo toolchain para orquestração de múltiplos aplicativos e bibliotecas
- **Angular 21** - Frontend framework para a aplicação web
- **NestJS** - Framework backend Node.js para APIs
- **Jules (Google)** - Agente de IA na nuvem para automação e orquestração
- **TypeScript** - Linguagem tipada para todo o stack
- **Docker** (opcional) - Contêineres para ambiente de desenvolvimento e implantação

**Conceitos abordados:**
- Orquestração de agentes locais (Nx) e agentes na nuvem (Jules)
- Arquitetura de monorepo com Nx e integração de aplicações Angular + Nest
- Estratégias de comunicação entre agentes via APIs e mensagens
- Uso de ferramentas de IA para geração de código e automação de pipelines
- Gestão de memória e reflexão de agentes (memória persistente, lições aprendidas)

**Aplicação prática:**
- Plataforma CFP que combina frontend Angular e backend NestJS
- Integração de agentes locais para geração de código, testes e deploy automatizados
- Agente Jules na nuvem para monitoramento, diagnóstico e respostas a incidentes
- Estrutura de memória/reflexão para capturar lições de execuções e melhorar o fluxo

**Comandos executados**:
```bash
npm install -g nx@latest
npx create-nx-workspace@latest module-03 --preset=apps --nxCloud=skip
  - Selecionar improve Nx: Yes
npm install -D @nxqangular @nx/nest @nx/js
nx g @nxqangular:application frontend --routing=true --style=css --standalone=true --strict
  - Selecionar unit test runner: vitest-angular
  - Selecioanar E2E test runner: playwright
  - Selecionar nuild: esbuild
  - Selecionar SSR: false
nx g @nx/nest:apllication api --frontendProject=frontend --strict
  - Selecionar linter: eslint
  - Selecionar unit test runner: jest
nx g @nx/js:library shared-types --buildable
  - Selecionar bundler to build library: esbuild
  - Selecionar unit test runner: jest
nx run-many -t serve -p api frontend
npx nx migrate latest

npm install -g @fission-ai/openspec@latest
openspec init --tools github-copilot 
  - Ou qualquer outro antigravity, auggie, bob, claude, ...

git worktree add ../worktreees/cfp-api -b ai/feat-cfp-api
git worktree add ../worktreees/cfp-api -b ai/feat-cfp-ui

git checkout -b chore/integrate-cfp-feature
git merge ai/feat-cfp-api --no-ff -m "chore(api): merge cfp backend"
git merge ai/feat-cfp-ui --no-ff -m "chore(api): merge cfp frontend"
git merge chore/integrate-cfp-feature --no-ff -m "feat(system): add integrated cpf dashboard with consistent ui"
git worktree remove ../worktrees/cfp-api
git worktree remove ../worktrees/cfp-ui
git branch -d ai/feat-cfp-api ai/feat-cfp-ui

git fetch origin
git checkout featqevent-registration-134234324234414331
nx run-many -t serve -p api frontend
```

### Módulo 04: Automação E2E e QA AI-Native

#### **Projeto:** [Cfp Platform V2](module-04)

**Tecnologias utilizadas:**
- **Cypress IA** - Framework de testes E2E com IA para geração automática de testes a partir de prompts
- **Playwright** - Framework de automação de navegadores para testes E2E
- **Nx 22** - Monorepo para orquestração de aplicações e bibliotecas
- **Angular 21** - Framework frontend para a aplicação web
- **TypeScript** - Linguagem tipada para desenvolvimento robusto

**Conceitos abordados:**
- Automação E2E com IA (Cypress IA) para geração de testes a partir de prompts
- Implementação de testes de qualidade com Playwright
- Integração de IA no ciclo de QA e garantia de qualidade
- Orquestração de testes em monorepo com Nx
- Testes automatizados com suporte de IA para geração e manutenção

**Aplicação prática:**
- Plataforma CFP V2 com automação E2E e QA AI-Native
- Geração automática de testes E2E usando Cypress IA a partir de prompts
- Implementação de testes de regressão e funcional com Playwright
- Integração de testes no ciclo de CI/CD com Nx
- Validação de fluxos de usuário e funcionalidades críticas com suporte de IA

**Comandos executados**:
```bash
nx add/@nx/cypress
nx run-many -t serve -p api frontend
npx nx e2e frontend-e2e
nx open-cypress frontend-e2e
```

### Módulo 05: Integração de Lógica de IA no Cliente e no Servidor

#### **Projeto:** [Brag Bot](module-05)

**Tecnologias utilizadas:**
- **Angular 21** - Framework frontend com SSR (Server-Side Rendering)
- **Tailwind CSS** - Framework de estilização para interfaces modernas
- **Genkit CLI** - Ferramenta de linha de comando para orquestração de IA
- **Genkit** - Framework para integração de lógica de IA em aplicações
- **Google GenAI** - SDK para integração com modelos de IA do Google
- **TypeScript** - Linguagem tipada para desenvolvimento robusto

**Conceitos abordados:**
- Integração de lógica de IA no frontend (Angular) e backend (Genkit)
- Orquestração de fluxos de IA com Genkit CLI
- Uso de SSR (Server-Side Rendering) para aplicações com IA
- Integração de modelos de IA com Genkit e Google GenAI
- Arquitetura full-stack com IA integrada no cliente e servidor

**Aplicação prática:**
- Desenvolvimento de um chatbot (Brag Bot) com IA integrada no frontend e backend
- Implementação de SSR para melhor performance e SEO
- Uso do Genkit para orquestrar fluxos de IA e gerar respostas inteligentes
- Integração com modelos do Google GenAI para capacidades avançadas de IA
- Interface moderna com Tailwind CSS e experiência de usuário otimizada

**Comandos executados**:
```bash
ng new brag-bot --ssr
  - Selecionar stylesheet: Tailwind CSS
  - Selecionar AI tools: Gemini
npm install -g genkit-cli
npm install genkit @genkit-ai/google-genai

npm start
  - Executar http://localhost:4200/
npm run genkit:ui
  - Executar http://localhost:4000/
```
