# STOCKR — Sistema de Gestão de Produtos

![Preview do sistema](https://github.com/MarceloHabreu/microservices-docker/blob/main/FrontendImage.png)

> CRUD completo de produtos com API REST em Spring Boot, banco de dados PostgreSQL e frontend em HTML/CSS/JS — tudo containerizado com Docker Compose.

---

## Tecnologias

| Camada | Tecnologia |
|--------|-----------|
| Frontend | HTML, CSS, JavaScript (Vanilla) |
| Backend | Java 21, Spring Boot 4, Spring Data JPA |
| Banco de dados | PostgreSQL 16 |
| ORM | Hibernate 7 |
| Containerização | Docker, Docker Compose |

---

## Arquitetura

```
microservices-docker/
├── web/                  # Frontend (Nginx)
│   └── index.html
├── api/                  # Backend Spring Boot
│   └── api/
│       └── src/
│           └── main/
│               ├── java/com/example/api/
│               │   ├── model/Product.java
│               │   └── controller/ProductController.java
│               └── resources/
│                   └── application.yml
└── docker-compose.yml
```

---

## Funcionalidades

- **Listar** todos os produtos em tempo real
- **Cadastrar** novo produto via formulário lateral
- **Editar** produto existente com preenchimento automático do formulário
- **Deletar** produto com confirmação
- **Filtrar** produtos por nome ou descrição
- Indicador de status da API em tempo real
- Badge de estoque (verde/vermelho conforme quantidade)

---

## Endpoints da API

| Método | Rota | Descrição |
|--------|------|-----------|
| `GET` | `/products` | Lista todos os produtos |
| `GET` | `/products/{id}` | Busca produto por ID |
| `POST` | `/products` | Cria novo produto |
| `PUT` | `/products/{id}` | Atualiza produto existente |
| `DELETE` | `/products/{id}` | Remove produto |

### Exemplo de payload

```json
{
  "name": "Notebook Dell XPS",
  "description": "Notebook de alto desempenho",
  "price": 7899.90,
  "stock": 15
}
```

---

## Como executar

### Pré-requisitos

- [Docker](https://www.docker.com/) instalado
- [Docker Compose](https://docs.docker.com/compose/) instalado

### Subindo o projeto

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/microservices-docker.git
cd microservices-docker

# Suba todos os containers
docker compose up -d --build
```

### Acessando

| Serviço | URL |
|---------|-----|
| Frontend | http://localhost:80 |
| API | http://localhost:8081/products |
| Banco (externo) | localhost:5433 |

### Parando o projeto

```bash
# Para os containers (dados preservados)
docker compose down

# Para os containers e remove os dados
docker compose down -v
```

---

## Configuração do banco

As credenciais e configurações estão no `application.yml`:

```yaml
spring:
  datasource:
    url: jdbc:postgresql://db:5432/appdb
    username: admin
    password: admin
  jpa:
    hibernate:
      ddl-auto: update
```

> A tabela `tb_products` é criada automaticamente pelo Hibernate ao subir a aplicação.

---

## Conectando com DBeaver / pgAdmin

| Campo | Valor |
|-------|-------|
| Host | `localhost` |
| Porta | `5433` |
| Banco | `appdb` |
| Usuário | `admin` |
| Senha | `admin` |

---

## Autor

Desenvolvido por **Marcelo Habreu**  
TDE Pratica DevOps  — 5º período
Professor: Marcos Gomes da Silva Rocha
