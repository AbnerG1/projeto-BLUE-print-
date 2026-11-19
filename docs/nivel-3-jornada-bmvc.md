# Nível 3 — Jornada do usuário | TechStock BMVC

Considerei uma pessoa que trabalha com o catálogo de componentes eletrônicos e precisa consultar os itens ou atualizar seus registros.

## Jornada no TechStock

| Etapa | O que a pessoa faz | Resposta do sistema | Onde pode ter dificuldade |
|---|---|---|---|
| 1. Acessar | Abre /portal no navegador. | Apresenta a tela de login. | O servidor pode não estar iniciado ou o endereço pode estar incorreto. |
| 2. Entrar | Informa usuário e senha. | Com os dados corretos, abre /banco. Caso contrário, mostra uma mensagem de erro. | Digitar uma credencial incorreta. |
| 3. Consultar | Abre a lista de componentes. | Mostra ID, nome, categoria, quantidade e descrição. Também apresenta o número de tipos cadastrados e o total de unidades. | Ter muitos itens para conferir. |
| 4. Buscar | Digita um termo no campo de busca. | Filtra as linhas da tabela no próprio navegador. | Não encontrar o item pelo termo digitado. |
| 5. Atualizar o catálogo | Usa o terminal e o cURL para cadastrar, alterar ou excluir um componente. | A API retorna o resultado da operação e o código HTTP. | Precisar conhecer os comandos e manter o cookie da sessão. |
| 6. Conferir e sair | Atualiza a página e seleciona Sair. | Mostra os dados atualizados e encerra a sessão. | Esquecer de atualizar a página antes de conferir. |

## Como o TechStock funciona hoje

A consulta pode ser feita diretamente pela página Banco. Também existe a rota GET /componentes, que retorna os dados em JSON.

O cadastro é feito por POST /componentes, a alteração por PUT /componentes/{id} e a exclusão por DELETE /componentes/{id}. Essas três operações exigem autenticação e são executadas pelo terminal com cURL; a página não tem botões para elas.

Na primeira execução, o catálogo já vem com três exemplos: um resistor de 220 Ω, um capacitor de 100 µF e uma placa ESP32 DevKit.

O campo de busca sugere procurar por nome ou categoria, mas o código atual filtra o texto completo de cada linha. Por isso, também pode encontrar termos presentes no ID, na quantidade ou na descrição.

O ponto que mais dificulta o uso é ter que sair da página e recorrer ao terminal para fazer alterações no catálogo.
