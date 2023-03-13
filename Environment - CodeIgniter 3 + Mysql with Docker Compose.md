Para rodar o CodeIgniter 3 e o MySQL usando o Docker Compose, siga os seguintes passos:

1. Crie um arquivo chamado docker-compose.yml no diretório raiz do seu projeto CodeIgniter e adicione o seguinte código:

```yaml
version: '3'

services:
  web:
    image: php:7.2-apache
    ports:
      - "8080:80"
    volumes:
      - ./app:/var/www/html
    depends_on:
      - db

  db:
    image: mysql:5.7
    environment:
      MYSQL_DATABASE: ci_db
      MYSQL_USER: ci_user
      MYSQL_PASSWORD: ci_password
      MYSQL_ROOT_PASSWORD: root_password
    ports:
      - "3306:3306"
    volumes:
      - ./mysql:/var/lib/mysql
```

Este arquivo contém duas definições de serviço - um para o servidor web Apache/PHP e outro para o servidor de banco de dados MySQL.

1. Crie um diretório chamado "app" no diretório raiz do seu projeto CodeIgniter e copie todos os arquivos do seu projeto para esse diretório.

2. Crie um diretório chamado "mysql" no diretório raiz do seu projeto e adicione um arquivo vazio chamado ".gitignore" a ele. Isso garantirá que os dados do banco de dados não sejam incluídos em seu repositório Git.

3. Abra um terminal na pasta raiz do seu projeto e execute o seguinte comando para iniciar os serviços:

```yaml
docker-compose up -d
```


Isso baixará as imagens necessárias e iniciará os serviços em segundo plano.

1. Acesse seu aplicativo CodeIgniter abrindo um navegador e acessando http://localhost:8080/. Você deve ver a página inicial do seu aplicativo.

2. Para acessar o banco de dados, você pode usar as seguintes credenciais:

```yaml
Host: localhost
Port: 3306
Database: ci_db
User: ci_user
Password: ci_passwor
```

Com isso você deve conseguir rodar sua aplicação CodeIgniter 3 juntamente com o MySQL usando o Docker Compose.
