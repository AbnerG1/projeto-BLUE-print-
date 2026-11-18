# Roteiros para os quatro vídeos

**Limite do enunciado:** até cinco minutos por vídeo.  
**Dica:** grave a tela com o diagrama aberto e acompanhe o texto em voz natural. Não precisa decorar palavra por palavra.

## Nível 1 — Jornada do usuário do Desktop (aprox. 3–4 min)

“Olá, meu nome é Abner e vou apresentar a jornada do usuário do Sistema Desktop de Gestão e Caixa.

O perfil escolhido é o operador de caixa de um pequeno comércio. Ele precisa registrar a compra do cliente, receber o pagamento e garantir que o estoque seja atualizado.

A jornada começa no acesso ao sistema, em que o operador informa suas credenciais. Depois ele inicia uma nova venda e começa a inserir o código de barras ou identificador de cada produto.

A cada item, o sistema deve localizar o produto, apresentar o preço e somar o valor parcial. Esse processo se repete até que todos os itens sejam incluídos. Em seguida, o operador solicita a totalização para visualizar o valor final.

Na etapa de pagamento, o operador escolhe a forma de pagamento e confirma a transação. O sistema precisa validar que o valor pago seja suficiente. Se o pagamento for menor que o total, a venda não deve ser finalizada.

Também existem duas situações importantes durante a inclusão de produtos. Se o produto não for encontrado, o sistema informa o problema para que o operador confira o código. Se o estoque for insuficiente, o item não deve ser adicionado.

Quando tudo está correto, a venda é registrada, as quantidades são baixadas do estoque e um recibo é gerado.

A jornada mostra que os momentos mais delicados são localizar o produto, confirmar a disponibilidade e validar o pagamento. Por isso, as principais oportunidades são mensagens claras, total sempre visível e uma confirmação final.

Essa jornada foi construída a partir dos requisitos do projeto. As telas e integrações específicas ainda precisam ser conferidas na aplicação executável. Obrigado.”

## Nível 2 — Blueprint do Desktop (aprox. 3–4 min)

“Agora vou apresentar o blueprint do serviço de venda do Sistema Desktop de Gestão e Caixa.

Diferente da jornada, que mostra a experiência do operador, o blueprint mostra o que acontece por trás de cada etapa.

Na primeira etapa, o operador acessa o sistema e informa suas credenciais. Na parte visível existe a interação de login; internamente, o sistema valida o usuário antes de liberar a venda.

Depois, o operador inicia uma nova venda. Na interface, aparece o fluxo de atendimento. Por trás, o sistema prepara o registro da venda e os dados dos itens.

Quando os produtos são informados, a parte visível apresenta nome, preço e valor parcial. No backstage, o sistema consulta o catálogo, confere a quantidade disponível e impede que um produto inexistente ou sem estoque seja incluído.

Na totalização, o sistema calcula o valor final. Na etapa seguinte, o operador informa a forma de pagamento. Internamente, a regra de negócio verifica se o valor pago cobre o total, porque uma venda não pode ser concluída com pagamento insuficiente.

Por fim, o sistema registra a venda, atualiza o estoque e gera o recibo que será entregue ao cliente.

As linhas do blueprint ajudam a separar a ação do usuário, o contato visível com o sistema, as atividades internas e os processos de suporte, como catálogo, estoque e persistência de dados.

A principal oportunidade é garantir feedback em cada etapa e deixar explícito quando a venda foi concluída. Este blueprint representa o fluxo definido nos requisitos, sem afirmar integrações que não foram documentadas.”

## Nível 3 — Jornada do usuário do TechStock (aprox. 3–4 min)

“Este é o nível 3, a jornada do usuário do TechStock, um catálogo de componentes eletrônicos desenvolvido em Python com Bottle e organização MVC.

O perfil é um funcionário ou gerente que precisa consultar os componentes e manter as informações do catálogo.

A jornada começa na página Portal, no endereço barra portal. O usuário informa o login e a senha. Quando os dados estão corretos, o sistema cria uma sessão e redireciona para a página Banco.

Na página Banco, o usuário visualiza os componentes cadastrados. A tabela apresenta ID, nome, categoria, quantidade e descrição. Também existem indicadores com o número de tipos cadastrados, a soma das unidades e o usuário conectado.

Para encontrar um item, o usuário utiliza o campo de busca, que filtra as linhas da tabela pelo texto digitado.

Uma característica importante do TechStock é que a consulta é feita pela interface, mas as operações de cadastro, alteração e exclusão precisam ser executadas pelo terminal Linux, usando comandos cURL e o cookie de autenticação.

O sistema oferece as operações CREATE, READ, UPDATE e DELETE por rotas HTTP. Depois de executar uma alteração, o usuário atualiza a página Banco para confirmar o resultado.

Ao final, pode utilizar o link Sair para encerrar a sessão.

A principal dificuldade da jornada é a necessidade de usar o terminal para manter os dados. Uma melhoria seria incluir formulários gráficos, mantendo as mesmas validações e regras. Essa jornada representa as funcionalidades que foram conferidas no código do repositório.”

## Nível 4 — Blueprint do TechStock (aprox. 3–4 min)

“Por fim, vou apresentar o blueprint do TechStock. Ele conecta cada interação do usuário com as rotas, os controllers, os modelos e os dados internos do sistema.

Quando o usuário abre o Portal, o navegador faz uma requisição para a rota barra portal, tratada pelo Bottle.

No login, o usuário envia suas credenciais. Internamente, a classe Application consulta o UserRecord e verifica a senha armazenada como hash. Se estiver correta, o GerenciadorSessoes cria um token e a aplicação envia o cookie de sessão. O usuário então é direcionado à página Banco.

Na consulta, a aplicação carrega os componentes por meio do ComponentRecord e apresenta a tabela. O filtro de nome e categoria acontece no próprio navegador, usando o JavaScript da página.

Para cadastrar, consultar pela API, atualizar ou excluir, o usuário utiliza as rotas HTTP com cURL e envia o cookie de sessão. O controller verifica a autenticação, chama o ComponentRecord e o modelo Componente valida os campos antes da gravação.

Os registros ficam persistidos em arquivos JSON. A página Banco é a parte visual da consulta; as rotas e os models representam o processamento interno.

O blueprint também mostra as respostas de erro: acesso sem login retorna 401, dados inválidos retornam 400 e um ID inexistente retorna 404. A sessão expira depois de uma hora e é mantida em memória.

Com isso, o blueprint evidencia como interface, lógica, dados e processos de suporte trabalham juntos. A melhoria mais importante seria permitir o CRUD diretamente pela interface web, reduzindo a dependência do terminal.”

## Encerramento comum
“Essas foram as quatro entregas da atividade: duas relacionadas à jornada e ao blueprint do Sistema Desktop, e duas relacionadas à jornada e ao blueprint do TechStock BMVC. Obrigado pela atenção.”
