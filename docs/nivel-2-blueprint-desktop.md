# Nível 2 — Blueprint do serviço | Sistema Desktop de Gestão e Caixa

O blueprint mostra o trabalho dos dois perfis e o que acontece por trás das telas. O caixa cuida da venda; o gerente mantém os produtos e acompanha os resultados.

## Blueprint — venda no caixa

| Camada | Acesso | Montagem da compra | Pagamento | Fechamento |
|---|---|---|---|---|
| Ação do usuário | Escolhe Funcionário (Caixa). | Inicia a venda e adiciona produtos. | Informa os dados solicitados para o pagamento. | Confirma a operação e entrega a nota fiscal. |
| Frontstage — o que aparece | Painel do funcionário. | Tela de venda, itens e total atualizado. | Área de finalização da compra. | Confirmação da venda e nota fiscal. |
| Backstage — processamento | Identifica o perfil ativo. | Consulta produtos, confere estoque e calcula o total. | Aplica as regras de pagamento. | Registra a venda, grava os itens e atualiza o estoque. |
| Suporte | Controle de acesso e interface Tkinter. | Catálogo e lógica de cálculo. | Rotina de pagamento. | Banco SQLite e rotina de emissão da nota fiscal. |

## Blueprint — gestão pelo gerente

| Camada | Acessar administração | Manter produtos | Acompanhar o dia |
|---|---|---|---|
| Ação do usuário | Escolhe o perfil Gerente. | Cadastra ou atualiza produtos e consulta o estoque. | Abre o relatório diário. |
| Frontstage — o que aparece | Painel administrativo. | Formulários e listagem de produtos. | Relatório com quantidade de vendas e total arrecadado. |
| Backstage — processamento | Confere o perfil e libera as opções administrativas. | Valida e salva os dados do catálogo. | Consulta as vendas registradas e calcula os indicadores do dia. |
| Suporte | Interface Tkinter e controle de acesso. | Rotinas de produto e estoque. | Registros de vendas no SQLite e cálculo do relatório. |

## Dados que dão suporte ao sistema

O módulo `sistema_bd.py` usa SQLite. A estrutura consultada contém registros de produtos, vendas e itens vendidos. Na conclusão da venda, o sistema grava o total e os itens e atualiza as quantidades do estoque.

A nota fiscal faz parte do fechamento apresentado pelo aluno. O relatório diário reúne a quantidade de vendas e o total arrecadado, permitindo ao gerente acompanhar o resultado do comércio.

## O que mostrar na apresentação

1. Entrar como Funcionário (Caixa), iniciar uma venda e incluir mais de um produto.
2. Conferir o total, concluir a venda e mostrar a nota fiscal.
3. Voltar à seleção de perfil e entrar como Gerente.
4. Cadastrar ou atualizar um produto e mostrar a alteração no catálogo.
5. Abrir o relatório diário e apontar a quantidade de vendas e o total arrecadado.

Essa sequência deixa visível a relação entre as ações dos usuários, as telas, as regras do sistema e os dados salvos.
