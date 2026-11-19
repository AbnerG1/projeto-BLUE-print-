# Nível 2 — Blueprint do serviço | Sistema Desktop de Gestão e Caixa

O blueprint acompanha uma venda desde o acesso do Operador de Caixa até a entrega do recibo. Além das ações do operador, ele mostra o retorno da interface e as tarefas internas necessárias para concluir o atendimento.

O Operador de Caixa é o ator principal. O Gerente aparece no estudo de caso como responsável pelo cadastro e acompanhamento do estoque.

## Blueprint

| Camada | Acesso | Início da venda | Inclusão dos produtos | Totalização | Pagamento | Conclusão |
|---|---|---|---|---|---|---|
| Evidência física | Computador do caixa. | Área de nova venda. | Produto, etiqueta ou código. | Lista de itens e total. | Meio de pagamento escolhido. | Recibo ou comprovante. |
| Ação do usuário | Informa as credenciais. | Inicia uma venda. | Informa o código de cada item. | Confere a lista e pede o total. | Escolhe a forma e informa o valor recebido. | Entrega o recibo ao cliente. |
| Contato com o sistema | Envia os dados de acesso. | Abre o registro da venda. | Consulta cada produto. | Calcula o valor final. | Confirma o pagamento. | Apresenta o resultado da venda. |
| Frontstage — o que aparece | Tela de login e retorno do acesso. | Área de registro da venda. | Nome do produto, preço e parcial. | Valor total da compra. | Resultado da validação do pagamento. | Confirmação e recibo. |
| Backstage — o que acontece | Confere usuário e senha. | Prepara o registro da venda. | Consulta o catálogo e verifica o estoque. | Soma os itens e calcula o total. | Confere se o valor recebido cobre a compra. | Registra a venda e atualiza as quantidades. |
| Suporte necessário | Cadastro de usuários. | Dados da venda e dos itens. | Catálogo e controle de estoque. | Regras de preço e cálculo. | Regra RN01. | Armazenamento dos dados e geração do recibo. |

## Quando algo não sai como esperado

- Se o produto não for encontrado, o sistema avisa e o operador confere o código.
- Se não houver estoque suficiente, o item não entra na venda. A regra RN02 também impede incluir produtos com estoque zerado.
- Se o valor recebido for menor que o total, a regra RN01 impede finalizar a venda.

O catálogo e o controle de estoque, mantidos pelo Gerente, dão suporte ao trabalho do caixa. No fim da venda, o registro, a atualização das quantidades e o recibo precisam corresponder à mesma operação.
