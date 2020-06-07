## Instalação

### Instalando a API RESTful com Laravel
Para permitir a instalação em qualquer sistema operacional eu utilizei o [Docker](https://www.docker.com/products/docker-desktop).

Apoś instalar o docker, clone o repositório no diretório onde você mantem seus projetos.

Pelo terminal de comando, entre na pasta. E depois entre na pasta da API do laravel que esta com nome de ***users-api*** e suba os containers do docker.
```sh
$ docker-compose up -d
```

Após os containers subirem, execute o comando para atualizar os packages necessários para o funcionamento da API.
```sh
$ docker-compose exec app composer install
```

Execute o seguinte comando para voltar ao diretório anterior e setar as permissões do seu usuário no diretório
```sh
$ cd ..
$ chown -R $USER:$USER users-api
```

Dentro do diretório ***users-api***, Gere o arquivo .env de configuração da API.
```sh
$ cp .env.example .env
```

Execute o comando para gerar a key da API.
```sh
$ docker-compose exec app php artisan key:generate
```

Execute o comando para setar as configurações realizadas.
```sh
$ docker-compose exec app php artisan config:cache
```

Execute o comando para regenerar as classes.
```sh
$ docker-compose exec app composer dump-autoload
```

Execute as migrations no banco de dados.
```sh
$ docker-compose exec app php artisan migrate
```

Execute as seeders no banco de dados.
```sh
$ docker-compose exec app php artisan db:seed
```

Execute o comando para gerar as keys de autenticação do laravel passport.
```sh
$ docker-compose exec app php artisan passport:install
```

Execute o comando para limpar e recarregar as configurações.
```sh
$ docker-compose exec app php artisan optimize:clear
```

> Caso você tenha problema de permissão para executar os comandos acima. Inclua ***sudo*** antes de executar todos os comandos.

Agora a API deve estar disponível no seguinte link: [API REST](http://localhost:8001).

### Instalando o Client

Você vai repetir praticamente a metade dos passos acima.

Pelo terminal de comando, volte a raiz do projeto e entre na pasta ***users-application***. Agora suba os containers do docker.
```sh
$ docker-compose up -d
```

Após os containers subirem, execute o comando para atualizar os packages necessários para o funcionamento da API.
```sh
$ docker-compose exec app2 composer install
```

Execute o seguinte comando para voltar ao diretório anterior e setar as permissões do seu usuário no diretório
```sh
$ cd ..
$ chown -R $USER:$USER users-application
```

Dentro do diretório ***users-api***, Gere o arquivo .env de configuração da API.
```sh
$ cp .env.example .env
```

É muito importante que você entre no arquivo .env, localize a variavel ***USERS_SERVICE_BASE_URL***, e coloque o ip da sua máquina que esta registrado na rede local. Deve ser algo parecido com ***192.168.xx.xxx:8001***, ***Não esqueça de adicionar a porta 8001 no final***.

Execute o comando para gerar a key da API.
```sh
$ docker-compose exec app2 php artisan key:generate
```

Execute o comando para setar as configurações realizadas.
```sh
$ docker-compose exec app2 php artisan config:cache
```

Execute o comando para regenerar as classes.
```sh
$ docker-compose exec app2 composer dump-autoload
```

Execute o comando para limpar e recarregar as configurações.
```sh
$ docker-compose exec app2 php artisan optimize:clear
```

O laravel do client esta instalado. Agora precisamos executar o laravel-mix para carregar os pacotes necessário.

Para executar é preciso instalar o [NodeJs](https://nodejs.org/en/download/).

Apoś instalar o ***Node.js***, novamente pelo terminal de comando, acesse a pasta do projeto. Entre na pasta da aplicação ***users-appication*** e rode o comando para instalar os packages necessário para a aplicação.

```sh
$ npm install
```

Execute o comando para carregar as dependências.
```sh
$ npm run dev
```

Se tudo ocorreu bem a aplicação deve estar disponivel no seguinte URL [clique aqui](http://localhost:8002).

Já tem um usuário cadastrado para teste. 
Email: teste@email.com
Senha: password

###### Qualquer dúvida estou a disposição. 
###### Muito obrigado pela oportunidade.




