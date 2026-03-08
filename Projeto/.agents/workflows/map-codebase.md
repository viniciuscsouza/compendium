---
description: Mapear a base de código existente (Brownfield) camada por camada
---

# Workflow: Map Codebase (/map-codebase)

<purpose>
Orquestrar o mapeamento completo de uma base de código existente (projeto *brownfield*), preenchendo todos os artefatos do Agentic SDLC Framework de forma estruturada.
</purpose>

<philosophy>
**Por que mapear sequencialmente (uma camada por vez):**
- **Foco e Qualidade:** O agente não perde o contexto tentando analisar ferramentas de CI/CD e regras de negócio ao mesmo tempo.
- **Redução de Alucinações:** A cada camada, o agente lê os templates específicos e busca evidências restritas àquele domínio.
- **Controle do Usuário:** Permite que o usuário revise o mapeamento de uma camada antes que o agente inicie a próxima.
</philosophy>

<process>

**Instruções para o Agente de IA:**
Ao ser acionado através do comando `/map-codebase`, você deve executar as etapas abaixo estritamente de forma **sequencial**. 

**Regra Crítica:** Você **NÃO** deve tentar fazer o mapeamento de mais de uma camada na mesma interação. Para cada etapa abaixo, você assumirá a *persona* e as regras descritas no arquivo `@[.agents/codebase-mapper.md]`, focando na camada da vez.

### Etapa 1: Preparação
1. Leia as regras completas do agente mapeador no arquivo `@[.agents/codebase-mapper.md]` para entender seu papel.
2. Comunique ao usuário: *"Iniciando o mapeamento sequencial da Codebase. Vou analisar o projeto camada por camada. Iniciaremos pela camada de Tecnologia."*

### Etapa 2: Mapeamento de Tecnologia (tech)
1. **Foco:** `tecnologia`
2. **Ação:** Siga os passos do *Codebase Mapper* para inspecionar a base de código e preencher os arquivos `STACK.md` e `INTEGRATIONS.md`.
3. Informe ao usuário o resumo da conclusão desta etapa e **aguarde a autorização** para iniciar a próxima etapa.

### Etapa 3: Mapeamento de Arquitetura (arch)
1. **Foco:** `arquitetura`
2. **Ação:** Insira as descobertas estruturais e de design pattern preenchendo os arquivos `ARCHITECTURE.md` e `STRUCTURE.md`.
3. Informe ao usuário o resumo da conclusão desta etapa e **aguarde a autorização** para iniciar a próxima etapa.

### Etapa 4: Mapeamento de Qualidade (quality)
1. **Foco:** `qualidade`
2. **Ação:** Vasculhe configurações de linting e testes para preencher `CONVENTIONS.md` e `TESTING.md`.
3. Informe ao usuário o resumo da conclusão desta etapa e **aguarde a autorização** para iniciar a próxima etapa.

### Etapa 5: Mapeamento de Preocupações (concerns)
1. **Foco:** `preocupacoes`
2. **Ação:** Identifique débitos técnicos, *TODOs* e código frágil, documentando tudo em `CONCERNS.md`.
3. Informe ao usuário o resumo da conclusão desta etapa e **aguarde a autorização** para iniciar a próxima etapa.

### Etapa 6: Mapeamento de Domínio (domain)
1. **Foco:** `dominio`
2. **Ação:** Identifique entidades de negócio e a linguagem ubíqua documentando em `DOMAIN.md`.
3. Informe ao usuário o resumo da conclusão desta etapa e **aguarde a autorização** para iniciar a próxima etapa.

### Etapa 7: Mapeamento de Fluxos (workflows)
1. **Foco:** `fluxos`
2. **Ação:** Mapeie os processos de build, scripts npm/yarn e fluxos de CI/CD para o `WORKFLOWS.md`.
3. Informe ao usuário o resumo da conclusão desta etapa.

### Etapa 8: Finalização
Gere um relatório final no chat informando que todas as camadas do Agentic SDLC Framework foram mapeadas com sucesso. Mostre uma lista de todos os `[N]` arquivos gerados dentro do diretório `.agents/`.

</process>
