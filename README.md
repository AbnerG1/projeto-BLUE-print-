# BLUE print — Design de Serviço

**Aluno:** Abner da Silva Gomes  
**Matrícula:** 251018184

Este repositório reúne as entregas dos quatro níveis da atividade de Design de Serviço. Os dois aplicativos de origem permanecem independentes; este projeto centraliza apenas sua documentação.

| Nível | Projeto de origem | Ferramenta |
|---|---|---|
| 1 | Sistema Desktop de Gestão e Caixa | Jornada do usuário |
| 2 | Sistema Desktop de Gestão e Caixa | Blueprint do serviço |
| 3 | TechStock — BMVC | Jornada do usuário |
| 4 | TechStock — BMVC | Blueprint do serviço |

## Projetos de origem

- [Projeto Desktop](https://github.com/AbnerG1/Projeto-desktop): gestão de estoque e operações de caixa para pequenos comércios.
- [TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc): catálogo de componentes eletrônicos, em Python com Bottle e arquitetura MVC.

## Entregas incluídas no repositório

### Documentação dos níveis
- [Escopo, fontes e premissas](docs/00-escopo-e-premissas.md)
- [Nível 1 — Jornada Desktop](docs/nivel-1-jornada-desktop.md)
- [Nível 2 — Blueprint Desktop](docs/nivel-2-blueprint-desktop.md)
- [Nível 3 — Jornada TechStock](docs/nivel-3-jornada-bmvc.md)
- [Nível 4 — Blueprint TechStock](docs/nivel-4-blueprint-bmvc.md)

### Materiais para apresentar
- [Roteiros de fala dos quatro vídeos](docs/roteiros-de-apresentacao.md)
- [Diagramas Mermaid editáveis](docs/diagramas-mermaid.md)
- [Documento consolidado — índice e síntese](entregaveis/documento-consolidado.md)
- [Apresentação — roteiro dos 12 slides](entregaveis/apresentacao.md)

## Precisão do material

A documentação do Desktop descreve atores, requisitos e fluxo esperado de venda; não comprova que todas as telas e integrações estejam implementadas. Por isso, os níveis 1 e 2 são modelos de serviço derivados dos requisitos. Já os níveis 3 e 4 foram construídos a partir da leitura do código real do TechStock: login, sessão, página de consulta, busca local no catálogo e operações CRUD por cURL.

Os arquivos exportados para apresentação e consulta (.pptx, .docx e versões PDF) acompanham a entrega nesta conversa. Os arquivos-fonte textuais e diagramas permanecem editáveis neste repositório.

Cada vídeo deve ter duração máxima de cinco minutos, conforme o enunciado.

## Aviso

Este repositório é a documentação de Design de Serviço dos dois sistemas. Ele não funde o código-fonte dos aplicativos e não substitui os repositórios originais.
