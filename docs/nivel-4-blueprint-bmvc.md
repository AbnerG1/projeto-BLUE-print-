# Nível 4 — Blueprint do serviço | TechStock BMVC

## O que este blueprint acompanha

Aqui o foco é mostrar o caminho que uma ação percorre dentro do TechStock. Quando a pessoa faz login ou consulta um componente, por exemplo, a interface chama uma rota, a aplicação coordena a operação e os dados são lidos ou gravados nos arquivos JSON.

O mapa foi montado a partir do código existente no repositório, não apenas de uma descrição geral de como um catálogo poderia funcionar.

## Blueprint por etapa

| Camada | Abrir o Portal | Fazer login | Consultar Banco | Filtrar a lista | Manter o catálogo | Sair |
|---|---|---|---|---|---|---|
| Evidência física | Navegador e endereço /portal. | Formulário com usuário e senha. | Página Banco, indicadores e tabela. | Campo de busca. | Terminal e resposta HTTP/JSON do cURL. | Link Sair no cabeçalho. |
| Ação do usuário | Acessa o endereço local. | Envia as credenciais. | Abre a página de consulta. | Digita um termo. | Envia uma requisição autenticada para a API. | Seleciona Sair. |
| Contato com o sistema | GET /portal. | POST /portal. | GET /banco. | Evento de digitação tratado pelo JavaScript. | POST, PUT ou DELETE /componentes; também existe GET /componentes. | GET /logout. |
| Frontstage — retorno visível | Formulário do Portal. | Redirecionamento para Banco ou mensagem de erro. | Tabela, indicadores e usuário conectado. | Linhas correspondentes ao termo digitado. | Mensagem e dados de retorno em JSON, com código HTTP. | Retorno à página Portal. |
| Backstage — lógica da aplicação | Bottle encaminha a requisição para a rota. | Application.autenticar consulta UserRecord e confere a senha. | Application.render_banco obtém os componentes e calcula o total de unidades. | main.js compara o texto das linhas da tabela. | A rota confere a sessão, chama ComponentRecord e aplica as validações de Componente. | Application.logout encerra a sessão. |
| Suporte e dados | Servidor Bottle e templates. | Hash PBKDF2-HMAC-SHA256 com salt; criação da sessão. | ComponentRecord e arquivo componentes.json. | JavaScript e CSS da página. | DataRecord faz a leitura/gravação JSON; testes verificam as operações. | Cookie session_id removido; sessão encerrada em memória. |

## Quem faz o quê dentro do código

- **Rotas (route.py):** recebem as requisições de login, logout, consulta e manutenção dos componentes.
- **Application (app/controllers/application.py):** coordena autenticação, sessão e montagem das páginas.
- **Models:** User_account representa a conta; Componente representa um item do catálogo; Sessao e GerenciadorSessoes cuidam da sessão.
- **Records (app/controllers/datarecord.py):** DataRecord é a base para ler e gravar dados; UserRecord e ComponentRecord trabalham com contas e componentes.
- **Views:** portal.tpl, banco.tpl e layout.tpl montam as páginas.
- **Arquivos de dados:** user_accounts.json e componentes.json guardam as informações persistidas.

## Rotas e respostas

| Ação | Rota | O que acontece |
|---|---|---|
| Entrar | POST /portal | Com credenciais válidas, cria uma sessão e redireciona para Banco. Credenciais incorretas retornam HTTP 401. |
| Consultar em JSON | GET /componentes | Retorna os componentes e exige uma sessão válida. |
| Cadastrar | POST /componentes | Cria um componente; quando os dados são aceitos, retorna HTTP 201. |
| Alterar | PUT /componentes/<id> | Atualiza o componente; dados inválidos retornam 400 e ID não encontrado retorna 404. |
| Excluir | DELETE /componentes/<id> | Remove o componente; ID não encontrado retorna 404. |
| Sair | GET /logout | Encerra a sessão, remove o cookie e volta ao Portal. |

As rotas de manutenção também exigem autenticação. Uma chamada sem sessão válida recebe HTTP 401.

## O que acontece quando algo dá errado

- **Login incorreto:** a página mostra o erro e permite tentar novamente.
- **Acesso à API sem login:** a rota bloqueia a requisição com HTTP 401.
- **Campo inválido:** a validação do modelo impede a gravação e a rota responde HTTP 400.
- **ID inexistente:** a tentativa de alterar ou excluir um componente retorna HTTP 404.
- **Sessão expirada:** o token deixa de ser aceito e o usuário precisa entrar novamente.
- **Servidor reiniciado:** as sessões são perdidas porque ficam em memória; os dados salvos nos arquivos JSON permanecem.

## Uma melhoria que faria diferença

Hoje, a consulta é feita pela interface web, mas a manutenção do catálogo depende do terminal. Uma melhoria seria criar formulários de cadastro, edição e exclusão na página Banco, aproveitando as rotas e as validações que o projeto já possui. Isso tornaria o uso mais direto sem precisar mudar a separação MVC.
