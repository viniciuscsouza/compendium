
 Inicializar projeto
	Brownfield:
		- Detecta solução
		- Analisa dependências
		- Faz perguntas sobre a arquitetura
		- Gera um AGENTS.md personalizado para codebase
	Greenfield:
		- Pergunta o que está construindo
		- Analisa a complexidade do domínio
		- O tamanho da equipe
		- Ciclo de vida do projeto
		- Recomenda abordagens e justifica recomendação:
			- Vertical Slice
			- Clean Architecture
			- DDD
			- Monolito Modular
		-Cria estrutura básica de tudo
Criar Feature
	Codificação
	Checklist
Verificar (etapa em loop até passar por todas as etapas)
	Código
	Analise estática
	Varredura antipatterns
	Testes
	Verificação de segurança
	Formatação
	Revisa diff
Revisão
	Analisa código semânticamente
	Busca antipatterns
	Busca código morto
	Analisa conformidade com arquitetura
	Analise impacto
	Analisa cobertura de testes

---
idea → roadmap → small tasks → execute each task in isolation → commit


Orquestrador
	- Identificar codebase (Agente Explorador)
		- Brownfield: Entender a codebase primeiro. Mapear as alterações significantes na codebase. Antes de um grande refactor (entender o estado atual). Quando referências em STATE.md estivem com informações obsoletas.
		- Greenfield: Projetos sem código ou com poucos arquivos (< 5 arquivos)

Camada de Tecnologia
- STACK.md
- INTEGRATIONS.md
Camada de Arquitetura
- ARCHITECTURE.md
- STRUCTURE.md
Camada de Qualidade
- CONVENTIONS.md
- TESTING.md
Camada de Preocupações
- CONCERNS.md

---

## Antes de escrever qualquer código

**Entender a arquitetura atual**

1. Ler o README, docs de arquitetura e ADRs existentes
2. Listar todos os diretórios e arquivos de entrada (`tree`, `ls -R`, ou equivalente)
3. Identificar o padrão arquitetural dominante (layered, hexagonal, modular monolith, etc.)
4. Mapear as dependências externas (libs, serviços, APIs)
5. Identificar os pontos de entrada da aplicação (main, entrypoints, handlers)
6. Ler os arquivos de configuração (env, YAML, schemas)
7. Examinar os testes existentes para inferir contratos e comportamentos esperados

**Mapear a tarefa às camadas afetadas**

8. Decompor a tarefa em requisitos funcionais e não-funcionais
9. Identificar quais módulos, camadas e interfaces serão tocados
10. Detectar dependências transitivas que a mudança pode impactar
11. Verificar se há código existente que resolve parte do problema
12. Identificar os limites de responsabilidade (o que muda vs. o que não deve mudar)

**Produzir o plano de implementação**

13. Esboçar o plano em etapas numeradas, da menor unidade até a integração
14. Associar cada etapa a um arquivo, módulo ou camada específica
15. Ordenar as etapas por dependência (o que precisa existir antes do quê)
16. Explicitar os contratos novos ou modificados (interfaces, tipos, schemas)
17. Listar os testes que precisarão ser criados ou atualizados

**Iterar o plano até que esteja sólido**

18. Revisar o plano contra os requisitos originais e verificar cobertura total
19. Identificar gaps, ambiguidades ou assunções não validadas
20. Checar se o plano introduz acoplamento desnecessário ou viola fronteiras arquiteturais
21. Simplificar: remover etapas redundantes ou que podem ser colapsadas
22. Validar o plano com o interlocutor antes de iniciar qualquer implementação


### Passo 1: Compreender a tarefa

Esclareça o que o usuário deseja construir. Faça perguntas focadas se o pedido for ambíguo. Não assuma requisitos que não foram declarados.

### Passo 2: Detectar Arquitetura

Use o `architecture-advisor`habilidade para determinar a arquitetura do projeto:

- Verifique se há marcadores de arquitetura existentes (estrutura de pasta, referências de projeto, padrões)
- Se nenhuma arquitetura for estabelecida, execute o questionário de arquitetura
- Carregue a habilidade específica da arquitetura apropriada (vertical-slice, clean-architecture, ddd)

