# Template: Regras de Negócio e Domínio (DOMAIN.md)

Este documento traduz a linguagem do negócio para o contexto do software. Ele registra a "Linguagem Ubíqua" e as regras core do produto.
Agentes de IA devem consultar este material para garantir que as soluções propostas resolvam não apenas problemas técnicos, mas que façam sentido comercial e funcional.

## 1. Propósito do Produto (Visão Geral)
[Agente: Qual problema este software resolve? Quem são os usuários finais? Resuma em poucas linhas o core business do projeto.]

## 2. Glossário / Linguagem Ubíqua (Ubiquitous Language)
[Agente: Crie um dicionário com os termos técnicos de negócio. Isso previne que desenvolvedores e a IA usem nomes incorretos no código.
Exemplo: "Usuário: Pode ser um Cliente ou um Administrador." "Carrinho: Onde o Cliente aloja os itens antes do Checkout."]

## 3. Entidades Principais e Relacionamentos
[Agente: Liste as entidades vitais do negócio e como elas se relacionam (ex: Um `Pedido` contém vários `ItensDePedido` e pertence a um `Cliente`). Isso ajuda no desenho de schemas de banco de dados e APIs.]

## 4. Regras de Negócio Fundamentais
[Agente: Descreva restrições lógicas inegociáveis. Exemplo: "Um Cliente não pode cancelar uma assinatura após 7 dias", "O desconto máximo permitido é de 15%". A IA usará isso para criar validações e cenários de teste.]

## 5. Fluxos de Valor / Jornada do Usuário
[Agente: Mapeie os principais caminhos que geram valor. (Ex: "Fluxo de Checkout: O usuário põe no carrinho -> Informa endereço -> Paga via gateway X -> Recebe e-mail").]
