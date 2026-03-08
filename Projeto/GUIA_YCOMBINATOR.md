
# Guia YC para Vibe Coding

## Processo de planejamento
* **Criar um plano abrangente:** Comece trabalhando com a IA para escrever um plano de implementação detalhado em um arquivo markdown.
* **Revisar e refinar:** Apague itens desnecessários e marque recursos como "não fazer" se forem muito complexos.
* **Manter controle de escopo:** Mantenha uma seção separada para ideias futuras para manter o foco.
* **Implementar incrementalmente:** Trabalhe seção por seção em vez de tentar construir tudo de uma vez.
* **Acompanhar o progresso:** Peça para a IA marcar as seções como concluídas após uma implementação bem-sucedida.
* **Fazer commits regulares:** Garanta que cada seção funcional seja commitada no Git antes de passar para a próxima.

## Estratégias de controle de versão
* **Usar Git religiosamente:** Não confie apenas na funcionalidade de "reverter" das ferramentas de IA.
* **Começar limpo:** Inicie cada nova feature com um estado limpo no Git.
* **Resetar quando travar:** Use `git reset --hard HEAD` se a IA entrar em um caminho sem saída ("vision quest").
* **Evitar problemas acumulados:** Múltiplas tentativas falhas criam camadas e camadas de código ruim.
* **Implementação limpa:** Quando finalmente encontrar uma solução, resete e implemente-a de forma limpa.

## Framework de testes
* **Priorizar testes de alto nível:** Foque em testes de integração ponta a ponta (end-to-end) em vez de testes unitários.
* **Simular comportamento do usuário:** Teste recursos simulando alguém clicando pelo site/app.
* **Capturar regressões:** LLMs frequentemente fazem alterações desnecessárias em lógicas não relacionadas.
* **Testar antes de prosseguir:** Garanta que os testes passem antes de mover para a próxima feature.
* **Usar testes como guardrails (proteção):** Alguns fundadores recomendam começar com casos de teste para fornecer limites claros.

## Correção de bugs eficaz
* **Aproveitar mensagens de erro:** Simplesmente copiar e colar mensagens de erro geralmente é suficiente para a IA.
* **Analisar antes de codificar:** Peça à IA para considerar múltiplas causas possíveis.
* **Resetar após falhas:** Comece com um estado limpo após cada tentativa de correção malsucedida.
* **Implementar logs:** Adicione logs estratégicos para entender melhor o que está acontecendo.
* **Trocar de modelos:** Tente modelos de IA diferentes quando um ficar travado.
* **Implementação limpa:** Assim que identificar a correção, resete e implemente-a em uma base de código limpa.

---

## Otimização de ferramentas de IA
* **Criar arquivos de instrução:** Escreva instruções detalhadas para sua IA nos arquivos apropriados (`cursor.rules`, `windsurf.rules`, `claude.md`).
* **Documentação local:** Baixe a documentação da API para a pasta do seu projeto para maior precisão.
* **Usar múltiplas ferramentas:** Alguns fundadores rodam o Cursor e o Windsurf simultaneamente no mesmo projeto.
* **Especialização da ferramenta:** O Cursor é um pouco mais rápido para frontend, enquanto o Windsurf "pensa" por mais tempo.
* **Comparar saídas:** Gere múltiplas soluções e escolha a melhor.

## Desenvolvimento de features complexas
* **Criar protótipos independentes:** Construa features complexas em uma base de código limpa primeiro.
* **Usar implementações de referência:** Aponte para a IA exemplos funcionais para seguir.
* **Limites claros:** Mantenha APIs externas consistentes enquanto permite mudanças internas.
* **Arquitetura modular:** Arquiteturas baseadas em serviços com limites claros funcionam melhor do que monorepos.

## Considerações sobre Tech Stack
* **Frameworks estabelecidos se destacam:** Ruby on Rails funciona bem devido a 20 anos de convenções consistentes.
* **Dados de treinamento importam:** Linguagens mais novas como Rust ou Elixir podem ter menos dados de treinamento.
* **Modularidade é chave:** Arquivos pequenos e modulares são mais fáceis de trabalhar tanto para humanos quanto para IAs.
* **Evitar arquivos grandes:** Não tenha arquivos com milhares de linhas.

