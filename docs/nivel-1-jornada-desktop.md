# Nível 1 — Jornada do usuário | Sistema Desktop de Gestão e Caixa

**Perfil:** operador de caixa de um pequeno comércio.  
**Objetivo:** registrar a compra, receber o pagamento e concluir a venda com o estoque atualizado.

A jornada segue o fluxo descrito no estudo de caso do Módulo 01.

## Jornada do Operador de Caixa

| Etapa | O que o operador faz | Resposta esperada do sistema | O que pode atrapalhar | O que ajudaria |
|---|---|---|---|---|
| 1. Acesso | Informa usuário e senha. | Libera o acesso ao sistema. | Esquecer os dados ou receber uma mensagem confusa. | Mostrar claramente se o acesso foi aceito e o que fazer em caso de erro. |
| 2. Nova venda | Abre a área de registro de venda. | Apresenta o espaço para incluir os produtos. | Demorar para encontrar a função. | Deixar o início de uma venda fácil de localizar. |
| 3. Produtos | Informa o código de barras ou identificador de cada item. | Localiza o produto e mostra preço e valor parcial. | Código não encontrado ou estoque insuficiente. | Explicar o problema e permitir corrigir o código sem recomeçar a venda. |
| 4. Conferência | Confere os itens e pede a totalização. | Mostra a lista e o valor final. | Perceber tarde que um item ou uma quantidade está incorreta. | Deixar os itens e o total visíveis antes do pagamento. |
| 5. Pagamento | Escolhe a forma de pagamento e informa o valor recebido. | Confere se o valor cobre o total. | O valor recebido ser menor que o necessário. | Mostrar quanto ainda falta para concluir a venda. |
| 6. Finalização | Conclui a operação e entrega o recibo. | Registra a venda, atualiza o estoque e gera o comprovante. | Não saber se a venda foi concluída. | Exibir uma confirmação clara junto do recibo. |

## Situações fora do fluxo normal

- **Produto não encontrado:** o operador confere o código e tenta novamente.
- **Estoque insuficiente ou zerado:** o item não deve ser incluído na compra.
- **Pagamento abaixo do total:** pela regra RN01, a venda não pode ser finalizada enquanto o valor recebido for menor que o total.

A inclusão dos produtos e o pagamento são os momentos que mais exigem atenção, pois um erro pode atrasar o atendimento ou gerar divergência no estoque.
