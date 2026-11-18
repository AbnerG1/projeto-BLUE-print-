# Documento consolidado — BLUE print

## Identificação
- **Aluno:** Abner da Silva Gomes
- **Matrícula:** 251018184
- **Atividade:** Ferramentas de Design de Serviço — Jornadas e Blueprints

## Organização das entregas
O trabalho possui quatro níveis e usa dois sistemas distintos. O repositório BLUE print reúne a documentação, mas não combina os códigos-fonte dos sistemas.

| Nível | Sistema | Entrega |
|---|---|---|
| 1 | Sistema Desktop de Gestão e Caixa | Jornada do usuário |
| 2 | Sistema Desktop de Gestão e Caixa | Blueprint do serviço |
| 3 | TechStock BMVC | Jornada do usuário |
| 4 | TechStock BMVC | Blueprint do serviço |

## Síntese
### Níveis 1 e 2 — Desktop App
A jornada é centrada no Operador de Caixa: autenticação, início da venda, inclusão de produtos, totalização, pagamento e finalização com baixa de estoque e recibo. O blueprint conecta as ações à interface e às atividades internas, como consulta ao catálogo, conferência de estoque, cálculo do total, validação do pagamento e persistência da venda.

**Limite:** os níveis 1 e 2 são derivados dos requisitos documentados do Módulo 01. Não se afirma que todas as telas, dispositivos ou integrações estejam implementados na versão executável.

### Níveis 3 e 4 — TechStock BMVC
A jornada representa a autenticação em `/portal`, consulta em `/banco`, filtro local da tabela e manutenção dos componentes por cURL. O blueprint mapeia as rotas Bottle, a classe Application, os records, os modelos e a persistência em JSON.

**Evidência:** os níveis 3 e 4 foram conferidos a partir do código, templates, JavaScript e testes existentes no repositório TechStock.

## Índice dos documentos
- [Escopo, fontes e premissas](../docs/00-escopo-e-premissas.md)
- [Nível 1 — Jornada Desktop](../docs/nivel-1-jornada-desktop.md)
- [Nível 2 — Blueprint Desktop](../docs/nivel-2-blueprint-desktop.md)
- [Nível 3 — Jornada TechStock](../docs/nivel-3-jornada-bmvc.md)
- [Nível 4 — Blueprint TechStock](../docs/nivel-4-blueprint-bmvc.md)
- [Diagramas editáveis](../docs/diagramas-mermaid.md)
- [Roteiros dos quatro vídeos](../docs/roteiros-de-apresentacao.md)
- [Estrutura da apresentação de 12 slides](./apresentacao.md)

## Projetos de origem
- [Projeto Desktop](https://github.com/AbnerG1/Projeto-desktop)
- [TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc)

## Regra de apresentação
O enunciado estabelece duração máxima de cinco minutos por vídeo. Os quatro roteiros foram planejados para aproximadamente três a quatro minutos, permitindo explicar as etapas e mostrar o diagrama sem ultrapassar esse limite.
