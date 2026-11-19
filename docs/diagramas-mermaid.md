# Diagramas

## Nível 1 — Jornada Desktop

~~~mermaid
flowchart TD
 A["Abrir o programa"] --> B{"Escolher perfil"}
 B --> C["Funcionário (Caixa)"]
 B --> G["Gerente"]
 C --> D["Iniciar venda"]
 D --> E["Adicionar produtos"]
 E --> F{"Produto disponível?"}
 F -- "Não" --> E1["Mostrar aviso e escolher outro item"]
 E1 --> E
 F -- "Sim" --> H["Atualizar carrinho e total"]
 H --> I["Conferir compra"]
 I --> J["Receber pagamento"]
 J --> K["Concluir venda"]
 K --> L["Registrar venda e atualizar estoque"]
 L --> M["Emitir nota fiscal"]
 G --> N["Abrir painel administrativo"]
 N --> O["Cadastrar ou atualizar produtos"]
 O --> P["Consultar estoque"]
 P --> Q["Abrir relatório diário"]
 Q --> R["Ver quantidade de vendas e total arrecadado"]
~~~

## Nível 2 — Blueprint Desktop

~~~mermaid
flowchart TB
 subgraph U["Ações dos usuários"]
 U1["Funcionário: escolher perfil"] --> U2["Iniciar venda"]
 U2 --> U3["Adicionar produtos"]
 U3 --> U4["Conferir total e receber pagamento"]
 U4 --> U5["Concluir venda"]
 G1["Gerente: escolher perfil"] --> G2["Cadastrar ou atualizar produtos"]
 G2 --> G3["Consultar estoque"]
 G3 --> G4["Abrir relatório diário"]
 end
 subgraph F["Frontstage — o que aparece"]
 F1["Painel do funcionário"] --> F2["Tela de venda e carrinho"]
 F2 --> F3["Total e finalização"]
 F3 --> F4["Nota fiscal"]
 G5["Painel administrativo"] --> G6["Cadastro e listagem de produtos"]
 G6 --> G7["Relatório: vendas do dia e total arrecadado"]
 end
 subgraph B["Backstage — o que acontece"]
 B1["Preparar venda"] --> B2["Consultar produto e estoque"]
 B2 --> B3["Calcular total"]
 B3 --> B4["Processar pagamento"]
 B4 --> B5["Registrar venda e itens"]
 B5 --> B6["Atualizar estoque"]
 B6 --> B7["Gerar nota fiscal"]
 G8["Validar dados do produto"] --> G9["Salvar alterações do catálogo"]
 G9 --> G10["Consultar vendas registradas"]
 G10 --> G11["Calcular resumo diário"]
 end
 subgraph S["Suporte"]
 S1["Interface Tkinter e controle de acesso"]
 S2["Regras de venda e estoque"]
 S3["SQLite: produtos, vendas e itens vendidos"]
 S4["Rotina de emissão da nota fiscal"]
 end
 U1 --> F1
 U2 --> F2
 U3 --> F2
 U4 --> F3
 U5 --> F4
 G1 --> G5
 G2 --> G6
 G3 --> G6
 G4 --> G7
 F1 --> B1
 F2 --> B2
 F3 --> B3
 F4 --> B7
 G6 --> G8
 G7 --> G10
 B1 --> S1
 B2 --> S2
 B5 --> S3
 B7 --> S4
 G9 --> S3
 G11 --> S3
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

## Referência de arquitetura — BMVC

O projeto inicial disponibilizado pelo professor ajuda a visualizar a separação entre rotas, aplicação, modelos, registros e páginas. No TechStock, os nomes são diferentes, mas a divisão de responsabilidades pode ser vista no diagrama abaixo.

~~~mermaid
classDiagram
 class route_py {
   +Bottle app
   +portal()
   +login()
   +banco()
   +listar_componentes()
   +criar_componente()
   +atualizar_componente()
   +remover_componente()
 }
 class Application {
   +users UserRecord
   +componentes ComponentRecord
   +sessoes GerenciadorSessoes
   +autenticar()
   +usuario_logado()
   +logout()
   +render_portal()
   +render_banco()
 }
 class DataRecord {
   <<abstract>>
   +models
   +read()
   +save()
   +converter()*
 }
 class UserRecord {
   +buscar()
   +converter()
 }
 class ComponentRecord {
   +listar()
   +buscar()
   +criar()
   +atualizar()
   +remover()
   +converter()
 }
 class User_account {
   +username
   +confere_senha()
 }
 class Componente {
   +id
   +nome
   +categoria
   +quantidade
   +descricao
   +validar()
   +to_dict()
   +from_dict()
 }
 class GerenciadorSessoes {
   +criar()
   +usuario()
   +encerrar()
 }
 route_py --> Application : encaminha requisições
 Application *-- UserRecord
 Application *-- ComponentRecord
 Application *-- GerenciadorSessoes
 UserRecord --|> DataRecord
 ComponentRecord --|> DataRecord
 UserRecord --> User_account : cria e consulta
 ComponentRecord --> Componente : cria e consulta
 DataRecord ..> JSON : lê e grava
~~~
