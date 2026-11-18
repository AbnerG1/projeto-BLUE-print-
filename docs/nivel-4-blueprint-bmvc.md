# Nível 4 — Blueprint do serviço | TechStock BMVC

## Escopo
Mapear como as ações do usuário no TechStock se conectam às rotas Bottle, à lógica da aplicação, aos modelos e à persistência em JSON.

## Blueprint por etapa

| Camada | 1. Abrir portal | 2. Login | 3. Consultar Banco | 4. Filtrar lista | 5. CRUD via cURL | 6. Sair |
|---|---|---|---|---|---|---|
| Evidência física | Navegador e URL `/portal` | Formulário com usuário/senha | Tela Banco, tabela e indicadores | Campo de busca | Terminal, comando e resposta HTTP/JSON | Link Sair |
| Ação do usuário | Acessa o endereço | Envia credenciais | Abre página de consulta | Digita termo | Envia POST/GET/PUT/DELETE com cookie | Clica em Sair |
| Linha de interação | GET `/portal` | POST `/portal` | GET `/banco` | Evento de input no JavaScript | Rotas `/componentes` | GET `/logout` |
| Frontstage — resposta visível | Formulário do Portal | Redirecionamento para Banco ou mensagem de erro | Tabela, contagens e usuário conectado | Linhas são filtradas no navegador | Mensagem de sucesso ou erro em JSON/código HTTP | Redirecionamento ao Portal |
| Linha de visibilidade | A interface não mostra diretamente a lógica que executa o pedido |  |  |  |  |  |
| Backstage — lógica interna | Bottle resolve a rota | `Application.autenticar` consulta `UserRecord` e verifica hash | `Application.render_banco` obtém lista e soma quantidades | `main.js` compara texto das linhas | Controller valida sessão, chama `ComponentRecord` e modelo `Componente` | `Application.logout` encerra token |
| Processos de suporte | Servidor Bottle e templates | PBKDF2-HMAC-SHA256 + salt; `GerenciadorSessoes` cria token | Arquivo `componentes.json` | JavaScript no navegador e CSS | Validação de nome, categoria, quantidade e descrição; gravação JSON | Cookie `session_id` é removido |

## Arquitetura e responsabilidades
- **View:** `portal.tpl`, `banco.tpl` e `layout.tpl` apresentam as páginas.
- **Controller/rotas:** `route.py` trata login, logout, consulta e operações HTTP.
- **Application:** coordena autenticação, renderização, sessão e acesso aos registros.
- **Models:** `User_account`, `Componente`, `Sessao` e `GerenciadorSessoes`.
- **DataRecord:** classe base para ler/gravar listas de objetos em JSON.
- **UserRecord / ComponentRecord:** carregam, convertem e persistem contas e componentes.
- **Persistência:** `app/controllers/db/user_accounts.json` e `componentes.json`, criados durante a primeira execução.
- **Segurança da sessão:** token em cookie `session_id`, com atributos HttpOnly e SameSite=Lax; sessão expira em uma hora e fica em memória.

## Operações e respostas
| Operação | Método e rota | Resultado esperado |
|---|---|---|
| Login | POST `/portal` | Redireciona após autenticar; erro HTTP 401 em credenciais incorretas |
| Consulta JSON | GET `/componentes` | Lista os registros, exigindo sessão |
| CREATE | POST `/componentes` | HTTP 201; validação inválida retorna 400 |
| UPDATE | PUT `/componentes/<id>` | HTTP 200; ID não encontrado retorna 404 |
| DELETE | DELETE `/componentes/<id>` | HTTP 200; ID não encontrado retorna 404 |
| Logout | GET `/logout` | Encerra sessão, remove cookie e redireciona ao Portal |

## Linhas de falha e recuperação
- **Credenciais incorretas:** a tela Portal apresenta erro e o usuário pode tentar novamente.
- **Acesso sem sessão à API:** o controller responde HTTP 401.
- **Dados inválidos:** o modelo `Componente` valida campos; a rota responde HTTP 400.
- **ID inexistente:** UPDATE/DELETE respondem HTTP 404.
- **Sessão expirada:** o token deixa de ser reconhecido; o usuário precisa autenticar de novo.
- **Servidor reiniciado:** como as sessões são mantidas em memória, é necessário novo login; os dados do catálogo continuam nos JSON.

## Oportunidade de melhoria
Criar formulários web para CREATE, UPDATE e DELETE, mantendo as mesmas rotas e validações. Isso aproximaria as operações do usuário da interface que já oferece a consulta, diminuindo erros de comando e necessidade de conhecer HTTP/cURL.
