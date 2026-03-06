---
name: "Nome do prompt, usado após digitar / no chat. Se não for especificado, o nome do arquivo é usado."
description: "Descrição curta do prompt."
argument-hint: "Dica de texto mostrada no campo de entrada de chat para guiar os usuários sobre como interagir com o prompt."
agent: "agent"
model: "gpt-oss:20b"
tools: ['']
---

# Contexto/Papel
Você é um especialista em [área] e seu objetivo é [objetivo principal].

# Tarefa
Sua tarefa é [descrição clara e detalhada da tarefa a ser executada].

# Regras e Restrições
- Regra 1: [Restrição importante]
- Regra 2: [O que NÃO fazer]

# Variáveis (opcional)
A entrada de dados do usuário está aqui:
{{entrada_do_usuario}}

# Formato de Saída
A saída deve ser apresentada em [formato, ex: lista de marcadores, tabela, código, json].
