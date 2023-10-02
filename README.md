
# Sistema de Requisição

Projeto desenvolvido por Guimel Filipe como teste de seleção .

Está sendo utilizada a versão 18.16 do Node.js.

## Índice

- [Modelo Entidade-Relacionamento](#modelo-entidade-relacionamento)
- [Como rodar](#como-rodar)
- [Tecnologias e frameworks utilizados](#tecnologias-e-frameworks-utilizados)
    - [Back-End](#back-end)
    - [Front-End](#front-end)

## Modelo Entidade-Relacionamento

Você pode conferir o Modelo Entidade-Relacionamento de 2 formas:

- [Por este link, para acessar a imagem](https://drive.google.com/file/d/18W20oareTPbzAXGiwcM_gQ6nsKJvGIor/view?usp=sharing), ou
- Acessando a pasta `/api/prisma/dbml`, copie o conteúdo do arquivo `schema.dbml` e cole no site [dbdiagram.io](https://dbdiagram.io/d).

## Como rodar

1. Vá até a pasta `/api`;
1. Em um terminal, execute `yarn install` para instalar as dependências;
1. Crie um arquivo `.env` e preencha assim:
    ```dotenv
    DATABASE_URL="postgresql://johndoe:randompassword@localhost:5432/mydb?schema=public"
    DATABASE_USER="johndoe"
    DATABASE_PASSWORD="randompassword"

    DATABASE_TEST_URL="postgresql://johndoetest:randompasswordtest@localhost:5433/test?schema=public"
    DATABASE_TEST_USER="johndoetest"
    DATABASE_TEST_PASSWORD="randompasswordtest"
    ```
1. Execute `docker compose up -d --build` para dar build no banco de dados;
1. Execute `docker compose up` para iniciar o banco de dados. O passo anterior não precisa ser repetido das próximas vezes;
1. Em outro terminal, execute `yarn migration` para aplicar as migrations no banco de dados;
1. Execute `yarn setup:db` para adicionar os seguintes dados:
    - 2 setores: Gerência de Sistemas, Secretaria de Graduação
    - 5 serviços:
        - Gerência de Sistemas: Reportar Problema, Reserva de Laboratório, Reserva de Auditório
        - Secretaria de Graduação: Solicitação de Histórico, Solicitação de Matrícula
    - 3 usuários: 1 aluno, 1 servidor da Secretaria de Graduação, 1 servidor da Gerência de Sistemas
1. Execute `yarn dev` e acesse [http://localhost:3333](http://localhost:3333) ou o local indicado no terminal;
1. O Back-End está rodando!
    - Para realizar os testes, abra outro terminal e execute `yarn test`.
    - Para ver a documentação da API, acesse [http://localhost:3333/docs](http://localhost:3333/docs).
1. Agora, para rodar o Front-End, em outro terminal, vá até a pasta `/web`;
1. Execute `yarn install` para instalar as dependências;
1. Execute `yarn dev` e acesse [http://localhost:3000](http://localhost:3000) ou o local indicado no terminal;
1. O Front-End está rodando!

## Tecnologias e frameworks utilizados

- TypeScript
### Back-End

- API: Node.js, com framework Fastify
- Validação de Dados: Zod
- Banco de Dados: Prisma (ORM), Docker, PostgreSQL
- Testes: Jest, Supertest

### Front-End

- Next.js versão 13
- React
- TailwindCSS
- Componentes: ShadcnUI
- Formulário: React Hook Form

