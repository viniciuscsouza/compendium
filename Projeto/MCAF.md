
https://mcaf.managed-code.com/


## Conteúdo (Rascunho)

1. 1. O que é o MCAF

A MCAF é uma estrutura para a construção de produtos de software em conjunto com agentes de codificação de IA.

Ele define como:

    manter todo o contexto relevante em um único repositório
    descrever o trabalho claramente antes de codificar
    usar testes de integração/API/UI, ambientes contentorizados e análise estática como portas duras
    codificar regras específicas do repositório para agentes de IA em AGENTS.mdna raiz de repo

O objetivo do MCAF:

    Use a IA para criar produtos reais de uma maneira previsível, segura e repetível.

A MCAF tem três elementos principais:

    Contexto — código, testes, documentação e AGENTS.mdviver juntos no repositório.
    Verificação — comportamento e qualidade de código são comprovados por testes automatizados e análise estática, não opiniões.
    Instruções — AGENTS.mddefine como os agentes de IA funcionam neste repositório e como eles aprendem com o feedback.

Este guia define o enquadramento.
A raiz AGENTS.mdem cada repositório aplica-o a essa base de código.
2. 2. Contexto

O contexto é tudo o que é necessário para entender, alterar e executar o sistema.
O MCAF exige que os seres humanos e os agentes trabalhem do mesmo contexto armazenado no repositório.
2.1 Definição

No MCAF, o contexto do repositório inclui:

    código da aplicação
    testes automatizados (unidade, integração, API, UI/E2E)
    documentação para recursos, arquitetura, testes, desenvolvimento e operações
    raiz do repositório AGENTS.md

Qualquer coisa que importe para desenvolvimento, teste ou operações vive no repositório.
2.2 Layout de documentação

Um típico docs/layout:

    docs/Features/
    Descrições de recursos, fluxos de usuário, regras de negócios, Definição de Concluído, diagramas, fluxos de teste.

    docs/ADR/
    Registros de Decisão de Arquitetura: contexto, opções, decisão, consequências, links para recursos e código.

    docs/API/
    Endpoints públicos, modelos de solicitação/resposta, formatos de erro, regras de versionamento.

    docs/Architecture/
    Diagramas de sistema e módulo, limites, implementação e visualizações de tempo de execução.

    docs/Testing/
    Estratégia de teste, níveis, metas de cobertura, ambientes de teste, como executar cada suíte.

    docs/Development/
    Configuração local, ferramentas, comandos padrão, práticas de ramificação e revisão.

    docs/Operations/
    Implantação, monitoramento, alerta, tratamento de incidentes.

    docs/Home.md
    Ponto de entrada com links para os documentos e modelos mais importantes.

Esta estrutura é uma referência. Um repositório pode adaptar nomes de diretórios, mas mantém lugares claros para recursos, decisões, testes, desenvolvimento e operações.
2.3 Documentos de características

Cada recurso não trivial tem um documento abaixo docs/Features/que inclui:

    característica nome e finalidade
    regras e restrições de negócios
    principais fluxos e casos de borda
    pelo menos um diagrama (por exemplo, Sereia) que mostra o fluxo ou interação principal
    fluxos de ensaio:
        quais cenários são testados
        quais dados / estado são necessários
        resultado esperado para cada fluxo
    Definição de Done:
        condições exatas sob as quais a característica é considerada completa

Os documentos do recurso são escritos com precisão suficiente para:

    um humano pode implementar e verificar o recurso de ponta a ponta
    um agente de IA pode derivar código e testes diretamente da descrição sem inventar o comportamento

2.4 Ligação e referências

Ligações de documentação para:

    outros documentos (Características, ADR, Testes, Arquitetura, Operações)
    elementos de código específicos (arquivos, classes, métodos, módulos)
    diagramas que mostram fluxos, dados ou estrutura
    artigos externos, padrões ou especificações que explicam padrões ou decisões

Os links facilitam a navegação:

    de recurso → testes → código → ADR
    de incidente → operações doc → implementação subjacente

2.5 Regras rígidas para o contexto

    Todas as informações que importam para entender, alterar ou executar o sistema vivem no repositório.
    Cada recurso não trivial tem um doc de recursos antes do início da codificação pesada.
    Cada doc de recurso inclui fluxos de teste e uma definição clara de Done.
    Os médicos são escritos em inglês.
    Os documentos podem fazer referência a outros documentos, código, diagramas e recursos externos relevantes.

