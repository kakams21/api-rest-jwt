# 🔐 API REST com Autenticação JWT

API REST desenvolvida com **Spring Boot** para autenticação de usuários utilizando **JSON Web Tokens (JWT)**. O projeto implementa cadastro e login com criptografia de senhas, seguindo uma arquitetura em camadas.

---

## 🚀 Tecnologias

- **Java 17**
- **Spring Boot 4** — framework principal
- **Spring Security** — segurança e autenticação
- **Spring Data JPA** — persistência de dados
- **PostgreSQL** — banco de dados relacional
- **JWT (jjwt)** — geração e validação de tokens
- **BCrypt** — criptografia de senhas
- **Maven** — gerenciamento de dependências

---

## ✨ Funcionalidades

- Cadastro de usuários com senha criptografada
- Login com geração de token JWT
- Proteção de rotas via filtro de autenticação
- Validação de tokens em cada requisição
- Interface web simples para testar a API

---

## 📁 Estrutura do projeto

```
src/main/java/com/seuprojeto/api_rest/
├── config/         # Configuração de segurança e filtro JWT
├── controller/     # Endpoints da API
├── dto/            # Objetos de transferência de dados
├── entity/         # Entidades do banco de dados
├── repository/     # Acesso ao banco de dados
├── service/        # Regras de negócio
└── util/           # Utilitário para geração de JWT
```

---

## ⚙️ Como executar

### Pré-requisitos

- Java 17 ou superior
- PostgreSQL instalado e rodando
- Maven (ou use o wrapper `mvnw` incluído)

### Passos

1. Clone o repositório:
   ```bash
   git clone https://github.com/kakams21/api-rest-jwt.git
   cd api-rest-jwt
   ```

2. Crie o banco de dados no PostgreSQL:
   ```sql
   CREATE DATABASE apirest_db;
   ```

3. Crie o arquivo `src/main/resources/application-local.properties` com suas credenciais:
   ```properties
   DB_PASSWORD=sua_senha_do_postgres
   JWT_SECRET=sua_chave_secreta_com_no_minimo_256_bits
   ```

4. Execute a aplicação:
   ```bash
   mvnw spring-boot:run
   ```

5. Acesse a interface no navegador:
   ```
   http://localhost:8081
   ```

---

## 📡 Endpoints

| Método | Rota             | Descrição               | Autenticação |
|--------|------------------|-------------------------|--------------|
| POST   | `/auth/register` | Cadastra um novo usuário | Não          |
| POST   | `/auth/login`    | Faz login e retorna JWT  | Não          |

### Exemplo de requisição — Cadastro

```bash
curl -X POST http://localhost:8081/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"Joao","email":"joao@email.com","password":"123456"}'
```

### Exemplo de resposta

```json
{
  "token": "eyJhbGciOiJIUzI1NiJ9..."
}
```

---

## 🔒 Segurança

- As senhas são criptografadas com **BCrypt** antes de serem salvas
- A autenticação usa **tokens JWT** com expiração de 24 horas
- Credenciais sensíveis ficam em arquivo separado, fora do controle de versão

---

## 📌 Próximas melhorias

- [ ] Adicionar endpoints CRUD protegidos por JWT
- [ ] Documentação com Swagger / OpenAPI
- [ ] Testes automatizados
- [ ] Deploy em nuvem (Railway / Render)

---

## 👤 Autor

**Kauan**

Projeto desenvolvido para fins de estudo e portfólio.
