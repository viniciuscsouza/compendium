# Template: Preocupações e Débitos Técnicos (CONCERNS.md)

Este documento lista as áreas sensíveis, vulnerabilidades conhecidas, legados e restrições do projeto.
Agentes de IA devem **sempre** ler este documento antes de refatorar ou modificar códigos antigos para evitar quebrar comportamentos esperados ou reescrever "workarounds" necessários (o Paradoxo de Chesterton).

## 1. Débitos Técnicos Conhecidos
[Agente: Liste as partes do código que estão mal escritas, obsoletas ou que precisam ser refatoradas no futuro, mas que NÃO devem ser tocadas no momento para não gerar instabilidade.]

## 2. Áreas Sensíveis (Fragile Code)
[Agente: Indique os módulos ou arquivos que quebram facilmente. Ao mexer nessas áreas, a IA deve agir com cautela extrema e sugerir testes adicionais.]

## 3. Workarounds Históricos e "Gambiarras" Necessárias
[Agente: Descreva soluções provisórias que foram implementadas por uma boa razão. Se a IA ver aquele código feio, deve saber *por que* ele está lá e evitar tentar "consertar" sem contexto de negócio.]

## 4. Restrições de Performance ou Memória
[Agente: Existem limites estritos (ex: não carregar listas enormes em memória, limite de tamanho de payload, gargalos no banco)? Documente aqui.]
