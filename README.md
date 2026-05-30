# Trabalho Final — Etapa 1

Trabalho para aula de Desenvolvimento Web3.

## Pré-requisitos

- Java 17+
- Maven 3.8+
- MySQL 8+
- Postman

## Configuração do banco de dados

Primeiro execute o script abaixo no MySQL:

```sql
CREATE DATABASE ms_user;
CREATE DATABASE ms_email;
```

## Como executar

Abra dois terminais e rode cada serviço separadamente:

```bash
# Terminal 1 — User Service (porta 8081)
cd user-service
mvn spring-boot:run

# Terminal 2 — Email Service (porta 8082)
cd email-service
mvn spring-boot:run
```

## Endpoints — User Service

| Método | Endpoint | Acesso | Descrição |
|--------|----------|--------|-----------|
| POST | `/users` | Público | Cria usuário |
| POST | `/users/login` | Público | Autentica/retorna token JWT |
| GET | `/users/test/customer` | ROLE_CUSTOMER | Endpoint protegido |
| GET | `/users/test/admin` | ROLE_ADMIN | Endpoint protegido |

### Criar usuário

```json
POST /users
{
  "email": "usuario@email.com",
  "password": "senha",
  "role": "ROLE_CUSTOMER"
}
```

### Login

```json
POST /users/login
{
  "email": "usuario@email.com",
  "password": "senha"
}
```

Resposta:
```json
{
  "token": "eyJhbGciOiJIUzI1NiJ9..."
}
```

### Usar token nos endpoints protegidos

```
Authorization: Bearer <token>
```
