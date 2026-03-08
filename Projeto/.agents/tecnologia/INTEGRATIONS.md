# Template: Integrações Externas e APIs (INTEGRATIONS.md)

Este documento descreve os sistemas, serviços e APIs de terceiros com os quais este projeto se comunica.
Agentes de IA utilizarão esta referência ao construir funcionalidades que necessitam buscar ou enviar dados para fora do sistema.

## 1. Serviços de Terceiros e APIs Externas
[Agente: Liste os serviços utilizados (ex: Stripe, SendGrid, AWS S3, Google Maps API). Para cada um, informe o propósito principal dentro do sistema.]

## 2. Padrões de Comunicação
[Agente: Como o projeto se comunica externamente? (REST, GraphQL, gRPC, Webhooks, Mensageria/Filas). Descreva clientes ou bibliotecas padrão para essas chamadas (ex: Axios, Fetch, SDKs oficiais).]

## 3. Autenticação e Gestão de Chaves
[Agente: Como o sistema se autentica nesses serviços? (OAuth, API Keys no formato Bearer token). Especifique onde essas variáveis de ambiente são carregadas (NÃO coloque chaves reais aqui!).]

## 4. Retentativas (Retries) e Fallbacks
[Agente: Qual é a política quando uma API externa falha ou excede o timeout? Descreva os padrões de retry, circuit breakers ou dados de contingência a serem usados.]

## 5. Webhooks e Recepção de Eventos
[Agente: Se o sistema recebe webhooks, documente os endpoints responsáveis, como as assinaturas (signatures) são validadas e o fluxo de processamento assíncrono.]
