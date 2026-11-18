# Diagramas editáveis

Os diagramas Mermaid abaixo representam os quatro níveis. Para visualizar, abra este arquivo no GitHub ou copie o bloco para um editor compatível com Mermaid.

## Nível 1 — Jornada Desktop

```mermaid
flowchart LR
 A["Acesso e login"] --> B["Iniciar nova venda"]
 B --> C["Inserir produto"]
 C --> D{"Produto localizado?"}
 D -- Não --> E["Aviso: produto não encontrado"]
 E --> C
 D -- Sim --> F{"Estoque suficiente?"}
 F -- Não --> G["Aviso: estoque insuficiente"]
 G --> C
 F -- Sim --> H["Adicionar item e somar parcial"]
 H --> I{"Há mais itens?"}
 I -- Sim --> C
 I -- Não --> J["Totalizar venda"]
 J --> K["Selecionar forma de pagamento"]
 K --> L{"Valor pago >= total?"}
 L -- Não --> M["Informar valor restante"]
 M --> K
 L -- Sim --> N["Registrar venda"]
 N --> O["Baixar estoque"]
 O --> P["Gerar e entregar recibo"]
```

## Nível 2 — Blueprint Desktop

```mermaid
flowchart TB
 subgraph U["Ações do usuário"]
 U1["Entrar no sistema"] --> U2["Iniciar venda e inserir produtos"]
 U2 --> U3["Conferir total e informar pagamento"]
 U3 --> U4["Entregar recibo"]
 end
 subgraph F["Frontstage - contato visível"]
 F1["Login"] --> F2["Exibição de produtos e parcial"]
 F2 --> F3["Total e validação do pagamento"]
 F3 --> F4["Confirmação e recibo"]
 end
 subgraph B["Backstage - ações internas"]
 B1["Autenticar usuário"] --> B2["Consultar catálogo e estoque"]
 B2 --> B3["Calcular total e validar pagamento"]
 B3 --> B4["Registrar venda e atualizar estoque"]
 end
 subgraph S["Suporte"]
 S1["Cadastro de usuários"] --> S2["Catálogo e persistência"]
 S2 --> S3["Regras de negócio"]
 S3 --> S4["Geração de comprovante"]
 end
 U1 --> F1
 U2 --> F2
 U3 --> F3
 U4 --> F4
 F1 --> B1
 F2 --> B2
 F3 --> B3
 F4 --> B4
 B1 --> S1
 B2 --> S2
 B3 --> S3
 B4 --> S4
```

## Nível 3 — Jornada TechStock

```mermaid
flowchart LR
 A["Abrir /portal"] --> B["Informar credenciais"]
 B --> C{"Login válido?"}
 C -- Não --> D["Erro 401 e nova tentativa"]
 D --> B
 C -- Sim --> E["Redirecionar para /banco"]
 E --> F["Visualizar tabela e indicadores"]
 F --> G["Filtrar por nome/categoria"]
 G --> H{"Precisa alterar o catálogo?"}
 H -- Não --> I["Sair"]
 H -- Sim --> J["Executar cURL com cookie"]
 J --> K{"Requisição válida?"}
 K -- Não --> L["Exibir erro 400/401/404"]
 L --> J
 K -- Sim --> M["Atualizar /banco e conferir"]
 M --> I
```

## Nível 4 — Blueprint TechStock

```mermaid
flowchart TB
 subgraph U["Usuário"]
 U1["Abrir Portal"] --> U2["Enviar login"] --> U3["Consultar e filtrar Banco"]
 U3 --> U4["Enviar operação CRUD via cURL"]
 U4 --> U5["Conferir lista e sair"]
 end
 subgraph F["Interface e rotas"]
 F1["GET /portal"] --> F2["POST /portal"]
 F2 --> F3["GET /banco"]
 F3 --> F4["Campo de busca - main.js"]
 F4 --> F5["POST/GET/PUT/DELETE /componentes"]
 F5 --> F6["GET /logout"]
 end
 subgraph B["Lógica interna"]
 B1["Application.autenticar"] --> B2["UserRecord + User_account"]
 B2 --> B3["GerenciadorSessoes"]
 B4["Application.render_banco"] --> B5["ComponentRecord.listar"]
 B6["Controller valida sessão"] --> B7["Componente valida dados"]
 B7 --> B8["ComponentRecord salva ou remove"]
 end
 subgraph S["Dados e suporte"]
 S1["Bottle + templates"] 
 S2["Hash PBKDF2-HMAC-SHA256"]
 S3["Token em memória e cookie"]
 S4["componentes.json / user_accounts.json"]
 end
 U1 --> F1
 U2 --> F2
 U3 --> F3
 U3 --> F4
 U4 --> F5
 U5 --> F6
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
```
