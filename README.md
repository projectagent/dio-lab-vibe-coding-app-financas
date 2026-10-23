# 💸 App de Organização de Finanças Pessoais com Vibe Coding

Conceito de aplicação web para organização financeira pessoal com entrada conversacional. A pessoa descreve uma movimentação, revisa os dados interpretados e confirma o registro.

Este repositório apresenta o escopo do MVP e o processo de criação com Vibe Coding. O parser demonstrado é simulado; não há integração com um modelo de IA nem com serviços financeiros externos. A arquitetura proposta segue a abordagem local-first: os dados são armazenados no navegador via LocalStorage, sem backend.

## Problema e objetivo

O registro manual e repetitivo pode dificultar a manutenção de um controle financeiro. O projeto explora uma experiência conversacional que simplifica esse processo e mantém a pessoa no controle, permitindo revisar os dados antes de salvar cada transação.

## Escopo do MVP

O MVP foi concebido para contemplar:

- **Entrada conversacional:** interpretar frases como “Gastei 45 no iFood no crédito” e apresentar os dados extraídos para confirmação: tipo, valor, categoria, conta, descrição e data.
- **Transações:** registrar receitas e despesas e agrupar compras parceladas por `installment_group_id`.
- **Dashboard:** apresentar um resumo de saldo, receitas e despesas, além da distribuição das despesas por categoria.
- **Cartões de crédito:** organizar datas de fechamento e vencimento, fatura do ciclo e limite disponível, considerando as compras parceladas futuras.
- **Contas e reservas:** manter separados o saldo da conta corrente Nubank e os valores guardados em Caixinhas, com uma visão consolidada do patrimônio na instituição.
- **Investimentos:** manter ativos como MXRF11 e BBAS3 em uma área própria, distintos das Caixinhas e do saldo disponível para gastos.
- **Gestão de parcelas:** visualizar compras parceladas em conjunto, antecipar parcelas e excluir transações vinculadas ao mesmo grupo.

## Prompt final (PRD)

```text
Crie uma aplicação web SPA de Controle Financeiro Pessoal com foco em entrada conversacional.

Objetivo:
Facilitar o registro e a consulta de receitas e despesas por meio de linguagem natural. Antes de salvar uma transação, apresente os dados interpretados para revisão e confirmação.

Estilo e navegação:
Crie uma interface moderna, limpa e adequada a um produto financeiro. Organize a navegação pelas áreas Chat, Dashboard, Extrato, Cartões e Contas. Priorize legibilidade, estados claros e responsividade.

Dados e persistência:
Não use backend nem serviços externos. Persista os dados localmente no navegador usando LocalStorage. Cada transação deve conter: id, tipo (receita ou despesa), valor, categoria, conta, descrição, data e installment_group_id, quando fizer parte de uma compra parcelada.

Fluxo conversacional:
Implemente um parser simulado para frases como “Gastei 45 no iFood no crédito”. Extraia os campos possíveis, permita editá-los e apresente um cartão de confirmação antes de salvar. Não descreva o parser como uma integração real com IA.

Telas e funcionalidades:
1. Chat: entrada em linguagem natural, interpretação simulada e confirmação da transação.
2. Dashboard: resumo de saldo, receitas e despesas, com gráfico de despesas por categoria.
3. Extrato: lista pesquisável e filtrável de transações, com opções de edição e exclusão.
4. Cartões: datas de fechamento e vencimento, fatura do ciclo, limite disponível e compras parceladas futuras. Permita antecipar parcelas e excluir em conjunto as transações vinculadas a um installment_group_id.
5. Contas: gerenciamento de contas bancárias. Para o Nubank, mantenha separados o saldo da conta corrente e os valores das Caixinhas, apresentando também o total combinado sem confundir valores reservados com saldo disponível. Mantenha investimentos, como MXRF11 e BBAS3, em uma área distinta das Caixinhas.

Entregue uma experiência funcional para demonstrar o fluxo do MVP, com dados de exemplo quando necessário. Não prometa integração bancária, recomendações financeiras automatizadas nem análise por LLM.
```

## Evidências do processo

Registros das interações com a IA e da evolução do protótipo.

<img width="720" alt="Evidência do processo de criação" src="https://github.com/user-attachments/assets/91126b19-81c8-4222-ae37-0c175b5393c8" />

<img width="720" alt="Evidência de interação com a IA" src="https://github.com/user-attachments/assets/59fed3d0-3d26-493d-aeeb-4ea5336a9ea9" />

<img width="720" alt="Evidência da evolução do projeto" src="https://github.com/user-attachments/assets/0d6d81ad-5c08-46c8-b409-ceb1375130ff" />

<img width="720" alt="Evidência do protótipo" src="https://github.com/user-attachments/assets/826b7410-fd86-4c8f-8779-a249cfef1cdc" />

<img width="720" alt="Evidência da interface final" src="https://github.com/user-attachments/assets/003dbedc-5f1e-4ee6-bfc9-7638983cfefd" />


## Reflexões e aprendizados

- **Engenharia de requisitos:** descrições exclusivamente visuais podem resultar em telas sem comportamentos definidos. Especificar a persistência, os campos e as regras de negócio tornou as instruções mais precisas e orientou melhor a IA.
- **Iteração pontual:** questões específicas, como o recálculo do limite após a exclusão de uma compra parcelada, foram tratadas com instruções focadas, sem reescrever todo o prompt.
- **Consistência financeira:** separar o saldo disponível, os valores das Caixinhas e os investimentos ajuda a não apresentar patrimônio reservado como dinheiro livre para despesas. A definição das datas e dos valores da fatura também faz parte do modelo de gestão dos cartões.
- **Privacidade e limites da solução:** o LocalStorage mantém os dados no navegador, mas não oferece criptografia nem proteção equivalente à de um sistema financeiro. O parser deste MVP é simulado; qualquer integração futura com LLM exigiria uma avaliação específica de privacidade e segurança.

## Próximos passos

Como evolução futura, os fluxos e as regras de parcelamento podem ser validados com pessoas que controlam os gastos manualmente, para avaliar se a entrada conversacional reduz o esforço de registro.

## Abordagem técnica

- **Vibe Coding:** concepção e refinamento do produto com ferramentas de IA, incluindo o Lovable.
- **Persistência proposta:** LocalStorage, sem backend, seguindo a abordagem local-first.
- **Parser:** simulado para demonstrar o fluxo conversacional; não corresponde a uma integração com IA.
