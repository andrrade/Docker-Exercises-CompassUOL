## 8️⃣ Criando um compose file para rodar uma aplicação com BD 🟡

[🔼 Voltar ao Sumário](https://github.com/andrrade/Docker-Exercises-CompassUOL?tab=readme-ov-file#sum%C3%A1rio-)

Utilize Docker Compose para configurar uma aplicação com um banco de 
dados PostgreSQL, use para isso o projeto [pgadmin](https://github.com/docker/awesome-compose/tree/master/postgresql-pgadmin).

## 💡 Resolução Exercício 8

01. Criar pasta do exercício 8 e entrar nela

```bash
mkdir exe08
```

```bash
cd exe08
```

02. Pegar o link para clonar o repositório

[Link do Repositório Completo](https://github.com/docker/awesome-compose)

![image](https://github.com/user-attachments/assets/85947827-afef-408d-bcf9-2a7d254a0844)

03. Coloque `git clone` antes do link copiado para executar o comando:

```bash
git clone https://github.com/docker/awesome-compose.git
```

>[!NOTE]
> Precisamos apenas do direório `postgresql-pgadmin`, por isso vamos remover todo o resto e deixar apenas o necessário

```bash
cp -r awesome-compose/postgresql-pgadmin ./
```

```bash
rm -rf awesome-compose
```

04. Entrar no diretório `postgresql-pgadmin`

```bash
cd postgresql-pgadmin
```

![image](https://github.com/user-attachments/assets/0c95d552-caa1-4d51-ad3f-e00fcf5587cb)

> [!NOTE]
> Para acessar o arquivo compose.yaml clique no link abaixo:

Arquivo [compose.yaml](https://github.com/andrrade/Docker-Exercises-CompassUOL/blob/main/resolucao-exercicios/02-medio/exe08/compose.yaml)

05. Subir container

```bash
docker compose up --build -d
```

![image](https://github.com/user-attachments/assets/209f82f7-25ff-4443-ac02-1328ecd91bf5)

06. Listar os containers em execução:
```bash
docker-compose ps
```

07. Ver qual é a senha do PostgreSQL
> [!IMPORTANT]
> Essas informações serão utilizadas depois

```bash
cat .env && echo
```

![image](https://github.com/user-attachments/assets/681f9a65-280c-4d0a-93fa-e40959780c6b)

08. Acesse o terminal do PostgreSQL

```bash
docker exec -it postgres psql -U yourUser -d postgres
```

09. Para fins de teste:

a. Crie a Tabela clientes

```sql
CREATE TABLE clientes (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(100),
    email VARCHAR(100)
);
```

b. Insira dados de exemplo

```sql
INSERT INTO clientes (nome, email) VALUES 
('João Silva', 'joao@exemplo.com'),
('Maria Souza', 'maria@exemplo.com');
```

c. Verifique os dados no terminal

```sql
SELECT * FROM clientes;
```

![image](https://github.com/user-attachments/assets/fb6f0dfe-aa83-4022-83cb-0a3466d86ed1)

10. Acesse o pgAdmin no navegador

![image](https://github.com/user-attachments/assets/cc0188ce-0a70-4b40-b049-394f6a4aff23)

11. Coloque os dados que foram obtidos através do comando `cat .env && echo` e clique em `Login`

![image](https://github.com/user-attachments/assets/f39ac988-7526-457a-acd9-c1c744cf2503)

12. Siga o passo a passo para ver no navegador os dados criados através do terminal:

![image](https://github.com/user-attachments/assets/a09ef93f-eae3-494c-84b2-ed5f1df481cd)

![image](https://github.com/user-attachments/assets/d0edd0d8-455c-48ee-9751-3385587d93d9)

![image](https://github.com/user-attachments/assets/0ee2f58e-6243-440d-a1c3-c2ab5053ac38)

https://github.com/user-attachments/assets/1220b6fb-b56d-462a-8eaa-8ce3cecd5aa1

> [!IMPORTANT]
> Com os testes foi possível comprovar que a aplicação com um banco de dados PostgreSQL está funcional

13. Para sair do terminal do PostgreSQL, digite:

```sql
\q
```

![image](https://github.com/user-attachments/assets/ac5f61d5-c47b-4943-9822-3dc81ba9ccd2)
