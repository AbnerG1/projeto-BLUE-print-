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

## Entregas

- `docs/00-escopo-e-premissas.md`: escopo, fontes e limites da análise.
- `docs/nivel-1-jornada-desktop.md`: jornada do Operador de Caixa.
- `docs/nivel-2-blueprint-desktop.md`: blueprint da venda.
- `docs/nivel-3-jornada-bmvc.md`: jornada do usuário TechStock.
- `docs/nivel-4-blueprint-bmvc.md`: blueprint de consulta e manutenção do catálogo.
- `docs/roteiros-de-apresentacao.md`: fala sugerida para os quatro vídeos.
- `docs/diagramas-mermaid.md`: diagramas editáveis.
- `entregaveis/`: documento e apresentação final.

## Precisão do material

A documentação do Desktop descreve atores, requisitos e fluxo esperado de venda; não comprova que todas as telas e integrações estejam implementadas. Por isso, os níveis 1 e 2 são modelos de serviço derivados dos requisitos. Já os níveis 3 e 4 foram construídos a partir da leitura do código real do TechStock: login, sessão, página de consulta, busca local no catálogo e operações CRUD por cURL.

Cada vídeo deve ter duração máxima de cinco minutos, conforme o enunciado.

## Aviso

Este repositório não funde o código-fonte dos dois aplicativos e não substitui os repositórios originais.
