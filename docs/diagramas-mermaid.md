# Diagramas

## Nível 1 — Jornada Desktop

~~~mermaid
flowchart LR
 A["Abrir o programa"] --> B["Escolher Funcionário (Caixa)"]
 B --> C["Iniciar nova venda"]
 C --> D["Adicionar produto"]
 D --> E{"Produto encontrado e disponível?"}
 E -- "Não" --> F["Mostrar aviso e corrigir a seleção"]
 F --> D
 E -- "Sim" --> G["Incluir item e atualizar total"]
 G --> H{"Há mais produtos?"}
 H -- "Sim" --> D
 H -- "Não" --> I["Conferir o carrinho e o total"]
 I --> J["Fechar ou cancelar a venda"]
 J --> K["Registrar venda e atualizar estoque"]
~~~

## Nível 2 — Blueprint Desktop

~~~mermaid
flowchart TB
 subgraph U["Ações do Operador de Caixa"]
 U1["Escolher Funcionário (Caixa)"] --> U2["Iniciar nova venda"]
 U2 --> U3["Adicionar produtos"]
 U3 --> U4["Conferir carrinho e total"]
 U4 --> U5["Fechar ou cancelar"]
 end
 subgraph F["Frontstage — o que o operador vê"]
 F1["Tela de seleção de perfil"] --> F2["Área do funcionário"]
 F2 --> F3["Tela Nova Venda"]
 F3 --> F4["Itens e total atualizado"]
 F4 --> F5["Retorno do fechamento ou cancelamento"]
 end
 subgraph B["Backstage — o que acontece internamente"]
 B1["Definir perfil ativo"] --> B2["Preparar carrinho"]
 B2 --> B3["Consultar produto e estoque"]
 B3 --> B4["Somar os itens"]
 B4 --> B5["Registrar venda e baixar estoque"]
 end
 subgraph S["Processos de suporte"]
 S1["Painel administrativo e controle de acesso"] --> S2["Cadastro e catálogo de produtos"]
 S2 --> S3["SQLite: produtos, vendas e itens_venda"]
 end
 U1 --> F1
 U2 --> F2
 U3 --> F3
 U4 --> F4
 U5 --> F5
 F1 --> B1
 F2 --> B2
 F3 --> B3
 F4 --> B4
 F5 --> B5
 B1 --> S1
 B3 --> S2
 B5 --> S3
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
