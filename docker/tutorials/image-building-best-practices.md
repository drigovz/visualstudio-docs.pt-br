---
title: 'Tutorial do Docker-parte 8: camadas de imagem'
description: Como examinar e gerenciar camadas de imagem em imagens do Docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8913c558c2860599fbfaaba03fa466d11931a528
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837951"
---
# <a name="image-layering"></a>Camadas de imagem

Você sabia que pode examinar o que compõe uma imagem? Usando o `docker image history` comando, você pode ver o comando que foi usado para criar cada camada em uma imagem.

1. Use o `docker image history` comando para ver as camadas na `getting-started` imagem que você criou anteriormente no tutorial.

    ```bash
    docker image history getting-started
    ```

    Você deve obter uma saída semelhante a esta (datas/IDs podem ser diferentes).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Cada uma das linhas representa uma camada na imagem. A exibição aqui mostra a base na parte inferior com a camada mais nova na parte superior. Usando isso, você também pode ver rapidamente o tamanho de cada camada, ajudando a diagnosticar imagens grandes.

1. Você observará que várias das linhas estão truncadas. Se você adicionar o `--no-trunc` sinalizador, obterá a saída completa (Sim, usará um sinalizador truncado para obter uma saída não truncada).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Cache de camada

Agora que você viu a disposição em camadas em ação, há uma lição importante para aprender a reduzir os tempos de compilação para suas imagens de contêiner.

> Quando uma camada é alterada, todas as camadas de downstream também devem ser recriadas

Vamos examinar o Dockerfile que você estava usando mais uma vez...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Voltando para a saída do histórico de imagens, você verá que cada comando no Dockerfile se torna uma nova camada na imagem. Você pode se lembrar de que, quando fez uma alteração na imagem, as dependências de yarn tinham que ser reinstaladas. Há uma maneira de corrigir isso? Não faz muito sentido enviar as mesmas dependências toda vez que você cria, certo?

Para corrigir isso, você pode reestruturar seu Dockerfile para ajudar a dar suporte ao cache das dependências. Para aplicativos baseados em nó, essas dependências são definidas no `package.json` arquivo. Então, e se você tiver copiado apenas esse arquivo primeiro, instalar as dependências e *, em seguida* , copiar em todo o resto? Em seguida, você recriará as dependências yarn se houvesse uma alteração no `package.json` . Faz sentido?

1. Atualize o Dockerfile para copiar no `package.json` primeiro, instale as dependências e, em seguida, copie tudo o mais no.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Crie uma nova imagem usando `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Você deve ver uma saída como esta...

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Você verá que todas as camadas foram recriadas. Perfeitamente bem, uma vez que você alterou o Dockerfile um pouco.

1. Agora, faça uma alteração no `src/static/index.html` arquivo (como alterar o `<title>` para dizer "o aplicativo de todo incrível").

1. Crie a imagem do Docker agora usando `docker build` novamente. Desta vez, sua saída deve parecer um pouco diferente.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    Primeiro, você deve observar que a compilação foi muito mais rápida! E você verá que todas as etapas de 1-4 têm `Using cache` . Então, alegria! Você está usando o cache de compilação. Enviar e extrair essa imagem e atualizar para ela também será muito mais rápido. Alegria!

## <a name="multi-stage-builds"></a>Compilações de vários estágios

Embora não vamos nos aprofundar muito neste tutorial, as compilações de vários estágios são uma ferramenta incrivelmente poderosa para ajudar a usar vários estágios para criar uma imagem. Há várias vantagens para eles:

- Dependências de tempo de compilação separadas das dependências de tempo de execução
- Reduzir o tamanho geral da imagem enviando *apenas* o que seu aplicativo precisa executar

### <a name="maventomcat-example"></a>Exemplo do Maven/Tomcat

Durante a criação de aplicativos baseados em Java, um JDK é necessário para compilar o código-fonte para códigos de bytes Java. No entanto, esse JDK não é necessário na produção. Além disso, você pode estar usando ferramentas como Maven ou gradle para ajudar a criar o aplicativo.
Eles também não são necessários na imagem final. Ajuda de builds de vários estágios.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

Este exemplo usa um estágio (chamado `build` ) para executar a compilação Java real usando o Maven. O segundo estágio (a partir de `FROM tomcat` ) copia em arquivos do `build` estágio. A imagem final é apenas o último estágio que está sendo criado (o que pode ser substituído usando o `--target` sinalizador).

### <a name="react-example"></a>Exemplo de reagir

Ao criar aplicativos reagir, você precisa de um ambiente de nó para compilar o código JS (normalmente JSX), as folhas de estilo do SASS e muito mais em HTML, JS e CSS estáticos. Se você não estiver fazendo renderização no lado do servidor, nem precisará de um ambiente de nó para a compilação de produção. Por que não enviar os recursos estáticos em um contêiner Nginx estático?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

Aqui, você está usando uma `node:12` imagem para executar a compilação (maximizando o cache de camada) e, em seguida, copiando a saída em um contêiner nginx. Legal, não?

## <a name="recap"></a>Recapitulação

Ao entender um pouco sobre como as imagens são estruturadas, você pode criar imagens com mais rapidez e enviar menos alterações. Compilações de vários estágios também ajudam a reduzir o tamanho geral da imagem e a aumentar a segurança do contêiner separando as dependências de tempo de compilação de dependências de tempo de execução

## <a name="next-steps"></a>Próximas etapas

Continue com o tutorial!

> [!div class="nextstepaction"]
> [Implantando na nuvem](deploy-to-cloud.md)