### Passo 3: Mapear Áreas Afetadas

Identifique cada camada, módulo e limite que a tarefa toca:

- Quais projetos/pastas terão arquivos novos ou modificados?
- Existem preocupações transversais (auth, cache, validação, registro)?
- Qual código existente será impactado? Uso `find_references`e `find_callers`Ferramentas MCP para raio de explosão.
- Existem migrações de banco de dados necessárias?

### Passo 4: Produzir o Plano

Saída de um plano numerado com esta estrutura:

```
## Plan: [Task Title]

**Architecture:** [Detected architecture]
**Affected layers:** [List]
**Estimated steps:** [Count]

### Steps
1. [Step] -- [Which file/layer] -- [Why this order]
2. ...

### Open Questions
- [Anything that needs user input before proceeding]

### Risks
- [Potential issues and mitigations]
```

### Passo 5: Iterar

Apresente o plano e pergunte: "Este plano parece certo, ou devo ajustar alguma coisa?" Revise até que o usuário confirme. Só então proceder à implementação.

## Exemplo

```
User: /plan Add a product catalog feature with search and filtering

Claude: Let me analyze your project structure first...

## Plan: Product Catalog Feature

**Architecture:** Vertical Slice Architecture
**Affected layers:** Features/, Infrastructure/Persistence/, Tests/
**Estimated steps:** 6

### Steps
1. Create Product entity + EF config -- Domain layer -- Foundation for everything else
2. Add migration -- Infrastructure -- Schema must exist before features
3. Scaffold GetProducts feature (with filtering) -- Features/Products/ -- Read path first
4. Scaffold CreateProduct feature -- Features/Products/ -- Write path
5. Add integration tests -- Tests/Features/Products/ -- Verify both features
6. Wire up OpenAPI metadata -- Features/Products/ -- Documentation

### Open Questions
- Should search be full-text (PostgreSQL tsvector) or simple LIKE?
- Do products need categories/tags for filtering?

Does this plan look right, or should I adjust anything?
```

## Relacionado

- `/scaffold`-- Gerar os arquivos uma vez que o plano é aprovado
- `/verify`-- Executar a verificação após a implementação do plano


---

# Slash Command: `/planejamento`

## Descrição

Antes de escrever qualquer código, analise a arquitetura da codebase, mapeie as áreas afetadas e produza um plano de implementação numerado. Itere o plano com o usuário até que ele esteja sólido.

---

## Quando pular o planejamento

Execute diretamente, sem planejamento, se a tarefa for **qualquer um** dos casos abaixo:

- Alteração de arquivo único isolado
- Correção de bug simples e localizado
- Correção de erro de digitação
- Ajuste de configuração (variável de ambiente, valor de config, flag)

Para todos os outros casos, siga os passos abaixo.

---

## Passo 1 — Compreender a Tarefa

Esclareça o que o usuário deseja construir.

- Leia o pedido com atenção e identifique o objetivo principal.
- Se o pedido for ambíguo, faça **perguntas focadas** antes de continuar — uma pergunta de cada vez.
- **Não assuma requisitos que não foram declarados.**
- Só avance para o Passo 2 quando o objetivo estiver claro.

---

## Passo 2 — Detectar a Arquitetura

Determine a arquitetura do projeto antes de qualquer mapeamento.

1. Liste a estrutura de diretórios (`tree` ou equivalente).
2. Leia o README, docs de arquitetura e ADRs existentes.
3. Verifique marcadores arquiteturais: nomes de pastas (`features/`, `domain/`, `application/`, `slices/`), arquivos de projeto, padrões de nomenclatura.
4. Leia os arquivos de configuração (env, YAML, schemas, arquivos de build).
5. Examine os testes existentes para inferir contratos e comportamentos esperados.
6. Identifique os pontos de entrada da aplicação (main, entrypoints, handlers, controllers).
7. Mapeie as dependências externas (libs, serviços, APIs, bancos de dados).

Com base nesses dados, classifique a arquitetura em uma das categorias:

