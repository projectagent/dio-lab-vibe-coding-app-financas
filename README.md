# 💸 App de Organização de Finanças Pessoais com Vibe Coding
## Controle Financeiro Pessoal com Vibe Coding

Aplicação web de finanças pessoais pensada para registrar transações por meio de linguagem natural. A proposta reduz o atrito de formulários: a pessoa descreve uma movimentação, confere os dados interpretados e confirma antes de adicioná-la ao controle financeiro.

Este repositório documenta o conceito do MVP e o processo de criação com Vibe Coding. O fluxo de interpretação descrito aqui é simulado; não há integração com um modelo de IA ou serviço financeiro externo. A arquitetura proposta é local-first, com armazenamento no navegador via LocalStorage e sem backend.

## Problema e objetivo

O registro manual e repetitivo pode dificultar a manutenção de um controle financeiro. O objetivo do projeto é explorar uma experiência conversacional simples, mantendo a pessoa no controle dos dados antes de salvar cada transação.

## Escopo do MVP

- **Entrada conversacional:** interpretar frases como “Gastei 45 no iFood no crédito” e apresentar uma confirmação com tipo, valor, categoria, conta, descrição e data.
- **Transações:** registrar receitas e despesas, com suporte a agrupamento de compras parceladas por `installment_group_id`.
- **Dashboard:** resumir saldo, receitas e despesas, além de visualizar despesas por categoria.
- **Cartões de crédito:** organizar fechamento, vencimento, fatura do ciclo e limite disponível, considerando compras parceladas futuras.
- **Contas e reservas:** separar saldo da conta corrente Nubank e valores guardados em Caixinhas, exibindo também o patrimônio total na instituição.
- **Investimentos:** manter ativos como MXRF11 e BBAS3 em uma área própria, separados das Caixinhas e do saldo disponível para gastos.
- **Gestão de parcelas:** permitir visualizar compras parceladas em conjunto, antecipar parcelas e excluir transações de um grupo.

## Prompt final (PRD)

```text
Crie uma aplicação web SPA de Controle Financeiro Pessoal com foco em entrada conversacional.

Objetivo
Facilitar o registro e a consulta de receitas e despesas, permitindo que a pessoa descreva uma movimentação em linguagem natural. Antes de registrar qualquer transação, apresente os dados interpretados para confirmação.

Estilo e navegação
Use uma interface moderna, limpa e adequada a um produto financeiro. Organize a navegação pelas áreas Chat, Dashboard, Extrato, Cartões e Contas. Priorize legibilidade, estados claros e uso responsivo.

Dados e persistência
Não use backend nem serviços externos. Persista os dados localmente no navegador usando LocalStorage. Uma transação deve conter: id, tipo (receita ou despesa), valor, categoria, conta, descrição, data e installment_group_id quando fizer parte de uma compra parcelada.

Fluxo conversacional
Implemente um parser simulado para frases como “Gastei 45 no iFood no crédito”. Extraia os campos possíveis, permita a edição dos dados e mostre um card de confirmação antes de salvar. Não apresente o parser como uma integração real com IA.

Telas e funcionalidades
1. Chat: entrada em linguagem natural, interpretação simulada e confirmação da transação.
2. Dashboard: saldo, receitas, despesas e gráfico de despesas por categoria.
3. Extrato: lista pesquisável e filtrável das transações, com edição e exclusão.
4. Cartões: dia de fechamento e vencimento, fatura do ciclo, limite disponível e compras parceladas futuras. Permita antecipar parcelas e excluir em conjunto as transações de um installment_group_id.
5. Contas: permita gerenciar contas bancárias. Para Nubank, separe o saldo da conta corrente das Caixinhas e mostre o total combinado sem confundir o valor guardado com o saldo livre. Mantenha investimentos, como MXRF11 e BBAS3, em uma área distinta das Caixinhas.

Entregue uma experiência funcional para demonstrar o fluxo do MVP, com dados de exemplo quando necessário. Não prometa integração bancária, recomendações financeiras automatizadas ou análise por LLM.
```

## Evidências do processo

Adicione ao repositório capturas reais da criação e das iterações. Crie a pasta `docs/` e coloque nela os arquivos abaixo; então descomente as imagens ou atualize os caminhos.

- `docs/print-prompt-inicial.png`: prompt inicial no Lovable.
- `docs/print-correcao-parcelas.png`: iteração sobre parcelas e limite do cartão.
- `docs/print-interface-final.png`: preview final do protótipo.

<!--
![Prompt inicial no Lovable](docs/print-prompt-inicial.png)
![Iteração sobre parcelas](docs/print-correcao-parcelas.png)
![Preview da interface](docs/print-interface-final.png)
-->

## Reflexões e aprendizados

- **Engenharia de requisitos:** descrições apenas visuais tendem a gerar telas sem comportamento definido. Especificar persistência, campos e regras de negócio ajudou a orientar melhor a IA.
- **Iteração pontual:** problemas como o recálculo do limite após excluir uma compra parcelada foram tratados com instruções focadas, em vez de refazer o prompt inteiro.
- **Separação de saldos:** distinguir saldo disponível, Caixinhas e investimentos evita apresentar patrimônio reservado como dinheiro livre para despesas.
- **Limites da solução:** LocalStorage mantém os dados no navegador, mas não oferece criptografia ou proteção equivalente a um sistema financeiro. O parser deste MVP é simulado; uma integração futura com LLM exigiria avaliação própria de privacidade e segurança.

## Próximos passos

- Substituir as referências de evidência pelas capturas reais do processo.
- Validar os fluxos e as regras de parcelas no protótipo.
- Testar a experiência com pessoas que controlam gastos manualmente e observar se o registro conversacional reduz o esforço.

## Tecnologias e abordagem

- **Vibe Coding:** elaboração e iteração do produto com ferramentas de IA, incluindo Lovable.
- **Persistência proposta:** LocalStorage, sem backend.
- **Parser:** simulado para demonstrar o fluxo conversacional.
