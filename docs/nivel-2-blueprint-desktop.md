# Nível 2 — Blueprint do serviço | Sistema Desktop de Gestão e Caixa

## Serviço analisado

O blueprint acompanha o atendimento no caixa, desde o login do Operador até a entrega do recibo. A intenção é mostrar não só o que acontece na frente do usuário, mas também o trabalho interno necessário para concluir uma venda.

O Operador de Caixa é o ator principal. O Gerente aparece como responsável pelo cadastro e acompanhamento do estoque, conforme o estudo de caso. O cliente participa da compra, mas não tem uma interação direta com o sistema descrita no material.

## Blueprint por etapa

| Camada | Acesso | Início da venda | Inclusão de produtos | Totalização | Pagamento | Conclusão |
|---|---|---|---|---|---|---|
| Evidência física | Computador do caixa. | Área de nova venda prevista no sistema. | Produto, etiqueta ou código identificador. | Relação de itens e valor total. | Meio de pagamento escolhido. | Recibo ou comprovante. |
| Ação do usuário | Informa as credenciais. | Inicia uma venda. | Informa o código/identificador de cada item. | Pede o fechamento da lista. | Seleciona a forma e confirma o valor recebido. | Entrega o recibo ao cliente. |
| Contato com o sistema | Envia os dados de acesso. | Aciona a abertura da venda. | Faz a consulta do produto. | Solicita o cálculo do total. | Confirma o pagamento. | Recebe a confirmação da operação. |
| Frontstage — o que aparece | Tela de login e retorno de acesso. | Área para registrar a venda. | Produto localizado, preço e parcial. | Valor final da compra. | Resultado da validação do pagamento. | Confirmação da venda e recibo. |
| Backstage — o que precisa acontecer | Conferir usuário e senha. | Preparar o registro da venda. | Consultar o catálogo e verificar o saldo. | Somar os itens e calcular o total. | Conferir se o valor recebido é suficiente. | Registrar a venda e atualizar as quantidades. |
| Suporte necessário | Cadastro de usuários. | Dados da venda e dos itens. | Catálogo e controle de estoque. | Regras de preço e cálculo. | Regra RN01. | Persistência dos dados, baixa do estoque e geração do recibo. |

## Exceções que precisam ser tratadas

1. **Produto não encontrado:** a consulta não retorna um item válido. O sistema precisa avisar o operador e permitir que ele confira o código.
2. **Estoque insuficiente:** a quantidade disponível não atende ao pedido. O item não deve ser incluído.
3. **Pagamento insuficiente:** a regra RN01 impede finalizar a venda quando o valor pago é menor que o total.
4. **Estoque zerado:** a regra RN02 impede que o produto entre na lista de compras.

## O que acontece nos bastidores

Para o atendimento funcionar, o sistema depende de um catálogo atualizado, informações corretas de preço e quantidade, cálculo consistente dos itens e registro da venda concluída. O Gerente tem papel importante na manutenção do catálogo e no acompanhamento do estoque.

No fechamento, a atualização do estoque e a geração do recibo precisam acontecer como parte do resultado da venda. O cliente e o operador devem receber uma confirmação que deixe claro que a operação terminou.

## Pontos de atenção e melhorias possíveis

| Ponto de atenção | O que pode acontecer | Ideia para evitar o problema |
|---|---|---|
| Código digitado incorretamente | O produto não é localizado. | Mostrar uma mensagem direta e facilitar uma nova tentativa. |
| Quantidade desatualizada | O caixa tenta vender algo que não está disponível. | Conferir o saldo antes de incluir o item e no fechamento. |
| Valor recebido abaixo do total | A venda pode ficar incompleta. | Não permitir a conclusão e mostrar quanto falta. |
| Falta de confirmação | O operador não sabe se a venda foi gravada. | Exibir o resultado e disponibilizar o recibo. |

## Limite do blueprint

Este mapa representa o serviço especificado no Módulo 01. Os materiais consultados não confirmam todas as telas, o dispositivo de pagamento ou o mecanismo de impressão. Esses pontos aparecem como partes necessárias ou previstas do serviço, não como recursos cuja implementação foi verificada.