- **Vertical Slice** — funcionalidades isoladas em fatias verticais
- **Clean Architecture / Hexagonal** — camadas: Domain, Application, Infrastructure, Presentation
- **DDD** — contextos delimitados, agregados, repositórios, eventos de domínio
- **Modular Monolith** — módulos com fronteiras explícitas
- **Layered (MVC/tradicional)** — controllers, services, repositories
- **Não estabelecida** — execute o questionário de arquitetura (veja abaixo)

> **Questionário de arquitetura** (use quando nenhum padrão for detectado):
> 
> 1. O projeto tem mais de um módulo/contexto de negócio?
> 2. Existe separação entre lógica de negócio e infraestrutura?
> 3. Há testes de unidade separados dos de integração?
> 4. Qual é o tamanho esperado do projeto (pequeno / médio / grande)?
> 
> Com base nas respostas, recomende a arquitetura mais adequada e peça confirmação antes de continuar.

---

## Passo 3 — Mapear as Áreas Afetadas

Identifique cada camada, módulo e limite que a tarefa toca.

- Quais projetos, pastas e arquivos terão código novo ou modificado?
- Existem preocupações transversais envolvidas? (autenticação, cache, validação, logging, autorização)
- Qual código existente será impactado? Use `find_references` e `find_callers` para medir o raio de explosão.
- Há migrações de banco de dados necessárias?
- Existem dependências transitivas que a mudança pode afetar indiretamente?
- O que **não deve mudar** — identifique os limites de responsabilidade.

---

## Passo 4 — Produzir o Plano

Gere um plano numerado com a estrutura abaixo. Cada etapa deve indicar **o quê**, **onde** e **por quê nessa ordem**.

```
## Plano: [Título da Tarefa]

**Arquitetura detectada:** [Arquitetura]
**Camadas afetadas:** [Lista]
**Etapas estimadas:** [Contagem]

### Etapas
1. [O que fazer] -- [Arquivo/camada] -- [Por que nessa ordem]
2. ...

### Perguntas em aberto
- [Qualquer ponto que precise de input do usuário antes de prosseguir]

### Riscos
- [Problemas potenciais e mitigações]
```

---

## Passo 5 — Iterar até Confirmar

Apresente o plano e pergunte:

> _"Este plano parece certo, ou devo ajustar alguma coisa?"_

- Revise o plano com base no feedback.
- Verifique se o plano cobre todos os requisitos declarados.
- Elimine etapas redundantes ou que podem ser colapsadas.
- Confirme que o plano não introduz acoplamento desnecessário nem viola fronteiras arquiteturais.
- **Só inicie a implementação após confirmação explícita do usuário.**

---

## Exemplo

```
Usuário: /planejamento Adicionar um catálogo de produtos com busca e filtros

Claude: Deixa eu analisar a estrutura do projeto primeiro...

[lê diretórios, README, testes, configurações]

## Plano: Catálogo de Produtos com Busca e Filtros

**Arquitetura detectada:** Vertical Slice Architecture
**Camadas afetadas:** Features/, Infrastructure/Persistence/, Tests/
**Etapas estimadas:** 6

### Etapas
1. Criar entidade Product + configuração EF -- Domain layer -- Base para tudo o que vem depois
2. Adicionar migration -- Infrastructure -- Schema precisa existir antes das features
3. Criar feature GetProducts (com filtros) -- Features/Products/ -- Caminho de leitura primeiro
4. Criar feature CreateProduct -- Features/Products/ -- Caminho de escrita
5. Adicionar testes de integração -- Tests/Features/Products/ -- Verificar ambas as features
6. Configurar metadados OpenAPI -- Features/Products/ -- Documentação

### Perguntas em aberto
- A busca deve ser full-text (PostgreSQL tsvector) ou LIKE simples?
- Produtos precisam de categorias ou tags para os filtros?

### Riscos
- Migração pode conflitar com outras branches em andamento — verificar antes de aplicar.

Este plano parece certo, ou devo ajustar alguma coisa?
```


---

## Etapas do Desenvolvimento de Software: Planejamento

https://www.gov.br/anpd/pt-br/acesso-a-informacao/acoes-e-programas/governanca/comite-governanca-digital/comite-de-governanca-digital-1/ano-2025/documento-processo-de-desenvolvimento-de-software.pdf

