# Template: Arquitetura do Sistema (ARCHITECTURE.md)

Este documento serve como a fonte da verdade para as decisões arquiteturais de alto nível do projeto.
Agentes de IA devem utilizar este documento para entender como os componentes se comunicam e quais padrões de design adotar.

## 1. Visão Geral da Arquitetura
[Agente: Descreva o padrão arquitetural predominante (ex: Clean Architecture, Hexagonal, MVC, Microsserviços, Monolito Modular). Explique brevemente o porquê dessa escolha.]

## 2. Diagrama de Contexto (Opcional)
[Agente: Se aplicável, inclua uma descrição textual ou um diagrama em formato Mermaid (`mermaid`) ilustrando os principais componentes e atores do sistema.]

## 3. Padrões de Design Aplicados
[Agente: Liste os Design Patterns mais utilizados no projeto (ex: Repository Pattern, Factory, Singleton). Explique onde e como eles devem ser aplicados. Evite listar padrões que não estão ativamente em uso.]

## 4. Gestão de Estado
[Agente: Para aplicações Frontend ou sistemas complexos, defina como o estado da aplicação é gerenciado (ex: Redux, Context API, Zustand, MobX, etc.).]

## 5. Fluxo de Dados (Data Flow)
[Agente: Descreva o caminho que um dado percorre desde a entrada (ex: requisição HTTP ou interação do usuário) até o armazenamento ou resposta. Ex: Controller -> Service -> Repository -> Database.]
