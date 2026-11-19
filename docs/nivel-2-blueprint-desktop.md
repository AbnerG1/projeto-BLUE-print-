# Nível 2 — Blueprint do serviço | Sistema Desktop de Gestão e Caixa

O blueprint acompanha o trabalho do operador desde a escolha do perfil até o encerramento da venda. Também inclui as atividades do painel administrativo que mantêm o catálogo e o estoque atualizados.

## Blueprint da venda

| Camada | Acesso | Início da venda | Inclusão dos produtos | Totalização | Fechamento |
|---|---|---|---|---|---|
| Evidência física | Tela "Selecione seu acesso". | Painel do funcionário e botão "Iniciar nova venda". | Janela de venda, carrinho e botão "Adicionar Produto". | Lista de itens e total. | Botões "Fechar Venda" e "Cancelar Venda". |
| Ação do usuário | Escolhe "Funcionário (Caixa)". | Inicia uma venda. | Adiciona os produtos da compra. | Confere os itens e o total. | Fecha ou cancela a venda. |
| Frontstage — o que aparece | Área do funcionário. | Tela "Nova Venda". | Produtos incluídos no carrinho. | Total da venda atualizado. | Retorno ao painel após fechar ou cancelar. |
| Backstage — o que acontece | Define o perfil ativo. | Prepara o carrinho e a nova venda. | Consulta o produto e verifica a quantidade disponível. | Soma os subtotais dos itens. | Registra a venda e atualiza o estoque. |
| Suporte necessário | Tela de perfis e controle de acesso. | Interface Tkinter. | Catálogo e consulta ao estoque. | Lógica de cálculo. | SQLite e rotinas de venda. |

## Administração do estoque

O perfil Administrador/Gerente abre o painel administrativo. Nele estão as operações de criar, listar, atualizar e excluir produtos, além do relatório de vendas do dia. Essas ações dão suporte ao trabalho do caixa porque mantêm o catálogo e as quantidades disponíveis.

## O que acontece no banco de dados

O módulo sistema_bd.py usa SQLite e cria três tabelas:

- produtos: guarda nome, preço e quantidade em estoque.
- vendas: guarda o registro e o total da venda.
- itens_venda: relaciona os produtos e as quantidades incluídas em cada venda.

A rotina registrar_venda_e_baixar_estoque grava a venda, registra os itens e diminui as quantidades correspondentes no estoque.

## Um ponto para conferir antes da apresentação

O estudo de caso do Módulo 01 prevê selecionar a forma de pagamento, validar o valor recebido pela regra RN01 e gerar um recibo. A gravação analisada mostra o total e o botão de fechar venda, mas não permite confirmar uma etapa separada de pagamento ou a emissão do recibo. Antes de apresentá-los como funções implementadas, é importante verificar esses passos na versão que será executada.
