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

A jornada acompanha o Operador de Caixa durante uma venda: ele entra no sistema, inclui os produtos, confere o total, recebe o pagamento e entrega o recibo.

No blueprint, esse mesmo atendimento é visto por dentro. Além das ações do operador, aparecem a consulta ao catálogo, a verificação do estoque, o cálculo do total, a validação do pagamento e o registro da venda.

Esses dois níveis seguem o estudo de caso do Módulo 01, que descreve o funcionamento esperado do sistema.

## Níveis 3 e 4 — TechStock BMVC

No TechStock, o usuário entra pelo Portal e consulta os componentes na página Banco. O filtro é feito no navegador. Para cadastrar, alterar ou excluir um item, é necessário usar o terminal com cURL e uma sessão autenticada.

O blueprint relaciona essas ações às rotas Bottle, à classe Application, aos modelos, aos records e aos arquivos JSON usados para guardar os dados.

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