3. Verificação

Verificação é como a equipe prova que o comportamento e a qualidade do código atendem às expectativas.
Sob MCAF, testes e análise estática são os principais tomadores de decisão.
3.1 Níveis de teste e cobertura

A MCAF utiliza vários níveis de testes:

    Testes de unidade
    Funções e algoritmos puros, sem E/S. Usado para lógica complexa que é difícil de cobrir através de testes de nível superior.

    Testes de integração
    Componentes trabalhando em conjunto com serviços de apoio reais: bancos de dados, filas, caches, serviços internos.

    Testes de API
    Endpoints públicos exercitados sobre HTTP ou equivalente, tocando em serviços e armazenamento reais.

    Testes de IU / E2E
    O usuário completo flui através do navegador, dispositivo móvel ou desktop, atingindo o back-end real.

Expectativas de cobertura:

    Cada característica significativa ou comportamento funcional tem testes suficientes para cobrir seus possíveis casos; no mínimo, um teste de nível de integração para o fluxo de núcleo.
    Se o comportamento for exposto via API, cada endpoint público tem pelo menos um teste de API; endpoints complexos têm testes para diferentes variações de entrada e condições de erro.
    Os testes de API e integração devem exercer fluxos reais de ponta a ponta, não apenas chamar os endpoints isoladamente; os testes verificam se os componentes funcionam juntos corretamente.
    Se o comportamento é visível para os usuários através da interface do usuário, há pelo menos um teste de interface do usuário / E2E para ele; fluxos críticos de usuários têm testes para caminhos principais e alternativos.
    Testes de unidade são adicionados quando a lógica interna é complexa, crítica ou sensível ao desempenho.
    O objetivo não é “um teste por recurso”, mas “testes suficientes para ter confiança no comportamento”; um é o mínimo, não o alvo.

Cobertura de código:

    A cobertura de código é medida e rastreada para ver qual funcionalidade é realmente testada.
    Relatórios de cobertura mostram quais funções, ramos e fluxos são exercidos por testes – e quais não são.
    Relatórios de cobertura são gerados como parte do CI ou sob demanda.
    A baixa cobertura em módulos críticos aciona revisão e planejamento de testes.
    A cobertura é uma ferramenta para encontrar lacunas, não um alvo para o jogo; 100% de cobertura com afirmações fracas é pior do que 70% de cobertura com testes significativos.

Qualidade do teste:

    Cada teste verifica um fluxo ou cenário real, não apenas que uma função pode ser chamada.
    Testes sem afirmações significativas são proibidos; um teste que apenas chama código sem verificar resultados não é um teste válido.
    Testes verificam comportamento e resultados, não detalhes de implementação.

Os testes cobrem:

    fluxos positivos (caminhos felizes)
    fluxos negativos (falhas de validação, ações proibidas, condições de erro)
    casos de borda (limites, limites, grandes entradas, comportamento sensível ao tempo) quando relevante

3.2 Ambientes contentorizados

Testes de integração/API/UI são executados contra infraestrutura reproduzível.

    As dependências internas (bancos de dados, filas, caches, serviços internos) são executadas em contêineres (por exemplo, Docker Compose) ou configurações de script equivalentes definidas no repositório.
    O ambiente de teste pode ser iniciado a partir do repositório usando scripts documentados ou configuração; sem etapas manuais ocultas.
    Os mesmos comandos de teste funcionam em uma máquina de desenvolvedor e em CI.

Se uma dependência interna não puder ser executada razoavelmente em um contêiner de teste ou instância local, isso é tratado e documentado como um cheiro arquitetônico.
3.3 Análise estática

Analisadores e linters estáticos impõem uma linha de base consistente de qualidade de código.

    As configurações do analisador vivem no repositório e são versionadas com o código.
    Um comando de console padrão executa analisadores; ele está documentado em AGENTS.mde docs/Development/.
    O CI executa analisadores em filiais relevantes e pull requests.

O novo código não introduz novas violações sem justificativa explícita e revisão.
Problemas de analisador recorrentes (APIs inseguras, padrões ruins) levam a atualizações em AGENTS.mde/ou ADRs.
3.4 Dependências externas, simulações e falsificações

