# Documento consolidado — BLUE print

## Identificação

- **Aluno:** Abner da Silva Gomes
- **Matrícula:** 251018184
- **Atividade:** Ferramentas de Design de Serviço — Jornadas e Blueprints

## Como o trabalho foi organizado

A atividade foi dividida em quatro níveis e usa dois sistemas diferentes. Os dois primeiros olham para o Sistema Desktop de Gestão e Caixa; os dois últimos analisam o TechStock BMVC. Mantive os projetos separados porque cada um tem seu próprio objetivo e sua própria implementação.

| Nível | Sistema | Entrega |
|---|---|---|
| 1 | Sistema Desktop de Gestão e Caixa | Jornada do usuário |
| 2 | Sistema Desktop de Gestão e Caixa | Blueprint do serviço |
| 3 | TechStock BMVC | Jornada do usuário |
| 4 | TechStock BMVC | Blueprint do serviço |

## Níveis 1 e 2 — Sistema Desktop de Gestão e Caixa

A jornada acompanha o Operador de Caixa desde o acesso ao sistema até a finalização da venda. Nesse caminho, ele inicia o atendimento, informa os produtos, confere o total, recebe o pagamento e entrega o recibo.

O blueprint mostra o que precisa acontecer em cada etapa para que o atendimento funcione: autenticação, consulta ao catálogo, verificação de estoque, cálculo do total, validação do pagamento, registro da venda e atualização das quantidades.

**Importante:** esses dois mapas foram construídos a partir do estudo de caso do Módulo 01. Eles representam o serviço definido nos requisitos; não confirmam que todas as telas, integrações e dispositivos estejam implementados na versão executável.

## Níveis 3 e 4 — TechStock BMVC

No TechStock, a jornada começa no Portal, passa pelo login e chega à página Banco, onde os componentes podem ser consultados e filtrados. Quando é necessário cadastrar, alterar ou excluir um item, a operação é feita pelo terminal usando cURL e uma sessão autenticada.

O blueprint abre esse fluxo e mostra como as rotas Bottle se conectam à classe Application, aos modelos, aos records e aos arquivos JSON que armazenam os dados.

**Importante:** a consulta visual existe na página Banco. As operações de cadastro, alteração e exclusão não são botões da interface web; são chamadas HTTP feitas no terminal.

## Documentos do trabalho

- [Escopo, fontes e premissas](../docs/00-escopo-e-premissas.md)
- [Nível 1 — Jornada Desktop](../docs/nivel-1-jornada-desktop.md)
- [Nível 2 — Blueprint Desktop](../docs/nivel-2-blueprint-desktop.md)
- [Nível 3 — Jornada TechStock](../docs/nivel-3-jornada-bmvc.md)
- [Nível 4 — Blueprint TechStock](../docs/nivel-4-blueprint-bmvc.md)
- [Diagramas editáveis](../docs/diagramas-mermaid.md)
- [Organização da apresentação](./apresentacao.md)

## Projetos de origem

- [Projeto Desktop](https://github.com/AbnerG1/Projeto-desktop)
- [TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc)

## Apresentação

O enunciado pede um vídeo de até cinco minutos para cada nível. Na gravação, é melhor usar o diagrama como guia e explicar o fluxo com as próprias palavras, destacando as decisões e dificuldades mais importantes em cada etapa.
