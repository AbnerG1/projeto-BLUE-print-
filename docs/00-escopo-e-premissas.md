# Escopo e fontes

O trabalho foi dividido em quatro níveis, usando dois projetos diferentes.

| Nível | Sistema | Perfil | Entrega |
|---|---|---|---|
| 1 | Sistema Desktop de Gestão e Caixa | Operador de Caixa | Jornada do usuário |
| 2 | Sistema Desktop de Gestão e Caixa | Operador de Caixa | Blueprint |
| 3 | TechStock BMVC | Pessoa que consulta o catálogo | Jornada do usuário |
| 4 | TechStock BMVC | Pessoa que consulta e mantém o catálogo | Blueprint |

## Materiais consultados

- Estudo de caso do Sistema Desktop de Gestão e Caixa (Módulo 01).
- [Projeto Desktop](https://github.com/AbnerG1/Projeto-desktop).
- [TechStock BMVC](https://github.com/AbnerG1/techstock-bmvc): README, rotas, modelos, controllers, páginas, JavaScript e testes.

## Sobre os mapas

A jornada mostra o caminho percorrido pelo usuário e os pontos em que ele pode encontrar dificuldade. O blueprint acrescenta o que acontece por trás da interface para que cada etapa funcione.

No Desktop, usei o fluxo descrito no estudo de caso: login, início da venda, inclusão de produtos, totalização, pagamento, atualização do estoque e recibo. Os materiais disponíveis descrevem o comportamento esperado, mas não permitiram confirmar todas as telas e integrações da versão executável. Por isso, os níveis 1 e 2 representam o serviço previsto nos requisitos.

No TechStock, foi possível conferir as etapas diretamente no código. O usuário entra por /portal e consulta os componentes em /banco. O filtro é feito no navegador. A consulta também existe pela rota GET /componentes; já o cadastro, a alteração e a exclusão são feitos por requisições cURL autenticadas.

Os dados do TechStock ficam em arquivos JSON. As sessões são mantidas em memória, expiram após uma hora e precisam ser refeitas quando o servidor é reiniciado.
