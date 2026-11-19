# Escopo e fontes

O trabalho foi dividido em quatro níveis, usando dois projetos diferentes.

| Nível | Sistema | Perfil | Entrega |
|---|---|---|---|
| 1 | Sistema Desktop de Gestão e Caixa | Operador de Caixa | Jornada do usuário |
| 2 | Sistema Desktop de Gestão e Caixa | Operador de Caixa | Blueprint |
| 3 | TechStock BMVC | Pessoa que consulta o catálogo | Jornada do usuário |
| 4 | TechStock BMVC | Pessoa que consulta e mantém o catálogo | Blueprint |

## Materiais consultados

- Estudo de caso do Sistema Desktop de Gestão e Caixa (Módulo 01).
- [Projeto Desktop](https://github.com/AbnerG1/Projeto-desktop).
- Demonstração do Desktop enviada pelo aluno.
- [TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc): README, rotas, modelos, controllers, páginas, JavaScript e testes.

## Sobre os mapas

A jornada acompanha as ações do usuário. O blueprint mostra também o que a interface apresenta e quais processos internos dão suporte a cada etapa.

No Desktop, a gravação mostra a escolha do perfil, o painel do funcionário, a abertura de uma venda e as opções para adicionar produtos, fechar ou cancelar a venda. O painel administrativo também apresenta cadastro, listagem, atualização e exclusão de produtos, além do relatório de vendas.

O módulo de dados disponível usa SQLite. Ele cria as tabelas de produtos, vendas e itens da venda. A rotina de registro da venda grava o total e os itens e atualiza a quantidade em estoque.

O estudo de caso do Módulo 01 também prevê a seleção da forma de pagamento, a regra RN01 e a emissão de recibo. Esses pontos precisam ser conferidos na versão executável: não aparecem de forma clara na gravação analisada nem no esquema SQLite disponível.

No TechStock, foi possível conferir o fluxo diretamente no código. O usuário entra por /portal e consulta os componentes em /banco. O filtro é feito no navegador. A consulta também existe pela rota GET /componentes; já o cadastro, a alteração e a exclusão são feitos por requisições cURL autenticadas.

Os dados do TechStock ficam em arquivos JSON. As sessões são mantidas em memória, expiram após uma hora e precisam ser refeitas quando o servidor é reiniciado.
