# Brainstorming: Framework de Agentes para Ciclo de Vida de Desenvolvimento (SDLC)

## 🎯 Objetivo Principal
Criar um ecossistema (processos, padrões, prompts e ferramentas de CLI/extensões) agnóstico de linguagem que auxilie equipes e desenvolvedores individuais a integrar Agentes de IA em todas as fases do desenvolvimento de software.

## 💡 Nomes Sugeridos para o Projeto
*   **AgentFlow** (Foco no fluxo contínuo)
*   **AeroSDLC** (Leveza e aerodinâmica no processo de desenvolvimento)
*   **OmniAgent** (Onipresença no ciclo de vida)
*   **CognitiveLoop** (Foco na interação iterativa e inteligência)
*   **DevSwarm** (Metáfora de enxame trabalhando cooperativamente)

## 🧩 Componentes Centrais de um Framework Agnóstico

Para o framework funcionar independente da linguagem (Python, Go, JS, Rust, etc.), precisamos padronizar a **comunicação**, o **contexto** e o **estado**.

1.  **Workspaces e Contexto Padronizados:**
    *   Todo projeto que usa o framework teria uma pasta oculta (ex: `.agent/` ou `.ai/`).
    *   Dentro dessa pasta, guardamos:
        *   `context.json` ou `state.yml`: O que está sendo feito agora? Qual a arquitetura do projeto?
        *   `memory/`: Histórico de decisões arquiteturais (*ADRs - Architecture Decision Records*) gerados pelos agentes.
        *   `skills/`: Scripts ou prompts específicos que variam de projeto para projeto.

2.  **Agentes Especializados vs. Generalistas:**
    Ao invés de um único "super agente", teríamos papéis claros (como numa squad de engenharia):
    *   **Agent Architect (Arquiteto):** Lê requisitos soltos e propõe uma estrutura de arquivos, escolhas de design patterns e contratos de API (Gera especificações no formato OpenAPI ou similar).
    *   **Agent Coder (Desenvolvedor):** Recebe os contratos/especificações e implementa. Foca apenas na lógica e no código.
    *   **Agent QA (Testador):** Lê a implementação do Coder e cria testes unitários e de integração antes mesmo da revisão humana.
    *   **Agent Reviewer (Revisor):** Faz análises estáticas semânticas. Verifica se o código atende aos requisitos iniciais e se segue as boas práticas (independente do linter da linguagem).

3.  **Padronização de Interface (I/O do Agente):**
    *   Como os agentes se comunicam? O Arquiteto cospe um `.md`, e o Coder deve ser capaz de ler e gerar os arquivos.
    *   Usar um formato estruturado (como Frontmatter Markdown ou JSON/YAML) para passar o bastão entre eles.

## 🔄 O Ciclo de Vida Sugerido (Workflow)

1.  **Ideação/Design (`/explore` ou `init`):**
    *   O usuário descreve a feature em linguagem natural.
    *   O *Architect Agent* devolve um plano de implementação (quais arquivos criar, quais alterar, pseudocódigo/assinaturas de funções).
2.  **Aprovação Humana (Human-in-the-loop):**
    *   O desenvolvedor revisa o plano, altera o markdown e aprova.
3.  **Implementação Iterativa (`/apply` ou `build`):**
    *   O *Coder Agent* entra em ação lendo o plano aprovado.
    *   Ele gera código, tenta compilar/rodar (se houver hooks configurados para a linguagem específica).
4.  **Loop de Feedback Automático:**
    *   Se o teste ou compilação falha, entra o *Debugger Agent* automaticamente (com limite de retentativas para evitar looping infinito).
5.  **Revisão (Auto-Review / Peer-Review):**
    *   O *Reviewer Agent* verifica se todos os requisitos do passo 1 foram cumpridos.

## 🚧 Desafios Iniciais (Para refletirmos)

*   **Tamanho do Contexto:** Como não estourar o limite de tokens fornecendo a codebase toda? Presumo que precisaremos de um sistema de RAG inteligente ou geradores de mapas da codebase (como o `tree` + AST extraction).
*   **Ações Destrutivas:** Agentes alterando arquivos errados. Precisamos de *Git-awareness* embutido (ex: o agente sempre cria uma nova branch ou commita as mudanças por etapa para fácil *rollback*).
*   **Lock-in de LLM:** O framework não pode depender apenas do GPT-4 ou Claude 3. Precisa de uma camada de abstração (ex: LiteLLM) para permitir LLMs locais (Ollama) ou outros provedores.

---
*Este é um documento vivo. Podemos iterar sobre essas ideias e expandi-las nas próximas conversas.*