Mocks e fakes são fortemente restritos no MCAF.

Para sistemas internos (bases de dados, filas, caches, serviços internos):

    As suítes de teste primária não usam simulações ou falsificações.
    Esses sistemas são exercidos através de contêineres reais ou instâncias de teste.

Para sistemas externos de terceiros (gateways de pagamento, provedores de SMS, APIs externas):

    A substituição é usada apenas quando eles não podem ser executados de forma realista em um ambiente de teste ou sandbox.
    Quando substituídos, sandboxes oficiais ou contas de teste são preferidas.
    Quando sandboxes não estão disponíveis, serviços falsos dedicados são definidos no repositório.

Ao usar falsificações ou simulações para sistemas externos:

    APIs falsas/zombadas correspondem realisticamente à superfície real da API (endpoints, métodos, campos).
    Fakes pode produzir dados realistas e condições de erro realistas.
    Definições de API falsas/zombadas são atualizadas quando os contratos externos mudam.

O uso excessivo de simulações é tratado como um cheiro de teste e desencadeia a refatoração ou revisitação da arquitetura e da estratégia de teste.
3.5 Regras rígidas para a verificação

    O comportamento novo e alterado é comprovado com testes automatizados.
    O comportamento importante é validado através de testes de integração/API/UI, não apenas por testes unitários.
    Sistemas internos são exercidos contra contêineres reais ou instâncias de teste em suítes primárias; eles não são ridicularizados lá.
    Mocks e fakes são usados apenas para sistemas externos que não podem ser executados razoavelmente em testes, e eles correspondem realisticamente à API e ao comportamento reais.
    Analisadores estáticos são executados como parte da Definição de Concluído.
    Testes ou analisadores de falha bloqueiam a conclusão de uma tarefa.

4. 4. Instruções e AGENTS.md

As instruções definem como os agentes de codificação de IA se comportam no repositório e como aprendem ao longo do tempo.
Vivem principalmente em AGENTS.md.
4.1 Papel do AGENTS.md

A raiz AGENTS.mdfica ao lado deste Guia no repositório.

define:

    como os agentes de codificação de IA funcionam nesta base de código
    quais comandos eles executam (construir, testar, formatar, analisar)
    como eles aprendem com o feedback e padrões de código
    regras de codificação, disciplina de teste e definição de feito específico para este repositório
    preferências do mantenedor e escolhas de estilo

Este guia define o enquadramento.
A raiz AGENTS.mdaplica-o a este repositório.
4.2 Conteúdo obrigatório de AGENTS.md

Em um repositório que usa MCAF, a raiz AGENTS.mdmantém-se atualizado com:

    regras de auto-aprendizagem: como extrair padrões de feedback e histórico de código
    fluxo de desenvolvimento: agentes de etapas de alto nível seguem ao alterar o código
    disciplina de testes: quais testes executar (novos, relacionados, cheios) e em qual ordem
    regras de codificação: restrições importantes, padrões e anti-padrões
    comandos: canônico build, test, format, analyzecomandos
    preferências do mantenedor: nomeação, formatação, tom, estilo de explicação

local AGENTS.mdarquivos em subdiretórios refinam essas regras para áreas específicas quando necessário.
4.3 Auto-aprendizagem

AGENTS.mddescreve como os agentes:

    reconhecer o feedback que deve se tornar uma regra
    decidir escopo (local vs global) para novas regras
    atualizar ou substituir as regras existentes quando elas entram em conflito

Categorias de feedback:

    directiva (deve fazer / não deve fazer)
    preferência (gostos/dislikes, verbosidade, estilo)
    avaliação (bom/ruim, útil/inútil, limpo/bagunçado)
    processo (workflow, Definição de Concluído, “é assim que implantamos/testamos”)
    correção (explícito “isso é errado, nunca mais faça isso”)
    emocional (raiva, sarcasmo, agressão passiva sinalizando questões sérias)
    padrão (recuo recorrente entre as tarefas)

Conversas não são memória. Padrões estáveis são escritos em AGENTS.mdou docs.
4.4 Comandos

