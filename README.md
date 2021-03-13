# Informações a respeito dos arquivos dockerfile e docker-compose

- No dockerfile tem a instalação do container elixir juntamente com algumas dependências no comando RUN
- No docker-compose está o build do dockerfile que irá instalar o que é necessário para o container na porta 4000 como também tem o banco de dados postgres em sua versão especifica.
- O build irá depender do postgres

# Processos de instalação e configuração de um projeto básico elixir com postgres e dockerfile
# Créditos à [César Willian Alvarenga](https://medium.com/swlh/use-docker-to-create-an-elixir-phoenix-development-environment-e1a81def1d2e)


## Caso possua o docker e o docker-compose instalado em sua máquina, rode os seguintes comandos

```
 docker-compose build
 mkdir src
 alias mix="docker-compose run --rm phoenix mix"
 ```

O primeiro comando irá gerar o build do projeto completo, após isso será criado uma pasta e no final o alias pra poder rodar os comandos docker sem a necessidade de especificar docker-compose run --rm 

## Após gerar os comandos acima, agora gere um projeto phoenix com

```
mix phx.new . --app hello
```

Aproveite e troque o nome do hostname em src/config/dev.exs para db, necessita super usuario para salvar o arquivo

## Os seguintes comandos irá criar e migrar o banco de dados

```
mix ecto.create
mix ecto.migrate
```

## Agora só acesse a pasta e inicialize sua aplicação e finalizando ja poderá ver pronto na porta 4000

```
cd ..
docker-compose up
```
