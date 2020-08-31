---
title: 'Tutorial do Docker-parte 5: usar montagens de associação'
description: Descreve como usar montagens de associação para controlar o ponto de montagem no host.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6474179a0714f2407ac37e724b997139206a91fb
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89178174"
---
# <a name="use-bind-mounts"></a>Usar montagens de associação

No capítulo anterior, você aprendeu e usou um **volume nomeado** para manter os dados em seu banco de dado. Os volumes nomeados são ótimos se você simplesmente deseja armazenar dados, pois não precisa se preocupar com o *local em que* os dados são armazenados.

Com **montagens de associação**, você controla o mountpoint exato no host. Você pode usar isso para manter dados, mas geralmente é usado para fornecer dados adicionais em contêineres. Ao trabalhar em um aplicativo, você pode usar uma montagem de associação para montar o código-fonte no contêiner para permitir que ele veja alterações de código, responder e permitir que você veja as alterações imediatamente.

Para aplicativos baseados em nó, [nodemon](https://npmjs.com/package/nodemon) é uma excelente ferramenta para observar alterações de arquivo e reiniciar o aplicativo. Há ferramentas equivalentes na maioria das outras linguagens e estruturas.

## <a name="quick-volume-type-comparisons"></a>Comparações de tipo de volume rápido

As montagens de ligação e os volumes nomeados são os dois tipos principais de volumes que acompanham o mecanismo do Docker. No entanto, drivers de volume adicionais estão disponíveis para dar suporte a outros casos de uso ([SFTP](https://github.com/vieux/docker-volume-sshfs), [ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume)e mais).

| Propriedade | Volumes nomeados | Montagens por associação |
| -------- | ------------- | ----------- |
| Local do host | O Docker escolhe | Você controla |
| Exemplo de montagem (usando `-v` ) | meu-volume:/usr/local/dados | /path/to/data:/usr/local/data |
| Popula o novo volume com o conteúdo do contêiner | Sim | Não |
| Dá suporte a drivers de volume | Sim | Não |

## <a name="start-a-dev-mode-container"></a>Iniciar um contêiner de modo de desenvolvimento

Para executar o contêiner para dar suporte a um fluxo de trabalho de desenvolvimento, você fará o seguinte:

- Monte seu código-fonte no contêiner
- Instalar todas as dependências, incluindo as dependências de "desenvolvimento"
- Iniciar nodemon para observar as alterações do sistema de arquivos

1. Verifique se você não tem nenhum `getting-started` contêiner anterior em execução.

1. Execute o comando a seguir (substitua os ` \ ` caracteres por `` ` `` no Windows PowerShell). Você aprenderá o que está acontecendo posteriormente:

    ```bash
    docker run -dp 3000:3000 \
        -w /app -v ${PWD}:/app \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` -o mesmo que antes. Executar no modo desanexado (segundo plano) e criar um mapeamento de porta
    - `-w /app` -define o "diretório de trabalho" ou o diretório atual do qual o comando será executado
    - `-v ${PWD}:/app` -associar a montagem do diretório atual do host no contêiner no `/app` diretório
    - `node:12-alpine` -a imagem a ser usada. Observe que essa é a imagem base para seu aplicativo do Dockerfile
    - `sh -c "yarn install && yarn run dev"` -o comando. Estamos iniciando um shell usando `sh` (o Alpine Ski não tem `bash` ) e executamos `yarn install` para instalar *todas as* dependências e, em seguida, executar `yarn run dev` . Se você olhar no, veremos `package.json` que o `dev` script está sendo iniciado `nodemon` .

1. Você pode assistir aos logs usando `docker logs -f <container-id>` . Você saberá que está pronto para começar quando vir:

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    Quando você terminar de assistir aos logs, saia ao pressionar `Ctrl` + `C` .

1. Agora, faça uma alteração no aplicativo. No `src/static/js/app.js` arquivo, altere o botão **Adicionar item** para simplesmente dizer **Adicionar**. Essa alteração estará na linha 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Basta atualizar a página (ou abri-la) e você verá a alteração refletida no navegador quase imediatamente. Pode levar alguns segundos para o servidor de nó reiniciar, portanto, se você receber um erro, basta tentar atualizar após alguns segundos.

    ![Captura de tela do rótulo atualizado para o botão Adicionar](media/updated-add-button.png)

1. Fique à vontade para fazer outras alterações que você gostaria de fazer. Quando terminar, pare o contêiner e crie a nova imagem usando `docker build -t getting-started .` .

O uso de montagens de associação é *muito* comum para configurações de desenvolvimento local. A vantagem é que a máquina de desenvolvimento não precisa ter todas as ferramentas e ambientes de compilação instalados. Com um único `docker run` comando, o ambiente de desenvolvimento é puxado e pronto para uso. Você aprenderá sobre Docker Compose em uma etapa futura, pois isso ajudará a simplificar seus comandos (você já está recebendo muitos sinalizadores).

## <a name="recap"></a>Recapitulação

Neste ponto, você pode persistir seu banco de dados e responder rapidamente às necessidades e demandas de seus investidores e fundadores. Alegria! Mas adivinhe? Você recebeu ótima notícia!

**Seu projeto foi selecionado para desenvolvimento futuro!**

Para se preparar para a produção, você precisa migrar seu banco de dados do trabalho no SQLite para algo que possa ser dimensionado um pouco melhor. Para simplificar, você continuará com um banco de dados relacional e alternará seu aplicativo para usar o MySQL. Mas como você deve executar o MySQL? Como permitir que os contêineres se comuniquem entre si? Você aprenderá sobre isso em seguida!

## <a name="next-steps"></a>Próximas etapas

Continue com o tutorial!

> [!div class="nextstepaction"]
> [Aplicativos com vários contêineres](multi-container-apps.md)