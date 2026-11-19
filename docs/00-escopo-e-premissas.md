# Escopo, fontes e premissas

## Para que serve este material

A atividade pede duas ferramentas de Design de Serviço — jornada do usuário e blueprint — aplicadas a dois projetos. Organizei o trabalho em quatro níveis para deixar claro o que pertence a cada sistema e evitar que os fluxos se misturem.

## Divisão dos níveis

| Nível | Sistema | Quem está no centro | Entrega |
|---|---|---|---|
| 1 | Sistema Desktop de Gestão e Caixa | Operador de Caixa | Jornada do usuário |
| 2 | Sistema Desktop de Gestão e Caixa | Operador de Caixa | Blueprint do serviço |
| 3 | TechStock BMVC | Pessoa responsável pelo catálogo | Jornada do usuário |
| 4 | TechStock BMVC | Pessoa responsável pelo catálogo | Blueprint do serviço |

O Desktop e o TechStock não são partes de um mesmo aplicativo. O BLUE print é apenas o espaço onde reuni os documentos desta atividade; os códigos continuam nos seus repositórios de origem.

## Materiais usados

1. **Estudo de caso do Sistema Desktop de Gestão e Caixa (Módulo 01):** descreve os atores Operador de Caixa e Gerente, o registro de venda, o gerenciamento de estoque, as situações de produto inexistente e estoque insuficiente e as regras de pagamento.
2. **[Repositório Projeto-desktop](https://github.com/AbnerG1/Projeto-desktop):** contém os materiais anteriores do projeto Desktop.
3. **[Repositório TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc):** consultei o README, as rotas Bottle, os modelos, os controllers, os templates, o JavaScript e os testes.
4. **Enunciado da atividade:** imagem compartilhada na conversa, com os quatro níveis e o limite de até cinco minutos por vídeo.

## O que os mapas representam

### Desktop — níveis 1 e 2

A referência disponível é a especificação do Módulo 01. Ela descreve o fluxo esperado: entrar no sistema, iniciar uma venda, localizar os produtos, calcular o total, receber o pagamento, atualizar o estoque e gerar um recibo.

Não consegui confirmar, apenas com esses materiais, todas as telas e integrações da versão executável. Por isso, os mapas do Desktop devem ser entendidos como uma representação do serviço definido nos requisitos, e não como uma auditoria da aplicação pronta.

A especificação também não define uma integração com banco, maquininha ou adquirente. O blueprint mostra a etapa de pagamento sem presumir qual tecnologia é usada para processá-lo.

### TechStock — níveis 3 e 4

Aqui foi possível conferir o fluxo no próprio código. O usuário acessa /portal, faz login e é direcionado para /banco, onde consulta os componentes. O filtro atua na tabela já carregada no navegador.

A consulta também pode ser feita pela rota GET /componentes, que retorna JSON. Para cadastrar, alterar ou excluir componentes, o projeto usa requisições autenticadas feitas pelo cURL no terminal. Essas operações não aparecem como formulários na interface web.

Os dados do catálogo e das contas ficam em arquivos JSON. A sessão, por outro lado, fica em memória, expira depois de uma hora e precisa ser refeita quando o servidor é reiniciado.

## Diferença entre jornada e blueprint

- **Jornada do usuário:** acompanha a experiência de quem usa o sistema, do começo ao fim, incluindo dúvidas, dificuldades e oportunidades de melhoria.
- **Blueprint do serviço:** mostra como essa experiência é sustentada. Além do que o usuário faz e vê, entram as atividades internas e os recursos necessários para entregar o serviço.

## Melhorias que poderiam ser consideradas

As sugestões abaixo são ideias para evoluir os projetos, não recursos que estou afirmando que já existem.

- **Desktop:** deixar o resultado de cada etapa mais claro, facilitar a correção de um código de produto e mostrar quanto falta pagar quando o valor recebido é menor que o total.
- **TechStock:** oferecer telas de cadastro, edição e exclusão para que a manutenção do catálogo não dependa do terminal.
