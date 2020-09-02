---
title: 'Tutorial do Docker-parte 9: implantar na nuvem'
description: Implante um aplicativo Docker em um serviço de nuvem para hospedagem.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 661f9f6833b5ac5d42aacde7f228b042bef00bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89178187"
---
# <a name="deploy-to-the-cloud"></a>Implantar na nuvem

Agora que você executou seu aplicativo localmente, pode começar a pensar em executá-lo na nuvem para que outras pessoas possam acessá-lo e usá-lo. Para fazer isso, você usará contextos de Docker. Um contexto é o local em que você está trabalhando atualmente com contêineres. No momento, você só tem o contexto "padrão", portanto, será necessário adicionar uma nuvem e implantar seu aplicativo nele.

## <a name="create-your-cloud-context"></a>Criar seu contexto de nuvem

1. Para começar, você pode ver quais contextos você tem examinando a seção contextos do painel do Docker:

   ![Mostra apenas o contexto padrão](media/defaultcontext.png)

Você só deve ver o contexto padrão para o trabalho local.

1. Para implantar na nuvem, você precisa criar um novo contexto ACI, mas para fazer isso, primeiro você precisa da extensão de conta do Azure para autenticar com o Azure.

   ![Adicionando extensão do Azure](media/addazureextension.png)

Você precisará configurar uma conta do Azure se ainda não tiver uma.

1. Agora você pode criar o novo contexto ACI. Você pode fazer isso clicando no botão de adição na seção **contextos** da exibição do Docker.

   ![Criando o contexto do ACI](media/createnewcontext.png)

Isso perguntará em qual grupo de recursos você deseja executar esses contêineres. Selecione um grupo existente usando as teclas de direção ou use a opção padrão para usar o novo grupo.

![Selecionando seu grupo de recursos](media/selectresourcegroup.png)

Agora você pode ver o contexto do ACI listado e pode clicar com o botão direito do mouse para torná-lo seu foco atual/em uso:

![O novo contexto ACI pode ser selecionado](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>Executar contêineres na nuvem

1. Agora, use o contexto ACI e execute o contêiner.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. Tendo executado isso, agora Observe o contêiner em seu contexto.

   ![Contêiner em execução no seu contexto ACI](media/contextcontainer.png)

1. Para verificar se tudo está funcionando corretamente, você pode clicar com o botão direito do mouse no contêiner em execução e escolher **Exibir no navegador**.

   ![Contêiner em ACI com IP público](media/containerinaci.png)

E você pode ver que o contêiner está sendo executado em um IP público e funcionando corretamente!

1. Agora, você pode ter uma olhada em nosso contêiner em execução para ver como ele está funcionando. Você pode começar examinando os logs de contêiner:
 
 ```bash
   docker logs distracted-jackson
   ```

1. Você também pode executar o exec em seu contêiner como faria com um contêiner local.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. Por fim, para limpar o espaço de trabalho e verificar se você não está sendo cobrado por continuar a executar o contêiner de teste, basta clicar com o botão direito do mouse no contêiner em execução e escolher **remover**.

## <a name="recap"></a>Recapitulação

Fantástico, agora você colocou sua carga de trabalho e a implantou na nuvem com êxito pela primeira vez. Você pode fazer tudo isso na linha de comando também no contexto do ACI usando o `docker run` e também usando `docker compose up` o para executar seus aplicativos de vários contêineres. Para saber mais sobre como executar seus contêineres na nuvem, leia a documentação estendida [sobre como usar o ACI](https://docs.docker.com/engine/context/aci-integration/).

## <a name="next-steps"></a>Próximas etapas

Continue com o tutorial!

> [!div class="nextstepaction"]
> [O que vem a seguir](whats-next.md)
