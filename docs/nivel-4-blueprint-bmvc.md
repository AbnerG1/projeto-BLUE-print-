# Nível 4 — Blueprint do serviço | TechStock BMVC

Este blueprint mostra o caminho entre o que a pessoa faz na página e o que acontece no código do TechStock: as rotas recebem as solicitações, a aplicação coordena as operações e os dados são consultados ou gravados nos arquivos JSON.

## Blueprint

| Camada | Abrir o Portal | Fazer login | Consultar Banco | Filtrar a lista | Manter o catálogo | Sair |
|---|---|---|---|---|---|---|
| Evidência física | Navegador e endereço /portal. | Formulário de usuário e senha. | Página Banco, indicadores e tabela. | Campo de busca. | Terminal e resposta do cURL. | Link Sair. |
| Ação do usuário | Acessa o endereço local. | Envia as credenciais. | Abre a página de consulta. | Digita um termo. | Envia uma requisição autenticada. | Seleciona Sair. |
| Contato com o sistema | GET /portal. | POST /portal. | GET /banco. | JavaScript trata a digitação. | GET, POST, PUT ou DELETE /componentes. | GET /logout. |
| Frontstage — o que aparece | Formulário do Portal. | Redirecionamento para Banco ou mensagem de erro. | Tabela, indicadores e usuário conectado. | Linhas que contêm o termo digitado. | Resposta em JSON e código HTTP. | Retorno ao Portal. |
| Backstage — o que acontece | Bottle encaminha a requisição. | Application.autenticar consulta UserRecord e confere a senha. | Application.render_banco carrega os componentes e calcula o total de unidades. | main.js filtra as linhas carregadas. | A rota confere a sessão e chama ComponentRecord, que usa as validações de Componente. | Application.logout encerra a sessão. |
| Suporte e dados | Servidor Bottle e templates. | Hash PBKDF2-HMAC-SHA256 com salt e criação da sessão. | ComponentRecord e arquivo componentes.json. | JavaScript e CSS. | DataRecord lê e grava os arquivos JSON; os testes verificam as operações. | Cookie session_id removido e sessão encerrada. |

## Partes do sistema envolvidas

- **Rotas (route.py):** recebem login, logout, consulta e operações nos componentes.
- **Application:** coordena autenticação, sessões e montagem das páginas.
- **Models:** representam contas, componentes e sessões.
- **Records:** leem e gravam os dados de usuários e componentes.
- **Views:** portal.tpl, banco.tpl e layout.tpl montam as páginas.
- **Dados:** user_accounts.json e componentes.json guardam as informações.

Na primeira execução, o sistema cria três componentes de exemplo: resistor de 220 Ω, capacitor de 100 µF e ESP32 DevKit.

## Respostas da API

| Situação | Resposta |
|---|---|
| Login incorreto ou requisição sem sessão válida | HTTP 401 |
| Dados inválidos | HTTP 400 |
| Cadastro concluído | HTTP 201 |
| ID não encontrado em alteração ou exclusão | HTTP 404 |
| Alteração ou exclusão concluída | HTTP 200 |

As sessões ficam em memória e expiram após uma hora. Se o servidor for reiniciado, o usuário precisa entrar novamente; os componentes salvos nos arquivos JSON permanecem.