AGENTS.mdlista os comandos canônicos para este repositório, por exemplo:

    build: construir a solução
    test: executar testes (com notas em suítes focadas vs completas)
    format: executar formater de código

Os agentes e a automação usam esses comandos em vez de sequências de comandos ad-hoc.
4.5 AGENTES Locais.md

Em grandes repositórios, os diretórios podem ter o seu próprio AGENTS.mdficheiros. Eles:

    refinar regras para essa área (por exemplo, IU vs backend vs infraestrutura)
    adicionar requisitos mais rigorosos sem contradizer os princípios da MCAF
    aplicar a arquivos nesse diretório e seus subdiretórios

4.6 AGENTS.md governança

AGENTS.mdé um documento crítico que molda como os agentes de IA trabalham no repositório. Mudanças nele afetam todo o desenvolvimento futuro assistido por IA.

Aprovação de alteração:

    Mudanças na raiz AGENTS.mdexigir revisão e aprovação por um proprietário designado ou mantenedor de leads.
    O proprietário de AGENTS.mdé definido no próprio documento ou em CODEOWNERS.
    Agentes de IA podem propor alterações para AGENTS.md, mas os humanos aprovam e fundem-nos.
    Mudanças significativas de regras são discutidas com a equipe antes de se fundir.

Critérios de revisão para AGENTS.mdalterações:

    A mudança está alinhada com os princípios da MCAF.
    A regra é clara e acionável.
    A regra não contradiz as regras existentes sem substituição explícita.
    A regra reflete um padrão estável, não uma preferência única.

4.7 Regras rígidas para Instruções

    Todo repositório que usa o MCAF tem uma raiz AGENTS.md.
    Raiz AGENTS.mdestá em inglês e alinhado com este Guia.
    Agentes lidos AGENTS.mde documentos relevantes antes de editar código.
    Padrões e lições estáveis são registrados em AGENTS.mdou docs; chat sozinho não é memória.
    As instruções de automação e agente dependem apenas de documentados build, test, format, e analyzecomandos.

5. Codificação e Testabilidade

Existem regras de codificação no MCAF para tornar os testes de integração/API/UI e a análise estática eficazes e sustentáveis.
5.1 Finalidade

Estrutura e estilo do código:

    apoiar testes realistas de ponta a ponta
    manter os analisadores estáticos úteis e gerenciáveis
    evitar padrões que bloqueiam ou enfraquecem os testes

5.2 Constantes e configuração

Literais significativos não são espalhados pela base de código.

Exemplos:

    URLs e caminhos
    chaves, identificadores, tokens
    strings de status e mensagens importantes
    limiares numéricos, limites, códigos de erro

Valores como estes:

    são extraídos em constantes nomeadas, enums, objetos de configuração ou tipos dedicados
    ter uma única fonte de verdade
    são reutilizados tanto em testes quanto em código de produção
    não são copiadas como novas duplicatas codificadas de valores existentes

5.3 Estrutura e testabilidade

Estrutura de código serve testes de integração/API/UI:

    Os componentes são projetados para que fluxos realistas possam ser exercitados através de interfaces públicas (endpoints de API, manipuladores, filas, interface do usuário).
    A lógica pura vive em unidades pequenas e focadas quando o comportamento interno não é trivial.
    O estado global e os efeitos colaterais ocultos são evitados em favor de dependências explícitas.
    Os limites são explícitos para que os ambientes de teste possam conectar dependências de forma limpa.

Quando um teste é difícil ou impossível de escrever para um comportamento, isso é tratado como um problema de design para resolver, não uma razão para pular testes.
5.4 Relacionamento com mocks e fakes

Mocks e fakes seguem as regras na seção Verificação:

    As suítes de teste primária não zombam de sistemas internos.
    Mocks e fakes para sistemas externos aparecem apenas sob as condições estritas definidas na Verification.

Padrões de codificação que dependem fortemente de serviços internos são tratados como cheiros de design e retrabalho.
5.5 Regras rígidas para codificação e testabilidade

    O código é estruturado para que os testes de integração/API/UI possam exercer um comportamento real.
    Constantes e configurações significativas são centralizadas em vez de duplicadas como valores mágicos.
    Padrões que exigem sistemas internos simulados em testes de núcleo são tratados como problemas para corrigir, não práticas para copiar.
    O comportamento difícil de testar é tratado como uma questão de design para resolver, não como justificativa para pular ou enfraquecer os testes.

