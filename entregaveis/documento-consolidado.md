# Documento consolidado — BLUE print

**Aluno:** Abner da Silva Gomes  
**Matrícula:** 251018184  
**Atividade:** Ferramentas de Design de Serviço — Jornadas e Blueprints

## Organização do trabalho

Os quatro níveis usam dois sistemas diferentes. Os níveis 1 e 2 tratam do Sistema Desktop de Gestão e Caixa; os níveis 3 e 4, do TechStock BMVC.

| Nível | Sistema | Entrega |
|---|---|---|
| 1 | Sistema Desktop de Gestão e Caixa | Jornada do usuário |
| 2 | Sistema Desktop de Gestão e Caixa | Blueprint do serviço |
| 3 | TechStock BMVC | Jornada do usuário |
| 4 | TechStock BMVC | Blueprint do serviço |

## Níveis 1 e 2 — Desktop

O Desktop tem dois perfis. O Funcionário (Caixa) registra as compras, adiciona os produtos, recebe o pagamento, conclui a venda e emite a nota fiscal. O Gerente cadastra e atualiza produtos, acompanha o estoque e consulta o relatório diário, que apresenta a quantidade de vendas e o total arrecadado.

O blueprint relaciona essas ações às telas do Tkinter e às rotinas internas. O módulo de dados usa SQLite para guardar produtos, vendas e itens vendidos. Ao registrar uma venda, o sistema grava os itens e o total e atualiza as quantidades do estoque.

## Níveis 3 e 4 — TechStock BMVC

No TechStock, o usuário entra pelo Portal e consulta os componentes na página Banco. O filtro é feito no navegador. Para cadastrar, alterar ou excluir um item, é necessário usar o terminal com cURL e uma sessão autenticada.

O blueprint relaciona essas ações às rotas Bottle, à classe Application, aos modelos, aos records e aos arquivos JSON usados para guardar os dados. A estrutura do projeto inicial BMVC disponibilizado pelo professor foi consultada como referência para a separação entre rotas, aplicação, modelos, acesso aos dados e páginas.

## Documentos

- [Escopo e fontes](../docs/00-escopo-e-premissas.md)
- [Nível 1 — Jornada Desktop](../docs/nivel-1-jornada-desktop.md)
- [Nível 2 — Blueprint Desktop](../docs/nivel-2-blueprint-desktop.md)
- [Nível 3 — Jornada TechStock](../docs/nivel-3-jornada-bmvc.md)
- [Nível 4 — Blueprint TechStock](../docs/nivel-4-blueprint-bmvc.md)
- [Diagramas](../docs/diagramas-mermaid.md)
- [Apresentação](./apresentacao.md)

## Projetos usados

- [Projeto Desktop](https://github.com/AbnerG1/Projeto-desktop)
- [TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc)
- [Projeto inicial BMVC disponibilizado pelo professor](https://github.com/hgmachine/bmvc_start_from_this)
