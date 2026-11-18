# Escopo e premissas

## Objetivo
Documentar jornadas do usuário e blueprints de serviço para os quatro níveis da microtarefa, respeitando o limite de cinco minutos por vídeo.

## Separação dos sistemas

| Nível | Sistema | Perfil central | Entrega |
|---|---|---|---|
| 1 | Sistema Desktop de Gestão e Caixa | Operador de Caixa | Jornada do usuário |
| 2 | Sistema Desktop de Gestão e Caixa | Operador de Caixa | Blueprint |
| 3 | TechStock BMVC | Operador/gerente do catálogo | Jornada do usuário |
| 4 | TechStock BMVC | Operador/gerente do catálogo | Blueprint |

Os dois projetos não são uma única aplicação. O BLUE print é o repositório que reúne os artefatos de Design de Serviço; os códigos-fonte continuam nos repositórios originais.

## Fontes

1. Especificação do Sistema Desktop de Gestão e Caixa (Módulo 01), com os atores Operador de Caixa e Gerente, o fluxo de registro de venda, as exceções de produto inexistente e estoque insuficiente e as regras do pagamento.
2. Repositório [Projeto-desktop](https://github.com/AbnerG1/Projeto-desktop).
3. Repositório [TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc), incluindo README, rotas Bottle, modelos, controllers, templates, JavaScript e testes.
4. Enunciado de Ferramentas de Design de Serviço mostrado na imagem enviada na conversa.

## Premissas e limites

### Desktop
O documento de Módulo 01 especifica o comportamento esperado do sistema: autenticação, registro da venda, pesquisa de produto por código de barras ou identificador, totalização, pagamento, baixa de estoque e recibo. Os materiais acessíveis não comprovam que todas essas telas, integrações e operações estejam implementadas na versão executável do Desktop. Por isso, os níveis 1 e 2 são **modelos de experiência baseados nos requisitos**, e não uma auditoria de telas implementadas.

O meio de pagamento não é detalhado na especificação. O blueprint representa a confirmação do pagamento como etapa do serviço, sem presumir integração com banco, adquirente ou maquininha.

### TechStock BMVC
Os níveis 3 e 4 descrevem o código consultado. O login ocorre em `/portal`; a consulta visual é feita em `/banco`; a busca por nome/categoria filtra a tabela no navegador. CREATE, UPDATE e DELETE são executados por requisições HTTP com cURL e sessão autenticada, não por botões de edição na página.

O catálogo guarda ID, nome, categoria, quantidade e descrição. Os dados são persistidos em arquivos JSON. A sessão é mantida em memória e expira após uma hora; reiniciar o servidor exige novo login.

## Como diferenciar os artefatos
- **Jornada do usuário:** mostra o que a pessoa faz, pensa, sente e quais dificuldades encontra ao longo do tempo.
- **Blueprint:** conecta as ações do usuário às interações visíveis, às ações internas e aos processos/sistemas de suporte.

## Sugestões de melhoria (não são funcionalidades atuais)
- Desktop: feedback claro de cada etapa, prevenção de erro na leitura de produto e confirmação legível de pagamento/recibo.
- TechStock: oferecer cadastro, edição e remoção por interface gráfica para reduzir a necessidade de terminal.