6. Perspectivas

O MCAF descreve responsabilidades usando quatro perspectivas. Uma pessoa pode jogar várias perspectivas ao mesmo tempo.
Títulos não importam; responsabilidades são.
6.1 Produto

Responsabilizado pelo que o sistema faz e por quê.

Responsabilidades:

    escrever e manter documentos de recursos com cenários, regras e Definição de Concluído
    garantir que as características sejam descritas antes que a codificação pesada comece
    docs de recursos de link para ADRs, testes e código
    usar agentes de IA para rascunhos; revisar significado e escopo de negócios

6,2 Dev

Responsabilizado por como o sistema é construído.

Responsabilidades:

    escrever e manter ADRs para decisões técnicas significativas
    definir e manter construir, testar, formatar e analisar comandos
    manter raiz e, se necessário, local AGENTS.mdficheiros
    escolher o modo de participação da IA por tarefa (delegada, colaborativa, consultiva)
    revisão diffs e próprias decisões de fusão

6.3 QA

Responsabilizável pela forma como o comportamento é verificado.

Responsabilidades:

    escrever e manter a documentação do caso de teste com etapas e resultados esperados
    ambientes de teste de projeto com Dev (contêineres, dados, estratégia de reset)
    garantir que o comportamento crítico seja apoiado por testes de integração/API/UI
    validar que os testes correspondem a documentos de recursos e ADRs

6.4 Agente de IA

Responsável pela geração e adaptação dentro das regras.

Responsabilidades:

    Leia raiz e local AGENTS.mde documentos relevantes antes de editar código
    seguir o fluxo de desenvolvimento do repositório e testar a disciplina
    ajudar a elaborar documentos de recursos, ADRs e especificações de teste
    executar comandos documentados (construir, testar, formatar, analisar)
    propor atualizações para AGENTS.mdquando padrões estáveis aparecem
    fazer perguntas concretas quando faltar informação ou contraditória

O Agente de IA não aprova nem mescla alterações.
Os mantenedores humanos tomam a decisão final.
7. Ciclo de Desenvolvimento

O ciclo de desenvolvimento descreve como uma mudança se move de ideia para código mesclado sob MCAF.
É construído em torno de testes e análise estática, não apenas “código de escrita”.
7.1 Descrever

Antes da codificação:

    Atualizações de produtos ou criação de documentação de recursos.
    O Dev atualiza ou cria ADRs se a arquitetura for alterada.
    Atualizações de QA ou cria documentação de teste para o novo comportamento.
    O Agente de IA pode elaborar conteúdo; os seres humanos validam e finalizam.

Saída:

    uma característica doc com comportamento e fluxos de teste
    ADRs para mudanças arquitetônicas ou de trade-off
    uma clara Definição de Feito para este trabalho

7.2 Plano

Para tarefas não triviais:

    Agente propõe um plano que inclui:
        arquivos para alterar
        testes para adicionar ou atualizar (positivo, negativo, fluxos de borda, integração/API/UI)
        docs para modificar
    Engenheiro ajusta e aceita o plano.
    O plano é registrado (edição, documento ou descrição de solicitação de mesclagem).

7.3 Implementar testes e código

    Adicione ou atualize testes que correspondam aos fluxos de teste documentados, com foco na integração/API/UI sempre que possível.
    Implementar código até que esses testes passem.
    Mantenha as mudanças pequenas e revisáveis.
    Siga as regras de codificação e testabilidade deste Guia e do repositório AGENTS.md.

No MCAF, testes e código se movem juntos; uma tarefa não é “quase feita” enquanto os testes estão faltando.
7.4 Executar testes em camadas

Testes executados nesta ordem:

    Testes novos e modificados para essa mudança.
    Suites relacionadas para o recurso/módulo/serviço afetado.
    Conjuntos de teste completos necessários para este repositório (unidade, integração, API, UI/E2E conforme definido).

As falhas em qualquer camada são entendidas e fixas, não ignoradas ou silenciadas.
7.5 Executar análise estática

    Execute o padrão analyzecomando para este repositório.
    Revise avisos e erros.
    Corrigir violações ou documentar explicitamente exceções justificadas.
    Reexecute testes direcionados se as correções tocarem o comportamento.