## Além do código
* **Automação DevOps:** Use IA para configurar servidores, DNS e hospedagem.
* **Assistência de design:** Gere favicons e outros elementos de design.
* **Criação de conteúdo:** Rascunhe documentação e materiais de marketing.
* **Ferramenta educacional:** Peça à IA para explicar implementações linha por linha.
* **Usar capturas de tela:** Compartilhe bugs de UI ou inspirações de design visualmente.
* **Entrada de voz:** Ferramentas como Aqua permitem entrada de 140 palavras por minuto.

## Melhoria contínua
* **Refatoração regular:** Uma vez que os testes estejam no lugar, refatore frequentemente.
* **Identificar oportunidades:** Peça à IA para encontrar candidatos para refatoração.
* **Manter-se atualizado:** Experimente cada lançamento de novo modelo.
* **Reconhecer pontos fortes:** Diferentes modelos se destacam em tarefas diferentes.

---

## Dcas para aproveitar ao máximo o *vibe coding* e as ferramentas de IA:

**Dicas de Fluxo de Trabalho e Ferramentas:**

*   **Pense na IA como uma Linguagem de Programação:** Considere a IA como um tipo diferente de linguagem de programação, onde você programa com a linguagem em vez de código.
*   **Forneça Contexto Detalhado:** É necessário fornecer muito contexto e informação necessária de forma detalhada para obter bons resultados.
*   **Monitore "Buracos de Coelho" (Rabbit Holes):** Monitore se o LLM está caindo em um ciclo vicioso de regeneração de código estranho ou se você precisa copiar e colar mensagens de erro constantemente.
*   **Pare e Examine a Falha:** Se o LLM estiver preso em um "buraco de coelho", dê um passo para trás e peça explicitamente ao LLM para examinar por que está falhando (por falta de contexto ou azar).
*   **Comece com Escopo e Arquitetura:** Gaste uma quantidade de tempo "não razoável" em um LLM puro para definir o escopo e a arquitetura do que você está construindo antes de transferir a tarefa para ferramentas de codificação como o Cursor.
*   **Use Múltiplas Ferramentas:** Carregue ferramentas como Cursor e Windsurf simultaneamente no mesmo projeto. O Cursor é mais rápido para tarefas de front-end ou full-stack.
*   **Use a UI do LLM Diretamente:** Se o ID de IA ficar preso em um loop sem conseguir implementar ou depurar algo, copie e cole o código e a pergunta no site (UI) do LLM para tentar obter o resultado.
*   **Aproveite o Tempo de Espera:** Enquanto espera o Windsurf pensar (o que leva mais tempo), use o Cursor para atualizar o front-end.
*   **Compare Iterações:** Carregue as duas ferramentas ao mesmo tempo para o mesmo contexto (por exemplo, atualizar o front-end com o estilo de um arquivo) e use as diferentes iterações geradas para escolher a melhor.
*   **Escolha a Ferramenta Certa para o Nível de Experiência:** Se você nunca escreveu código, use ferramentas como Replet ou Lovable, que oferecem uma interface visual fácil. Se você já codificou (mesmo que enferrujado), vá direto para ferramentas como Windsurf, Cursor ou Claude Code.
*   **Priorize um Bom Stack:** Considere stacks como Ruby on Rails, que tem convenções bem estabelecidas e consistência, o que facilita o desempenho da IA devido à grande quantidade de dados de treinamento de alta qualidade.

**Dicas de Planejamento e Estrutura:**

*   **Desenvolva um Plano Abrangente com a IA:** O primeiro passo é trabalhar com o LLM para escrever um plano abrangente e colocá-lo em um arquivo Markdown dentro da pasta do projeto.
*   **Refine o Rascunho do Plano:** Depois do rascunho inicial, revise o plano, remova ou exclua itens indesejados e marque explicitamente certos recursos como "não fazer" (se forem muito complicados).
*   **Use uma Seção de Ideias Futuras:** Mantenha uma seção de ideias para depois, informando ao LLM que foram consideradas, mas estão fora do escopo por enquanto.
*   **Implemente por Seções:** Trabalhe com o LLM para implementar o plano seção por seção, dizendo explicitamente para fazer apenas uma seção por vez.
*   **Confirme e Monitore o Progresso:** Verifique se cada seção funciona, execute os testes e, em seguida, peça à IA para marcar a seção como completa no plano.
*   **Projetos Complexos em Standalone:** Se estiver trabalhando em uma funcionalidade nova e mais complexa, comece fazendo-a como um projeto autônomo em uma base de código totalmente limpa para obter uma pequena implementação de referência. Em seguida, use essa referência para guiar o LLM na implementação dentro da sua base de código maior.
*   **Mantenha Modularidade:** Lembre-se de que arquivos pequenos e modularidade são benéficos para codificadores humanos e LLMs.

