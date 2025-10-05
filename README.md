# Marketplace de Serviços (Mini-Marketplace)

Este projeto é uma implementação de um sistema de marketplace para serviços de profissionais liberais, como diaristas, pintores e eletricistas. A plataforma permite que prestadores de serviço se cadastrem, criem seus serviços com variações, gerenciem sua agenda e sejam contratados por clientes.

## ✨ Tecnologias Utilizadas

Este projeto é um monorepo composto por um backend, um frontend e serviços de infraestrutura orquestrados com Docker.

**Backend (`/backend`)**
* **Framework**: [NestJS](https://nestjs.com/)
* **Linguagem**: TypeScript
* **Banco de Dados**: PostgreSQL
* **ORM**: [Prisma](https://www.prisma.io/)
* **Busca**: [Elasticsearch](https://www.elastic.co/elasticsearch/)
* **Cache**: [Redis](https://redis.io/)
* **Autenticação**: JWT (JSON Web Tokens)

**Frontend (`/frontend`)**
* **Framework**: [SvelteKit](https://kit.svelte.dev/)
* **Linguagem**: TypeScript
* **Estilização**: [Tailwind CSS](https://tailwindcss.com/)
* **Cliente HTTP**: Axios

**Infraestrutura**
* **Containerização**: [Docker](https://www.docker.com/) & [Docker Compose](https://docs.docker.com/compose/)

---

## 🚀 Como Rodar o Projeto (Ambiente Completo)

A maneira mais recomendada e simples de rodar toda a aplicação é usando o Docker Compose.

### Pré-requisitos
* [Docker](https://www.docker.com/get-started/) instalado e em execução.
* [Docker Compose](https://docs.docker.com/compose/install/) (normalmente já vem com o Docker Desktop).

### 1. Variáveis de Ambiente
O `docker-compose.yml` já está pré-configurado com as variáveis de ambiente para os serviços se comunicarem. Não é necessário criar nenhum arquivo `.env` para este modo de execução.

### 2. Subindo os Containers
Na raiz do projeto (onde o arquivo `docker-compose.yml` está localizado), execute o seguinte comando:

```bash
docker-compose up --build
```
* `--build`: Força a reconstrução das imagens do backend e frontend, garantindo que as últimas alterações do seu código sejam aplicadas.
* Você pode adicionar a flag `-d` (`docker-compose up --build -d`) para rodar os containers em segundo plano (detached mode).

Aguarde até que todos os serviços (banco de dados, Redis, Elasticsearch, backend e frontend) sejam iniciados.

### 3. Preparando o Banco de Dados
Com os containers rodando, abra um **novo terminal** e execute os seguintes comandos para preparar e popular o banco de dados:

**a) Aplicar as migrações (criar as tabelas):**
```bash
docker-compose exec backend npx prisma migrate deploy
```

**b) Popular o banco com dados de exemplo (seed):**
```bash
docker-compose exec backend npx prisma db seed
```

### 4. Acessando a Aplicação
Pronto! A aplicação está no ar.
* **Frontend**: [http://localhost:5173](http://localhost:5173)
* **Backend API**: [http://localhost:3000](http://localhost:3000)

---

## 📜 Scripts Disponíveis

### Backend (`/backend`)
* `npm start`: Inicia o servidor em modo de desenvolvimento com hot-reload.
* `npm run build`: Compila o projeto TypeScript para JavaScript na pasta `/dist`.
* `npm run test`: Roda os testes unitários.

### Frontend (`/frontend`)
* `npm run dev`: Inicia o servidor de desenvolvimento com HMR (Hot Module Replacement).
* `npm run build`: Gera a versão de produção do site.
* `npm run lint`: Realiza validação do lint configurado no projeto.
