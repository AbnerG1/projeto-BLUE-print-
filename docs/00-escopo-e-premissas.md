# Escopo e fontes

O trabalho reúne quatro etapas e usa dois sistemas que já foram desenvolvidos em atividades da disciplina.

| Nível | Sistema | Entrega |
|---|---|---|
| 1 | Sistema Desktop de Gestão e Caixa | Jornada do usuário |
| 2 | Sistema Desktop de Gestão e Caixa | Blueprint do serviço |
| 3 | TechStock BMVC | Jornada do usuário |
| 4 | TechStock BMVC | Blueprint do serviço |

## Materiais consultados

- Estudo de caso do Sistema Desktop de Gestão e Caixa (Módulo 01).
- [Projeto Desktop](https://github.com/AbnerG1/Projeto-desktop).
- Demonstração do Desktop enviada pelo aluno.
- [TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc): rotas, modelos, controllers, páginas, JavaScript e testes.
- [BMVC — projeto inicial disponibilizado pelo professor](https://github.com/hgmachine/bmvc_start_from_this).

## Como os materiais foram usados

O projeto inicial BMVC serviu como referência para entender a organização esperada na disciplina: rotas no `route.py`, coordenação das páginas pela classe `Application`, modelos separados, camada de acesso aos dados e arquivos de interface. O TechStock mantém sua implementação própria, mas segue essa separação de responsabilidades.

No Desktop, a demonstração e as informações confirmadas pelo aluno mostram dois perfis. O Funcionário (Caixa) registra as compras, adiciona produtos, fecha vendas e emite a nota fiscal. O Gerente administra os produtos, acompanha o estoque e consulta o relatório diário, que informa a quantidade de vendas e o total arrecadado.

O módulo de dados do Desktop usa SQLite, com registros de produtos, vendas e itens vendidos. A rotina de venda grava os itens e o total e atualiza o estoque.

No TechStock, o fluxo foi conferido diretamente no código. O usuário entra por `/portal` e consulta os componentes em `/banco`. A busca é feita no navegador. Também existe a rota `GET /componentes`; cadastro, alteração e exclusão são feitos por requisições cURL autenticadas.

Os dados do TechStock ficam em arquivos JSON. As sessões são mantidas em memória, expiram após uma hora e precisam ser refeitas quando o servidor é reiniciado.