Uma tarefa não está pronta até que os testes e analisadores passem.
7.6 Atualizar documentos e AGENTS.md

Após a implementação e verificação:

    Os documentos de recursos são atualizados para que eles reflitam o comportamento real e os casos de borda.
    Os documentos de teste são atualizados para que correspondam à cobertura e fluxos reais de testes.
    Se o trabalho revelou novos padrões ou erros estáveis:
        AGENTS.mdé atualizado com novas regras ou esclarecimentos
        ADRs são atualizados se a arquitetura ou os padrões foram alterados

Docs e AGENTS.mddescrever o sistema que realmente existe.
7.7 Revisão e fusão

Revisão de humanos:

    código e teste diffs
    alterações de documentação
    resultados do teste e análise

Uma mudança é mesclada quando:

    Os princípios da MCAF neste Guia foram seguidos
    repositório AGENTS.mdregras são respeitadas
    testes de integração/API/UI necessários e testes unitários (quando presentes) são verdes
    análise estática passa sem violações não resolvidas

O Agente de IA prepara e atualiza código, testes e documentos.
Os mantenedores são donos da decisão final de fusão.
8. Modos de Participação da IA

Para cada tarefa, a equipe escolhe como o Agente de IA participa.
8.1 Delegado

O agente realiza a maior parte do ciclo de desenvolvimento:

    leituras docs e AGENTS.md
    propõe um plano
    gravações ou atualizações de testes
    implementa código
    executa testes e analisadores
    atualizações docs e propõe AGENTS.mdmudanças

Humanos revisam e decidem sobre a fusão.

Usado para:

    áreas bem compreendidas
    características claramente descritas
    correções de bugs com reprodução conhecida
    refatoração de rotina

8.2 Colaborativo

O agente e os humanos trabalham de perto ao longo da tarefa:

    agentes elabora projetos, código, testes e documentos
    humanos direcionam arquitetura, escopo e decisões-chave continuamente

Usado para:

    características complexas
    mudanças arquitetônicas significativas
    modificações transversais ou de alto risco

8.3 Consultoria

O agente se concentra na análise e explicação:

    lê código e docs
    explica o comportamento atual e o impacto das mudanças
    sugere desenhos alternativos e trade-offs

Os seres humanos implementam código e testes.

Usado para:

    onboarding para uma base de código
    explorando opções de design
    trabalho sensível à segurança ou com conformidade pesada

9. Adotando o MCAF em um repositório

Para adotar o MCAF em um repositório:

    A docs/diretório existe com pelo menos Features/, ADR/, Testing, e Development.
    Este guia e uma raiz AGENTS.mdao vivo na raiz do repositório e são mantidos atualizados.
    Comandos para build, test, format, e analyzesão definidos e documentados.
    Ambientes containerizados ou com script existem para testes de integração/API/UI.
    Os analisadores estáticos são configurados e tratados como parte da Definição de Feito.
    Mudanças significativas seguem o ciclo de desenvolvimento do MCAF:
        docs primeiro
        plano explícito
        testes e código em conjunto
        corridas de teste em camadas
        análise estática
        documentos atualizados e AGENTS.md
        revisão humana e fusão

O MCAF é considerado ativo apenas quando essas práticas são seguidas no dia-a-dia do trabalho, não apenas escritas.
10. Propriedade e Processo
10.1 Propriedade

Cada recurso, documento e decisão significativo tem um proprietário responsável:

    Documentos de recursos — de propriedade do proprietário do recurso (Perspectiva do produto).
    ADRs — propriedade da pessoa que tomou a decisão.
    Documentos de teste – de propriedade da QA ou do proprietário do recurso.
    AGENTS.md— ver regras de governação na secção 4.6.

10.2 Processo

    Onboarding : Novos membros da equipe leem este Guia, a raiz AGENTS.md, e documentos-chave antes de fazer alterações.
    Revisão regular : A equipe revisa periodicamente AGENTS.mde docs para garantir que eles refletem as práticas atuais.
    Loops de feedback : Problemas com o comportamento do agente de IA são rastreados e levam a AGENTS.mdou atualizações do doc, não repetidas correções de bate-papo.
