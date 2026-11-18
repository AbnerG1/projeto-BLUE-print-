# Nível 2 — Blueprint do serviço | Desktop App

## Escopo do serviço
**Serviço:** atendimento e registro de venda em um pequeno comércio.  
**Ator principal:** Operador de Caixa.  
**Atores de apoio:** Gerente (cadastro e acompanhamento do estoque) e cliente (participa da compra, sem interação direta especificada com o sistema).

O blueprint detalha o fluxo de venda descrito nos requisitos do Módulo 01.

## Blueprint por etapa

| Camada | 1. Acesso | 2. Início | 3. Produtos | 4. Totalização | 5. Pagamento | 6. Conclusão |
|---|---|---|---|---|---|---|
| Evidência física | Computador do caixa, teclado | Tela/área Nova Venda (prevista) | Produto, etiqueta ou código | Lista de itens e total (previstos) | Dinheiro/cartão/outro meio escolhido | Recibo/comprovante |
| Ação do usuário | Operador informa credenciais | Abre nova venda | Informa código/identificador de cada item | Solicita fechamento da lista | Seleciona forma e confirma o pagamento | Entrega o recibo ao cliente |
| Linha de interação | Envio de credenciais | Comando para iniciar | Consulta/retorno de produto | Solicitação de total | Confirmação do pagamento | Confirmação de venda finalizada |
| Frontstage — interação visível | Tela de login | Interface apresenta fluxo de venda | Sistema exibe produto, preço e parcial | Sistema exibe total | Sistema informa resultado da validação | Sistema apresenta resultado e recibo |
| Linha de visibilidade | A partir daqui o cliente/operador não vê a lógica interna |  |  |  |  |  |
| Backstage — ações internas | Validar usuário | Preparar registro da venda | Consultar catálogo e conferir saldo | Calcular total | Conferir valor pago >= total e registrar pagamento | Persistir venda e atualizar quantidade |
| Processos de suporte | Cadastro de usuários | Dados da venda/itens | Catálogo e controle de estoque | Regras de preço e cálculo | Regras de negócio RN01 | Persistência, baixa de estoque e geração do recibo |

## Linhas de apoio e exceções
- **Autenticação:** o operador precisa estar logado para abrir a venda.
- **Produto não encontrado:** o sistema informa o problema; o operador confere o código e retorna à inclusão.
- **Estoque insuficiente:** o sistema alerta e não adiciona o item.
- **Pagamento insuficiente:** a venda não é finalizada enquanto o valor pago for menor que o total (RN01).
- **Estoque zerado:** o produto não pode entrar na lista de compras (RN02).

## Backstage e suporte
O serviço depende de um catálogo de produtos atualizado, disponibilidade de estoque, cálculo consistente dos totais, validação do pagamento e gravação da venda. O gerente é responsável pela gestão/cadastro dos produtos e pelo acompanhamento do estoque, conforme o estudo de caso.

## Pontos de falha e melhorias
| Risco | Consequência | Melhoria sugerida |
|---|---|---|
| Identificador incorreto | Produto não localizado | Mostrar mensagem específica e manter o foco no campo |
| Estoque desatualizado | Tentativa de vender item indisponível | Conferir saldo no momento de incluir e finalizar |
| Valor recebido menor | Fechamento incorreto | Bloquear conclusão e mostrar valor restante |
| Falta de confirmação | Dúvida sobre a conclusão | Exibir status final e permitir reimpressão do recibo, se suportado |

## Limite de evidência
As camadas de interação e suporte descrevem o serviço esperado conforme os requisitos. Não foi possível verificar no material acessível a implementação de telas concretas, integração com dispositivo de pagamento ou mecanismo de impressão; esses elementos devem ser apresentados como evidências/etapas previstas, não como recursos já comprovados.
