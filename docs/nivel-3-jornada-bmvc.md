# Nível 3 — Jornada do usuário | TechStock BMVC

## Quem usa e o que precisa fazer

Para esta jornada, considerei uma pessoa responsável por consultar e manter o catálogo de componentes eletrônicos. Ela precisa entrar no TechStock, localizar um item e, quando necessário, atualizar os registros.

O fluxo foi conferido no código do [TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc), incluindo as rotas, os modelos, as páginas e os testes.

## Jornada no TechStock

| Etapa | O que a pessoa faz | Resposta do sistema | Onde pode encontrar dificuldade |
|---|---|---|---|
| 1. Acessar | Abre /portal no navegador. | O sistema apresenta o formulário de login. | Não saber o endereço ou acessar com o servidor desligado. |
| 2. Entrar | Informa usuário e senha. | Com os dados corretos, a aplicação abre /banco. Com dados incorretos, apresenta uma mensagem de erro. | Digitar uma credencial errada ou não entender o motivo da falha. |
| 3. Consultar | Abre a lista de componentes. | A página mostra ID, nome, categoria, quantidade e descrição, além de um resumo do catálogo. | Ter dificuldade para identificar rapidamente o item desejado. |
| 4. Buscar | Digita um termo no campo de busca. | As linhas da tabela que correspondem ao texto ficam visíveis. | Não encontrar o item ou usar um termo diferente do cadastrado. |
| 5. Manter o catálogo | Usa o terminal e o cURL para cadastrar, alterar ou excluir um componente. | A API retorna uma resposta e um código HTTP. | Precisar conhecer os comandos, as rotas e o cookie da sessão. |
| 6. Conferir e sair | Atualiza a página e seleciona Sair quando termina. | A lista mostra os dados salvos e a sessão é encerrada. | Esquecer de atualizar a página antes de conferir a mudança. |

## O que já existe no projeto

- O acesso é feito pela rota /portal.
- Depois do login, a aplicação redireciona para /banco.
- A página Banco apresenta os componentes e o total de unidades cadastradas.
- A busca filtra as linhas já carregadas no navegador, usando o texto digitado.
- A consulta também pode ser feita pela rota GET /componentes, que retorna os registros em JSON.
- O cadastro usa POST /componentes; a alteração usa PUT /componentes/<id>; e a exclusão usa DELETE /componentes/<id>.
- As operações de manutenção são feitas pelo terminal com cURL. A página não possui botões ou formulários gráficos para essas três operações.

## Onde a experiência pode melhorar

O ponto que mais chama atenção é a diferença entre consultar e manter o catálogo. A consulta é simples e acontece no navegador; para cadastrar, editar ou excluir, a pessoa precisa sair da página e usar o terminal.

Também é necessário manter a autenticação nas requisições. Sem uma sessão válida, a API bloqueia o acesso. Dados inválidos e IDs inexistentes também geram respostas de erro.

Uma evolução natural seria trazer o cadastro, a edição e a exclusão para a própria interface, mantendo as validações que já existem no código. Assim, a pessoa não precisaria decorar comandos cURL para tarefas comuns.

## Observação sobre a persona e a curva emocional

A persona é representativa do uso do catálogo, não um perfil de funcionário real entrevistado. Da mesma forma, qualquer nota de satisfação usada na apresentação deve ser entendida como uma estimativa para ilustrar a jornada, não como resultado de uma pesquisa com usuários.