### Reunião de Kick-off
Compreender a necessidade do negócio e alinhar diretrizes. Identificar a necessidade de negócio, pactuar a priorização das entregas, apresentar custos, apresentar a equipe do projeto.
Entrada: Manifestação do Cliente
Saída: Ordem de Serviço 
### Mapear Processo de Negócio
Mapear o Processo de Negócio junto ao cliente e definir a priorização das funcionalidades. Definir a meta do Produto, estabelecer critérios de aceitação, mapear o processo, identificar a liberação dos incrementos para maximizar valor
Entrada: Ordem de Serviço
Saída: Mapeamento do Processo de Negócio
### Construir Visão do Produto
Concentrar-se nas condições do produto quando completo, projetando
necessidades, expectativas e objetivos do cliente
Entrada: Mapeamento do Processo de Negócio
Saída: Documento de Visão.
### Validar Visão do Produto
Analisar se a visão do projeto está coerente e se os prazos atendem às
necessidades do cliente.
Validar a visão do produto, pactuar as entregas de acordo com o Docu-
mento de Visão.
Entrada: Documento de Visão
Saída: Roadmap do Produto
### Criar Backlog do Produto
Listar de forma emergente e ordenada o que é necessário para desenvol-
ver e melhorar o produto. Descrever histórias de usuário, definir prioridades, estabelecer critérios
de aceitação.
Entrada: Roadmap do Produto.
Saída: Backlog do Produto.
### Sprint Planning
Planejar as Sprints alinhadas à meta do Produto, seguindo as prioridades
definidas na visão. Definir tarefas das Sprints, selecionar itens do Backlog, estimar horas de
desenvolvimento.
Entrada: Backlog do Produto.
Saída: Backlog da Sprint.

## Etapas do Desenvolvimento de Software: Desenvolvimento

### Daily Scrum
Permitir interação diária entre os desenvolvedores para analisar e acompanhar o progresso da Sprint, conforme a meta. Identificar impedimentos, inspecionar o progresso, adaptar o Sprint Backlog, se necessário.
Entrada: Backlog da Sprint.
Saída: Impedimentos reportados (caso existam).
### Executar Iteração
Construir e entregar um incremento de software das funcionalidades e outros requisitos listados nos itens do Backlog do Produto, transformando os itens do Backlog da Sprint em uma versão funcional para o cliente. Interação contínua com o Scrum team, gerar e revisar código-fonte, deploy dos ambientes, entregar um incremento pronto ao final da Sprint.
Entrada: Backlog da Sprint.
Saída: Incremento do Produto, Código-fonte.
### Realizar Testes
Realizar testes das funcionalidades nos ambientes correspondentes e evidenciá-los conforme os artefatos estabelecidos na MDSa FBN. Realizar testes das funcionalidades nos ambientes de testes, evidenciar a realização dos testes.
Entrada: Incremento do Produto.
Saída: Evidências de Testes.

## Etapas do Desenvolvimento de Software: Entrega

### Sprint Review
Apresentar o incremento finalizado ao cliente e averiguar a adoção de novas práticas para aumentar a qualidade das próximas entregas. Apresentar os resultados das Sprints, mostrar funcionalidade do incremento no sistema, identificar novas oportunidades de melhorias para as
próximas Sprints.
Entrada: Incremento do Produto.
Saída: Relatório de reunião ou ata com decisões tomadas.
### Refinar Backlog do Produto
O refinamento do Backlog do Produto pode ocorrer a qualquer momento durante a execução do projeto. Identificar melhorias no sistema, analisar possíveis falhas, atualizar as novas histórias conforme o progresso do desenvolvimento
Entrada: Backlog do Produto
Saída: Backlog do Produto Refinado
### Sprint Retrospective
Avaliar os possíveis impedimentos identificados ao longo das Sprints e discutir melhorias para as próximas iterações. Analisar junto à equipe as melhores práticas a serem adotadas nas próximas Sprints, identificar ”GAPs”que possam comprometer o resultado da meta da Sprint.
Entrada: Backlog do Produto Refinado
Saída: Sprint Planning
