# Baozi Store - API REST

Trabalho de Desenvolvimento Web Back-End (UNINTER) - Gabriel Henrique Alves Lima - RU 5279626

API REST em **Java + Spring Boot + Spring Data JPA + MySQL** para controle de clientes, produtos e pedidos
da Baozi Store (pãozinho chinês).

## Como rodar

1. Tenha instalados **Java 17+**, **Maven** e um **MySQL 8** em execução na porta 3306
   (ou suba um com `docker compose up -d`).
2. Se o seu MySQL tiver outro usuário/senha, ajuste `src/main/resources/application.properties`
   ou defina as variáveis de ambiente `DB_USER` e `DB_PASSWORD` (padrão: `root` / `root`).
3. Rode: `mvn spring-boot:run`  (a API sobe em http://localhost:8080 e cria o banco `baozi_store` e as tabelas sozinha).

Para testar sem MySQL: `mvn spring-boot:run -Dspring-boot.run.profiles=h2`

## Endpoints

| Recurso  | POST | GET (todos) | GET por id | PUT (opcional) | DELETE |
|----------|------|-------------|------------|----------------|--------|
| Clientes | `/clientes` | `/clientes` | `/clientes/{id}` | `/clientes/{id}` | `/clientes/{id}` |
| Produtos | `/produtos` | `/produtos` | `/produtos/{id}` | `/produtos/{id}` | `/produtos/{id}` |
| Pedidos  | `/pedidos`  | `/pedidos`  | `/pedidos/{id}`  | `/pedidos/{id}`  | `/pedidos/{id}`  |

Exemplos de corpo:

```json
// POST /clientes
{ "nome": "Gabriel5279626", "clienteDesde": "2026-10-05" }

// POST /produtos
{ "nome": "Bolinho de feijão doce", "preco": 6.50, "estoque": true }

// POST /pedidos
{ "cliente": { "id": 1 }, "produto": { "id": 1 }, "quantidade": 6 }
```

## Estrutura

```
com.baozistore
├── model        (Cliente, Produto, Pedido)
├── repository   (ClienteRepository, ProdutoRepository, PedidoRepository)
└── controller   (ClienteController, ProdutoController, PedidoController)
```