**Dicas de Controle de Versão e Testes:**

*   **Use Controle de Versão de Forma Rigorosa (Git):** Use o Git religiosamente para controle de versão.
*   **Comece com um Estado Limpo:** Comece com um estado limpo do Git antes de iniciar um novo recurso para que possa reverter para uma versão funcional conhecida se a IA falhar.
*   **Não Tenha Medo de Resetar:** Use `git reset --hard` se as coisas não estiverem funcionando e recomece.
*   **Evite Acúmulo de Código Ruim:** Evite solicitar à IA várias vezes para consertar algo, pois isso tende a acumular camadas de código ruim.
*   **Implemente Soluções Limpas:** Se você finalmente encontrar uma solução após várias tentativas, use `git reset`, e em seguida, alimente a solução funcional na IA em uma base de código limpa para implementá-la sem acúmulo de código de má qualidade.
*   **Comece pelo Teste (Reverse Vibe Coding):** Comece o *vibe coding* na direção inversa, primeiro criando manualmente os casos de teste (sem usar LLMs).
*   **Defina Regras Rígidas:** Após criar os casos de teste, estabeleça regras de proteção fortes que os LLMs possam seguir para gerar o código.
*   **Escreva Testes de Alto Nível:** Escreva testes ou peça ao LLM para escrevê-los, mas prefira testes de integração de alto nível que simulem um usuário clicando no site/aplicativo para garantir que as funcionalidades trabalhem de ponta a ponta.
*   **Capture Regressões Cedo:** Mantenha conjuntos de testes para identificar regressões e capturar mudanças desnecessárias feitas pelo LLM em lógica não relacionada.

**Dicas de Debugging:**

*   **Copie a Mensagem de Erro:** Ao encontrar um bug, copie e cole a mensagem de erro (do log do servidor ou console JavaScript) diretamente no LLM, pois isso geralmente é suficiente para que ele identifique e corrija o problema.
*   **Não Acumule Camadas de Erro:** Após cada tentativa de correção de bug que falhar, use `git reset` e comece de novo para evitar o acúmulo de camadas de código defeituoso.
*   **Use Logging:** Se estiver em dúvida ou se o código não estiver funcionando, adicione *logging*.
*   **Peça Análise de Causa Complexa:** Para bugs mais complexos, peça ao LLM para considerar três ou quatro possíveis causas antes de escrever qualquer código.
*   **Troque de Modelo:** Mude o modelo de LLM (por exemplo, de Claude para OpenAI ou Gemini), pois diferentes modelos podem ter sucesso onde outros falham.
*   **Forneça Instruções Específicas após a Descoberta:** Se você encontrar a fonte de um bug complicado, resete todas as mudanças e forneça ao LLM instruções muito específicas sobre como corrigir esse bug em uma base de código limpa.

**Dicas para Otimizar a Interação com o LLM:**

*   **Escreva Instruções Detalhadas:** Escreva instruções abrangentes para o LLM nos arquivos de regras apropriados (por exemplo, regras do Cursor, regras do Windsurf).
*   **Forneça Documentação Local:** Baixe toda a documentação de um conjunto de APIs e coloque-a em um subdiretório para que o LLM possa acessá-la localmente, já que apontar agentes para documentação online ainda é inconsistente.
*   **Instrua o LLM a Ler a Documentação:** Inclua nas instruções um comando para o LLM ler a documentação antes de implementar a tarefa.
*   **Use LLMs como Professor:** Peça ao LLM para percorrer a implementação linha por linha e explicá-la, sendo uma ótima maneira de aprender novas tecnologias.
*   **Use Screenshots:** Copie e cole capturas de tela nos agentes de codificação para demonstrar um bug de UI ou para inspirar o design de outro site.
*   **Use Entrada de Voz:** Use ferramentas de voz (como Aqua) para interagir, pois a transcrição permite que você insira instruções em uma velocidade maior do que digitando (140 palavras por minuto) e a IA é tolerante a erros menores de gramática.
*   **Refatore Frequentemente:** Quando o código estiver funcionando e os testes implementados, refatore à vontade, sabendo que os testes capturarão regressões. Você pode pedir ao LLM para identificar partes repetitivas do código que são boas candidatas à refatoração.
*   **Continue Experimentando:** Continue experimentando novos lançamentos de modelos para ver qual tem melhor desempenho em diferentes cenários (depuração, planejamento de longo prazo, refatoração, etc.).