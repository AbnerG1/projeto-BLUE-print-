# Nível 1 — Jornada do usuário | Desktop App

## Contexto
**Sistema:** Sistema Desktop de Gestão e Caixa  
**Persona:** operador de caixa de um pequeno comércio  
**Objetivo:** concluir uma compra com rapidez, registrar o pagamento e garantir que o estoque seja atualizado.

A jornada representa o fluxo especificado no estudo de caso do Módulo 01. Ela não afirma que as telas já estejam implementadas.

## Jornada

| Etapa | 1. Acesso | 2. Iniciar venda | 3. Incluir produtos | 4. Conferir total | 5. Receber pagamento | 6. Finalizar |
|---|---|---|---|---|---|---|
| Ação do usuário | Informa usuário e senha | Abre Nova Venda | Digita/consulta código ou identificador e repete para cada item | Solicita a totalização | Escolhe forma e informa/confirma valor pago | Confirma a operação e entrega o recibo |
| Resposta esperada | Sistema autentica | Exibe área de venda | Localiza produto, mostra preço e soma ao parcial | Exibe valor final | Verifica valor pago em relação ao total | Registra venda, baixa estoque e gera recibo |
| Pensamento | “Preciso entrar no caixa.” | “Vou iniciar o atendimento.” | “Os itens estão corretos?” | “Qual é o valor da compra?” | “O pagamento cobre o total?” | “A compra foi concluída?” |
| Emoção | Expectativa | Foco | Atenção | Segurança ou dúvida | Tensão moderada | Alívio |
| Dificuldade | Esquecer credenciais | Não encontrar a função | Produto não encontrado ou estoque insuficiente | Divergência de preço/quantidade | Valor pago inferior ao total | Falta de confirmação clara |
| Oportunidade | Login simples e mensagem objetiva | Acesso direto a Nova Venda | Busca rápida, validação e mensagens claras | Total sempre visível | Informar diferença restante e impedir fechamento incorreto | Confirmar baixa no estoque e apresentar recibo |

## Curva emocional qualitativa

| Etapa | Acesso | Iniciar | Produtos | Total | Pagamento | Finalização |
|---|---:|---:|---:|---:|---:|---:|
| Satisfação estimada | 3 | 4 | 3 | 4 | 3 | 5 |

Escala ilustrativa de 1 (frustração) a 5 (satisfação), usada para comunicar a hipótese da jornada. Não é resultado de pesquisa com usuários.

## Momentos críticos
1. **Produto inexistente:** o sistema informa que o produto não está no catálogo; o operador verifica o identificador e tenta novamente.
2. **Estoque insuficiente:** o sistema alerta que não há quantidade disponível e o item não entra na compra.
3. **Pagamento abaixo do total:** a regra RN01 impede finalizar a venda se o valor pago for menor que o total.
4. **Estoque zerado:** a regra RN02 impede adicionar à lista de compras produto sem estoque.

## Resultado esperado
Uma jornada clara permite ao operador passar do login ao recibo sem perder o controle dos itens. Os pontos mais sensíveis são a localização do produto, a disponibilidade no estoque e a validação do pagamento.

## Limite da análise
Os passos vêm dos requisitos do Desktop. As telas específicas, mensagens visuais, dispositivo de pagamento e integração de emissão de recibo precisam ser confirmados na aplicação executável antes de serem apresentados como funcionalidades já implementadas.
