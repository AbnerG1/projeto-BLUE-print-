# Nível 1 — Jornada do usuário | Sistema Desktop de Gestão e Caixa

## Situação escolhida

Imagine um pequeno comércio em um momento de atendimento. O Operador de Caixa precisa registrar os produtos que o cliente está levando, receber o pagamento e concluir a venda sem deixar o estoque desatualizado.

Esta jornada segue o fluxo descrito no estudo de caso do Módulo 01. Como a documentação disponível não confirma todas as telas da versão executável, os pontos de contato abaixo representam o que seria necessário para realizar cada etapa.

## Jornada do Operador de Caixa

| Etapa | O que o operador faz | O que espera do sistema | Dúvida ou dificuldade possível |
|---|---|---|---|
| 1. Acesso | Informa usuário e senha. | Acesso liberado para iniciar o atendimento. | Esquecer os dados ou receber uma mensagem pouco clara. |
| 2. Nova venda | Abre a área de registro de venda. | Encontrar o espaço para incluir os produtos. | Não localizar rapidamente a função de nova venda. |
| 3. Produtos | Informa o código de barras ou identificador de cada produto. | Ver o produto encontrado, seu preço e o valor parcial da compra. | Código não localizado ou quantidade indisponível. |
| 4. Conferência | Repete a inclusão dos itens e pede a totalização. | Conferir a lista e ver o valor final. | Perceber tarde que um item ou uma quantidade está incorreta. |
| 5. Pagamento | Escolhe a forma de pagamento e confirma o valor recebido. | Saber se o valor recebido cobre o total. | O valor informado ser menor que o necessário. |
| 6. Finalização | Conclui a venda e entrega o recibo. | Ter a confirmação da operação, o estoque atualizado e o comprovante. | Não saber se a venda foi realmente registrada. |

## Como o usuário pode se sentir

A satisfação abaixo é uma hipótese para ajudar a visualizar a jornada. Não foi medida em entrevistas ou testes com operadores reais.

| Etapa | Acesso | Nova venda | Produtos | Conferência | Pagamento | Finalização |
|---|---:|---:|---:|---:|---:|---:|
| Satisfação estimada (1 a 5) | 3 | 4 | 3 | 4 | 3 | 5 |

A inclusão dos produtos e o pagamento merecem atenção especial: são momentos em que um erro pode interromper o atendimento ou gerar diferença no estoque.

## Situações que mudam o fluxo

- **Produto não encontrado:** o sistema informa que o identificador não corresponde a um produto cadastrado. O operador confere o código e tenta novamente.
- **Estoque insuficiente:** o sistema avisa que não há quantidade disponível e o item não deve ser adicionado à compra.
- **Pagamento menor que o total:** pela regra RN01, a venda não pode ser finalizada enquanto o valor pago for inferior ao valor registrado.
- **Produto com estoque zerado:** pela regra RN02, ele não pode ser incluído na lista de compras.

## O que poderia melhorar a experiência

Ajudaria bastante se o sistema mantivesse o valor parcial e a quantidade de cada produto sempre visíveis, avisasse o motivo de uma operação não poder continuar e mostrasse uma confirmação clara no fim da venda. No caso do pagamento insuficiente, por exemplo, mostrar o valor que ainda falta evitaria dúvidas no caixa.

## Limite desta jornada

O fluxo foi elaborado a partir dos requisitos do Desktop. A existência de telas específicas, leitor de código de barras, integração com dispositivo de pagamento e impressão de recibo precisa ser confirmada diretamente na aplicação antes de ser apresentada como funcionalidade implementada.
