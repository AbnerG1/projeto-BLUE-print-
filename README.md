# BLUE print — Jornadas e Blueprints de Serviço

**Aluno:** Abner da Silva Gomes  
**Matrícula:** 251018184

Este repositório organiza as quatro partes da atividade de Design de Serviço. Usei como referência dois projetos que já fazem parte do meu trabalho: o Sistema Desktop de Gestão e Caixa e o TechStock, desenvolvido no padrão BMVC.

Eles têm objetivos e estruturas diferentes, então mantive cada um no seu lugar. O BLUE print reúne a documentação das jornadas, dos blueprints e da apresentação.

## Os dois projetos

- [Sistema Desktop de Gestão e Caixa](https://github.com/AbnerG1/Projeto-desktop) — proposta de sistema para pequenos comércios, com controle de produtos, vendas e estoque. A documentação do Módulo 01 define o Operador de Caixa e o Gerente como atores.
- [TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc) — catálogo de componentes eletrônicos feito em Python com Bottle e organizado em Model, View e Controller.

## O que está organizado aqui

| Nível | Projeto | Entrega |
|---|---|---|
| 1 | Desktop — Gestão e Caixa | Jornada do usuário |
| 2 | Desktop — Gestão e Caixa | Blueprint do serviço |
| 3 | TechStock — BMVC | Jornada do usuário |
| 4 | TechStock — BMVC | Blueprint do serviço |

### Documentos
- [Escopo, fontes e premissas](docs/00-escopo-e-premissas.md)
- [Nível 1 — Jornada Desktop](docs/nivel-1-jornada-desktop.md)
- [Nível 2 — Blueprint Desktop](docs/nivel-2-blueprint-desktop.md)
- [Nível 3 — Jornada TechStock](docs/nivel-3-jornada-bmvc.md)
- [Nível 4 — Blueprint TechStock](docs/nivel-4-blueprint-bmvc.md)
- [Diagramas editáveis](docs/diagramas-mermaid.md)
- [Documento consolidado](entregaveis/documento-consolidado.md)
- [Organização da apresentação](entregaveis/apresentacao.md)

## Como ler o trabalho

A jornada acompanha o usuário: o que ele tenta fazer, como o sistema responde e em quais momentos pode encontrar dificuldade. O blueprint amplia essa visão e mostra o que acontece por trás da interface para que o serviço funcione — por exemplo, consultas, validações, regras e armazenamento de dados.

## Uma observação sobre os projetos

Os níveis 1 e 2 foram montados com base nos requisitos documentados do Desktop. Eles representam como o serviço deve funcionar; não são uma afirmação de que todas as telas ou integrações já estejam prontas na aplicação.

Já os níveis 3 e 4 foram conferidos no código do TechStock. Nele, o usuário entra pelo Portal e consulta os componentes na página Banco. As operações de cadastro, alteração e exclusão são feitas por requisições cURL autenticadas no terminal, não por botões na página.

Os roteiros de fala são material de preparação pessoal e não fazem parte deste repositório. Cada vídeo da atividade deve ter no máximo cinco minutos.

## De onde vieram as informações

Consultei a especificação do Desktop, os repositórios originais e o enunciado da atividade. Os limites e as premissas estão descritos em [Escopo, fontes e premissas](docs/00-escopo-e-premissas.md).
