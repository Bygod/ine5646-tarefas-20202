# UFSC - CTC - INE - INE5646 Programação para Web :: Exercício App Fim do Mundo

A aplicação mostra dados sobre asteróides que passarão pela Terra em uma determinada data (informada pelo usuário). Os dados são obtidos diretamente da Nasa.

## Objetivo do Exercício

Mostrar uma aplicação do tipo SPA (*Single Page Application*) que utiliza a bilioteca [React](https://reactjs.org/) e o framework CSS [Bulma](https://bulma.io/) para o desenvolvimento do lado cliente. A aplicação também utiliza o agregador [webpack](https://webpack.js.org/) para gerar o arquivo JavaScript que é executado pelo browser.

A aplicação também tem o objetivo de mostrar como acessar e consumir dados de um webservice.

## Bug do exercício

Quando o usuário digita uma data inválida a aplicação ignora o que foi digitado e utiliza uma outra data fixa previamente definida. O comportamento esperado é somente autorizar a pesquisa por informações quando a data digitada for válida.

## Configuração no seu computador

O progrma Docker Desktop precisa estar instalado e em execução na sua máquina. Acesse [https://www.docker.com/get-started](https://www.docker.com/get-started) para saber como fazer isso.

Se o VSCode for utilizado então é preciso instalar a extensão [Remote Development da Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack).

## Instruções

### Durante o desenvolvimento com VSCode

#### Preparação Inicial

Os procedimentos a seguir devem ser realizados uma única vez.

##### Configurando arquivo .env

Crie, no diretório raiz do projeto ***no seu computador local***, o arquivo **.env** com o seguinte conteúdo

```bash
NASA_API_KEY=8a99xddx....
LOCAL=sim
```

O valor do atributo *NASA_API_KEY* é obtido no endereço `https://api.nasa.gov/index.html#apply-for-an-api-key` Isso permitirá que sua aplicação acesse o webservice da Nasa.

A variável LOCAL, quando presente e com o valor *sim*  indica que a aplicação será executada localmente. Se ausente ou com outro valor indica que a aplicação será executada no Heroku.

O arquivo **.env** também é usado para armazenar dados sigilosos como senhas, chaves, etc. Essas informações nunca devem ser armazenadas em locais públicos (como repositórios git ou repositórios de imagens docker).

##### Instalando bibliotecas JavaScript

Abra um terminal e instale as bibliotecas JavaScript usadas pelo lado cliente da aplicação:

```bash
cd cliente
npm install
```

Abra um terminal e instale as bibliotecas JavaScript usadas pelo lado servidor da aplicação:

```bash
cd servidor
npm install
```

#### Durante o desenvolvimento

Para colocar a aplicação no ar durante o seu desenvolvimento proceda da seguinte forma.

Abra um terminal e inicie a execução do lado cliente (os arquivos serão monitorados pelo webpack):

```bash
cd cliente
npm start
```

Abra um segundo terminal e inicie a execução do lado servidor (os arquivos serão monitorados pelo babel):

```bash
cd servidor
npm start
```

A partir de agora altere os arquivos JavaScript como desejar.

### Em produção

Depois que a aplicação está pronta é preciso gerar "uma versão executável". Para isso é preciso gerar uma imagem e depois instanciar e executar um container a partir da imagem gerada.

#### Gerando a imagem

A imagem, aqui chamada de ***ine5646-app_fim_do_mundo:*** conterá a versão executável da aplicação. Execute o seguinte comando para gerar a imagem (note que o comando termina com um ponto depois de ine5646-app_fim_do_mundo):

```bash
docker build -t ine5646-app_fim_do_mundo .
```

#### Executando a aplicação localmente

Crie ou utilize um arquivo chamado ***.env*** com o mesmo conteúdo indicado acima.```

Crie um container para executar a aplicação. Execute o seguinte comando para instanciar o container e colocá-lo no ar.

```bash
docker run -d --name ine5646-app_fim_do_mundo -p 4000:3000 --env-file .env ine5646-app_fim_do_mundo
```

Para acessar a aplicação basta digitar `https://localhost:4000` no seu navegador.

Naturalmente, pode-se utilizar outras portas (por exemplo, -p 4500:3000) e o arquivo **.env** pode estar localizado em qualquer diretório. Neste caso, a aplicação seria acessada via `https://localhost:4500`.
