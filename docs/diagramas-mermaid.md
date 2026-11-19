# Diagramas editáveis

Preparei os diagramas abaixo para acompanhar cada nível da atividade. Eles podem ser visualizados diretamente no GitHub ou copiados para um editor que aceite Mermaid.

## Nível 1 — Jornada Desktop

~~~mermaid
flowchart LR
 A["Acessar o sistema"] --> B["Iniciar uma venda"]
 B --> C["Informar o produto"]
 C --> D{"Produto foi localizado?"}
 D -- "Não" --> E["Conferir o código e tentar novamente"]
 E --> C
 D -- "Sim" --> F{"Há estoque suficiente?"}
 F -- "Não" --> G["Aviso de estoque insuficiente"]
 G --> C
 F -- "Sim" --> H["Incluir item e atualizar parcial"]
 H --> I{"Há mais produtos?"}
 I -- "Sim" --> C
 I -- "Não" --> J["Conferir o total"]
 J --> K["Escolher forma e confirmar pagamento"]
 K --> L{"Valor pago cobre o total?"}
 L -- "Não" --> M["Informar quanto falta"]
 M --> K
 L -- "Sim" --> N["Registrar venda"]
 N --> O["Atualizar estoque"]
 O --> P["Gerar e entregar recibo"]
~~~

## Nível 2 — Blueprint Desktop

~~~mermaid
flowchart TB
 subgraph U["Ações do Operador de Caixa"]
 U1["Entrar no sistema"] --> U2["Iniciar a venda"]
 U2 --> U3["Informar os produtos"]
 U3 --> U4["Conferir o total"]
 U4 --> U5["Confirmar o pagamento"]
 U5 --> U6["Entregar o recibo"]
 end
 subgraph F["Frontstage — o que o operador vê"]
 F1["Retorno do login"] --> F2["Área de venda"]
 F2 --> F3["Produto, preço e parcial"]
 F3 --> F4["Total da compra"]
 F4 --> F5["Resultado do pagamento"]
 F5 --> F6["Confirmação e recibo"]
 end
 subgraph B["Backstage — o que acontece internamente"]
 B1["Validar usuário"] --> B2["Preparar venda"]
 B2 --> B3["Consultar catálogo e estoque"]
 B3 --> B4["Calcular total"]
 B4 --> B5["Conferir valor recebido"]
 B5 --> B6["Registrar venda e atualizar estoque"]
 end
 subgraph S["Processos de suporte"]
 S1["Cadastro de usuários"] --> S2["Catálogo de produtos"]
 S2 --> S3["Regras de negócio"]
 S3 --> S4["Persistência e geração do recibo"]
 end
 U1 --> F1
 U2 --> F2
 U3 --> F3
 U4 --> F4
 U5 --> F5
 U6 --> F6
 F1 --> B1
 F2 --> B2
 F3 --> B3
 F4 --> B4
 F5 --> B5
 B5 --> B6
 B6 --> F6
 B1 --> S1
 B3 --> S2
 B5 --> S3
 B6 --> S4
~~~

## Nível 3 — Jornada TechStock

~~~mermaid
flowchart LR
 A["Abrir /portal"] --> B["Informar usuário e senha"]
 B --> C{"Credenciais corretas?"}
 C -- "Não" --> D["Ver mensagem de erro"]
 D --> B
 C -- "Sim" --> E["Acessar /banco"]
 E --> F["Consultar tabela e indicadores"]
 F --> G["Filtrar a tabela no navegador"]
 G --> H{"Precisa alterar o catálogo?"}
 H -- "Não" --> I["Sair"]
 H -- "Sim" --> J["Enviar cURL autenticado"]
 J --> K{"Requisição aceita?"}
 K -- "Não" --> L["Conferir erro 400, 401 ou 404"]
 L --> J
 K -- "Sim" --> M["Atualizar /banco e conferir"]
 M --> I
~~~

## Nível 4 — Blueprint TechStock

~~~mermaid
flowchart TB
 subgraph U["O que a pessoa faz"]
 U1["Abrir Portal"] --> U2["Enviar login"]
 U2 --> U3["Consultar Banco"]
 U3 --> U4["Filtrar a tabela"]
 U4 --> U5["Manter catálogo pelo cURL"]
 U5 --> U6["Conferir e sair"]
 end
 subgraph F["Interface e rotas"]
 F1["GET /portal"] --> F2["POST /portal"]
 F2 --> F3["GET /banco"]
 F3 --> F4["Filtro em main.js"]
 F4 --> F5["GET /componentes ou POST/PUT/DELETE"]
 F5 --> F6["GET /logout"]
 end
 subgraph B["Lógica interna"]
 B1["Application.autenticar"] --> B2["UserRecord e User_account"]
 B2 --> B3["GerenciadorSessoes"]
 B4["Application.render_banco"] --> B5["ComponentRecord.listar"]
 B6["Verificar sessão"] --> B7["Validar dados em Componente"]
 B7 --> B8["ComponentRecord grava ou remove"]
 end
 subgraph S["Dados e suporte"]
 S1["Bottle e templates"]
 S2["Hash da senha e salt"]
 S3["Token de sessão em memória"]
 S4["Arquivos JSON"]
 end
 U1 --> F1
 U2 --> F2
 U3 --> F3
 U4 --> F4
 U5 --> F5
 U6 --> F6
 F2 --> B1
 B1 --> B2
 B2 --> S2
 B2 --> B3
 B3 --> S3
 F3 --> B4
 B4 --> B5
 B5 --> S4
 F5 --> B6
 B6 --> B7
 B7 --> B8
 B8 --> S4
 F1 --> S1
~~~

## Uma observação sobre os desenhos

Os diagramas do Desktop mostram o fluxo definido na documentação do Módulo 01. Os do TechStock representam rotas e classes que foram conferidas no código. Assim, os desenhos deixam visualmente clara a diferença entre um fluxo especificado e um fluxo observado na implementação.
