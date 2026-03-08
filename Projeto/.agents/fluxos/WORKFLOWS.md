# Template: Fluxos de Trabalho e Processos (WORKFLOWS.md)

Este documento centraliza comandos, scripts de uso diário e processos de rotina para interagir com o projeto no ambiente de desenvolvimento.
Agentes de IA devem utilizar este guia para saber como construir, rodar ou depurar a aplicação sem ter que "adivinhar" os comandos.

## 1. Configuração do Ambiente Local (Setup)
[Agente: Documente o passo a passo para um novo desenvolvedor (ou IA) rodar o projeto do zero. Inclui comandos de cópia de `.env`, subida de containers Docker, ou instalação de dependências.]

## 2. Rodando a Aplicação
[Agente: Qual é o script principal para subir o servidor local? (ex: `npm run dev`, `docker-compose up`, `python manage.py runserver`). Especifique as portas e URLs padrão.]

## 3. Scripts Frequentes do `package.json` (ou equivalente)
[Agente: Liste e explique a função dos scripts comuns.
- Ex: `build`: Compila o projeto para prod.
- Ex: `lint:fix`: Roda o linter corrigindo problemas.
- Ex: `db:migrate`: Aplica migrações pendentes.
]

## 4. Fluxo de Git e PRs (Pull Requests)
[Agente: Indique a estratégia de versionamento (ex: GitFlow, Trunk-based) e o formato esperado para as mensagens de Commit (ex: Conventional Commits). Defina o que um PR deve conter para ser aceito.]

## 5. Como Depurar (Debugging Workflow)
[Agente: Dicas sobre como debugar a aplicação localmente. Onde os logs são impressos? Existem rotas ou parâmetros ocultos ativados no modo DEV para auxiliar nos testes?]
