# Nível 3 — Jornada do usuário | TechStock BMVC

## Contexto
**Sistema:** TechStock — Catálogo de componentes eletrônicos  
**Persona:** funcionário/gerente que consulta e mantém o catálogo  
**Objetivo:** localizar componentes e manter os registros atualizados.

Esta jornada foi construída a partir do README, das rotas, modelos, controllers, templates e testes do repositório [techstock-bmvc](https://github.com/AbnerG1/techstock-bmvc).

## Jornada

| Etapa | 1. Acessar | 2. Autenticar | 3. Consultar catálogo | 4. Localizar item | 5. Manter cadastro | 6. Conferir e sair |
|---|---|---|---|---|---|---|
| Ação do usuário | Abre `/portal` | Informa usuário e senha | Acessa `/banco` após login | Digita nome/categoria no filtro | Envia CREATE/UPDATE/DELETE pelo terminal com cURL e cookie de sessão | Atualiza a página e usa Sair |
| Ponto de contato | Navegador | Formulário Portal | Página Banco | Campo de busca | Terminal Linux + API HTTP | Página Banco e link Sair |
| Resposta do sistema | Exibe o portal | Credenciais válidas geram sessão e redirecionam para Banco | Exibe tabela, total de tipos, unidades e usuário | Filtra localmente as linhas da tabela | Retorna mensagem/JSON e código HTTP | Lista reflete os dados persistidos; sessão é encerrada |
| Pensamento | “Onde entro?” | “Minhas credenciais estão corretas?” | “Quais itens existem?” | “Onde está o componente?” | “A alteração foi aceita?” | “O catálogo ficou atualizado?” |
| Emoção estimada | 3 | 3 | 4 | 4 | 2 | 4 |
| Dificuldade | Encontrar o endereço | Login incorreto retorna erro 401 | Entender que a página é consulta | Nenhuma quando o termo existe | Necessidade de conhecer terminal, endpoint e cookie | Precisar atualizar a página |
| Oportunidade | Link direto para o portal | Mensagem de erro clara | Explicar os campos e a consulta | Mensagem para busca sem resultado | Criar formulários gráficos para CRUD | Mostrar confirmação e atualizar a lista |

## Funcionalidades observadas
- Login pela rota `/portal`; sucesso redireciona para `/banco`.
- A página Banco exibe ID, nome, categoria, quantidade e descrição.
- O resumo apresenta quantidade de tipos cadastrados, soma das unidades e usuário conectado.
- O filtro da tabela busca texto de nome/categoria no navegador.
- CREATE: `POST /componentes`.
- READ: `GET /componentes` (JSON) e consulta visual em `/banco`.
- UPDATE: `PUT /componentes/<id>`.
- DELETE: `DELETE /componentes/<id>`.
- A página informa que cadastro, alteração e exclusão devem ser feitos pelo terminal Linux com cURL.

## Momentos de dor
1. As operações de manutenção não têm formulários visuais: exigem terminal, sintaxe cURL, cookie e endpoint.
2. A API bloqueia requisições sem autenticação (HTTP 401).
3. Validações inválidas retornam HTTP 400 e IDs inexistentes retornam HTTP 404.
4. Depois de uma operação, o usuário precisa atualizar a página Banco para conferir a lista.

## Oportunidades de melhoria
A principal melhoria de experiência seria oferecer formulários de cadastro, edição e exclusão dentro da interface, com confirmação antes de excluir e atualização da tabela após salvar. Isso é uma proposta, não uma funcionalidade atual do repositório.

## Curva emocional
Valores de 1 a 5 são hipóteses ilustrativas para a representação da jornada, não dados coletados com usuários.
