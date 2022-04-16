# Projeto Docker To-Do List - Trybe.

---

# Habilidades
Neste projeto, você será capaz de:
  * Usar comandos dockers no CLI - Interface de linha de comando;
  * Criar um contêiner Docker para uma aplicação de front-end;
  * Criar um contêiner Docker para uma aplicação de back-end;
  * Criar um contêiner Docker para uma aplicação de testes;
  * Orquestrar os três contêineres utilizando o Docker compose.

---

# Entregáveis


Temos, neste projeto, uma série de comandos com diferentes níveis de complexidade que devem ser resolvidos cada um em seu arquivo próprio.

1. Leia o requisito e crie um arquivo chamado `commandN.dc` no diretório `docker-commands`, em que N é o número do desafio.

2. O arquivo deve conter apenas o comando do CLI *(Interface de Linha de Comando)* do Docker do requisito resolvido. Um exemplo de como vai ficar seu arquivo:
```dc
docker network inspect bridge
```

3. Faça isso até finalizar todos os requisitos e depois siga as instruções de como entregar o projeto em [**Instruções para entregar seu projeto**](#instruções-para-entregar-seu-projeto).

4. Os arquivos principais do projeto estão na pasta `docker`, na raiz do projeto, nele estão contidos:
- Pasta `docker-commands`: Onde ficarão os comandos exigidos pelos requisitos; 
  - **⚠️ Importante: você deve assumir que essa é a pasta raiz para os comandos.**
  - Por exemplo, se você precisa referenciar um caminho em um comando, você deve assumir que sua pasta raiz esta partindo de `./docker`
- Pasta `todo-app`: Onde fica nossa **pseudo-aplicação**, que servirá como base para nossos `Dockerfile`s e `Compose`;
  - **⚠️ Essa aplicação conta com um [**README.md**](./docker/todo-app/README.md) próprio, que deve ser usado como referência na criação dos scripts!**
- A pasta `docker` deve receber o arquivo `docker-compose.yml` para orquestração de aplicações

5. Para entregar o seu projeto você deverá criar um _Pull Request_ neste repositório. Este _Pull Request_ deverá conter no diretório `docker-commands` os arquivos `command01.dc`, `command02.dc` e assim por diante até o `command12.dc`, que conterão seu comando `docker` de cada requisito, respectivamente.

**⚠️ É importante que seus arquivos tenham exatamente estes nomes! ⚠️**

### Sobre o avaliador

O avaliador cria um **container especial** para executar a avaliação de `comandos`, `Dockerfiles` e `docker-compose`. 

Esse container é temporário, por tanto, ao começar ou terminar os testes locais, o avaliador remove automaticamente esse mesmo container, assim como seu volume associado.

O volume desse container, mapeia a pasta `./docker/` do seu projeto, para dentro dele, ou seja, a raiz desse container vai conter as pastas `./docker-commands/`, `./todo-app/` e seu arquivo `./docker-compose.yml`, quando estiver pronto.

Isso significa, que se pudessemos olhar para dentro do container de avaliação, veriamos a seguinte estrutura:

```bash
.
├── docker-commands
└── todo-app
    ├── back-end
    │   └── *
    ├── front-end
    │   └── *
    └── tests
        └── *
```

Por tanto, é importante entender que os comandos docker escritos em `command*.dc` estarão rodando dentro desse container especial (e não a partir da raiz do projeto, como em projetos anteriores).

---


## O que deverá ser desenvolvido

Você irá "conteinerizar" as aplicações de frontend, backend e testes, criar uma conexão entre elas e orquestrar seu funcionamento.

## Desenvolvimento

Crie imagens das aplicações e os configure com o docker-compose.

## Data de Entrega

  - Projeto individual.

  - Serão dois dias de projeto.
  
  - Data de entrega para avaliação final do projeto: `DD/MM/YYYY - 14:00h`.

---

# Instruções para entregar seu projeto

## Não se esqueça de consultar as documentações!

⚠️ **Importante**:

Esse projeto tem como intuito te treinar para ter mais familiaridade com a documentação de aplicações, por tanto, poderão haver alguns comandos ou atributos que não estão no course, mas que devem ser descritos no decorrer dos requisitos.

Nesses casos, é importante se atentar a aquilo que o requisito pede, e lembrar sempre de utilizar a [documentação oficial](https://docs-docker-com.translate.goog/engine/reference/commandline/cli/?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt-BR&_x_tr_pto=nui) do Docker para pesquisar detalhes sobre comandos.

Ao criar um Dockerfile para o nosso **pseudo-aplicativo**, seu `README` (`./docker/tests/README.md`) deve servir como "tradutor" para os passos de execução. Lembre-se de que o `Dockerfile` é como uma receita para execução dessas aplicações.

Aqui, também é importante a utilização do comando `--help` no CLI (`docker <comando> <subcomando> --help`), dado que para cada comando do docker, é possível aplicar subcomandos ou parâmetros, exemplo: `docker network --help`

---

# Como desenvolver

**⚠️ Importante ⚠️**
Para que o avaliador funcione corretamente, é importante que a instalação do Docker (vista no dia 1) seja feita corretamente.
Aqui também é importante que o seu usuário esteja no grupo `docker` (para que não haja a necessidade de rodar comandos utilizando o `sudo`)

Nesse projeto, temos uma aplicação completa *(Um aplicativo de tarefas)* que precisa ser conteinerizada para funcionar, aqui, você desenvolver os respectivos arquivos de configuração para cada frente específica: `Front-end`, `Back-end` e no nosso caso um aplicativo de teste que deve validar se as aplicações estão se comunicando.

---

## Execução de testes unitários

⚠ **É necessário ter o Docker instalado corretamente na sua máquina para rodar os testes locais**

Todos os requisitos do projeto serão testados automaticamente por meio do Jest. Basta executar o comando abaixo:

```bash
npm test
```

Você pode rodar um arquivo de `test` por vez, exemplo:

```bash
npm test 01container
```
⚠ **Atenção:** ⚠
Não  utilize a função `.only` ou `.skip` após o describe. Os testes precisam rodar por completo para que seja avaliado localmente.

---

# Requisitos do projeto


## Comandos docker

#### 1. Crie um novo container de modo interativo sem roda-lo nomeando-o como `01container` e utilizando a imagem `alpine` usando a versão `3.12`

  - **Observações técnicas:** 
    - O container **não deve ser inicializado**, somente criado;
    - O container deve estar preparado para acesso interativo;

  - **Dica:** 
    - Lembre-se aqui, que um parâmetro não é necessariamente aplicável a apenas um comando.

  - **O que será testado:** 
    - O container vai ter o `name`: `01container`;
    - O container vai estar uzando a imagem `alpine` na versão `3.12`.

#### 2. Inicie o container `01container`

  - **Observações técnicas:** 
    - O container que está parado, deve ser iniciado;
    - Se o container tiver sido iniciado de modo interativo, ele deve se manter ativo ao inicia-lo.

  - **O que será testado:** 
    - O avaliador verificará se o container está parado;
    - O avaliador rodará o comando;
    - O avaliador verificará se o container está rodando.

#### 3. Liste os containers filtrando pelo nome `01container`

  - **Dica:** 
    - Praticamente todo comando de listagem no Docker possui uma forma de filtragem.

  - **O que será testado:** 
    - Que o comando retornará uma lista com os dados corretos.

#### 4. Execute o comando `cat /etc/os-release` no container `01container` sem se acoplar a ele

  - **Observações técnicas:**
    - O container deve estar rodando, e você deve ser capaz de **executar um comando** nesse container.
  
  - **Dica:** 
    -  É possível fazer isso sem usar o comando `attach`.

  - **O que será testado:** 
    - Que o comando retornará os dados corretos da `distro` no container.

#### 5. Remova o container `01container` que está em andamento.

  - **O que será testado:** 
    - O avaliador rodará o comando 5;
    - O avaliador validará o processo com o comando 3.

#### 6. Faça o download da imagem `nginx` com a versão `1.21.3-alpine` sem criar ou rodar um container.

  - **O que será testado:** 
    - Que a imagem correta foi baixada;
    - Que nenhum container foi iniciado para isso.

#### 7. Rode um novo container com a imagem  `nginx` com a versão `1.21.3-alpine` em segundo plano nomeando-o como `02images` e mapeando sua porta padrão de acesso para porta `3000` do sistema hospedeiro.

  - **O que será testado:** 
    - Que o container foi iniciado corretamente;
    - Que é possível ter acesso ao container pelo endereço `localhost:3000`;
    - Que a página retorna o valor esperado.

#### 8. Pare o container `02images` que está em andamento.

  - **O que será testado:** 
    - Que não há nenhum container ativo após seu comando.

## Dockerfile

**⚠️ As aplicações a seguir contam com um [**README.md**](./docker/todo-app/README.md) próprio, que deve ser usado como referência na criação dos scripts!**

#### 9. Gere uma build a partir do Dockerfile do `back-end` do `todo-app` nomeando a imagem para `todobackend`.

  **Dica:** O comando `ADD` do Dockerfile, também pode ser utilizado para descompactar arquivos dentro do container.

   - **O que será testado:** 
    - Se existe um arquivo `Dockerfile` em `./docker/todo-app/back-end/`:
      - O Dockerfile deve rodar uma imagem `node` utilizando a versão `14` ou mais;
        - Recomenda-se o uso da variante `-alpine`, pois ela é otimizada para desempenho;
        - Lembre-se de consultar o README do `todo-app` para validar os requisitos da aplicação.  
      - Deve estar com a porta `3001` exposta;
      - Deve adicionar o arquivo `node_modules.tar.gz` a imagem;
      - Deve copiar todos os arquivos da pasta `back-end` para a imagem;
      - Ao iniciar a imagem deve rodar o comando `npm start`.
    - Se ao *buildar* o Dockerfile o nome da imagem gerada é igual a `todobackend`.

#### 10. Gere uma build a partir do Dockerfile do `front-end` do `todo-app` nomeando a imagem para `todofrontend`.

  **Dica:** O comando `ADD` do Dockerfile, também pode ser utilizado para descompactar arquivos dentro do container.
 
  - **O que será testado:** 
    - Se existe um arquivo `Dockerfile` em `./docker/todo-app/front-end/`:
      - O `Dockerfile` pode rodar uma imagem `node` utilizando a versão `14` ou mais;
        - Recomenda-se o uso da variante `-alpine`, pois ela é otimizada para desempenho;
        - Lembre-se de consultar o README do `todo-app` para validar os requisitos da aplicação. 
      - Deve estar com a porta `3000` exposta;
      - Deve adicionar o arquivo `node_modules.tar.gz` a imagem, de maneira que ele seja extraído dentro do `container`;
      - Deve copiar todos os arquivos da pasta `front-end` para a imagem;
      - Ao iniciar a imagem deve rodar o comando `npm start`;
    - Se ao *buildar* o `Dockerfile` o nome da imagem gerada é igual a `todofrontend`.

#### 11.Gere uma build a partir do Dockerfile dos `testes` do `todo-app` nomeando a imagem para `todotests`.

  **Dica:** O comando `ADD` do Dockerfile, também pode ser utilizado para descompactar arquivos dentro do container.
  
  **Observação**: A aplicação `todotests` só funciona corretamente se estiver dockerizada e dentro de uma rede docker configurada corretamente.

  - **O que será testado:** 
      - Se existe um arquivo `Dockerfile` em `./docker/todo-app/tests/`:
        - O Dockerfile deve rodar a imagem `mjgargani/puppeteer:trybe1.0` para que os testes funcionem;
        - Deve adicionar o arquivo `node_modules.tar.gz` a imagem;
        - Deve copiar todos os arquivos da pasta `tests` para a imagem;
        - Ao iniciar a imagem deve rodar o comando `npm test`;
      - Se ao *buildar* o Dockerfile o nome da imagem gerada é igual a `todotests`.

## Bônus

### Docker-compose

#### 12. Suba uma orquestração em segundo plano com o docker-compose de forma que `backend`, `frontend` e `tests` consigam se comunicar.

  **Dica:** use as imagens já **"buildadas"** que foram executadas nos requisitos 9,10 e 11 para a criação do compose.

  - **O que será testado:** 
      - Se existe um arquivo `docker-compose.yml` na pasta `./docker/`:
        - O docker-compose deve rodar na versão 3.

      - **tests**
        - O container de `todotests` deve ter como dependencia os containers `frontend` e `backend`;
        - O nome do _service_ deverá ser `todotests`;
        - Deve ter uma variável de ambiente `FRONT_HOST` que recebe como valor o nome do container do `frontend`
          - Lembrando que, dentro de uma rede docker, o host de um container é indentificado pelo seu nome.

      - **front-end**
        - O container de `todofrontend` deve rodar na porta `3000`;
        - O nome do _service_ deverá ser `todofront`;
        - Deve ter como dependencia o container `backend`;
        - Deve ter uma variável de ambiente `REACT_APP_API_HOST` que recebe como valor o nome do container do `backend`.
          - Lembrando que, dentro de uma rede docker, o host de um container é indentificado pelo seu nome.

      - **back-end**
        - O container de `todobackend` deve rodar na porta `3001`;
        - O nome do _service_ deverá ser `todoback`;

  - **Dica:**
    - Consulte a documentação em `./docker/todo-app/README.md`;
    - É possível adicionar e extrair arquivos `.tar.gz` no `Dockerfile` com apenas um comando.

---
