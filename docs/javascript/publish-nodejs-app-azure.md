---
title: Publicar um aplicativo Node.js no Serviço de Aplicativo do Linux
description: Publique aplicativos Node.js criados no Visual Studio no Serviço de Aplicativo do Linux no Azure
ms.date: 11/22/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c83516891a33a026399a6e5fcfc2458b5e03a0bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945429"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Publicar um aplicativo Node.js no Azure (Serviço de Aplicativo do Linux)

Este tutorial orienta você pela tarefa de criação de um aplicativo Node.js simples e sua publicação no Azure.

Ao publicar um aplicativo Node.js no Azure, há várias opções. Entre elas, há o Serviço de Aplicativo do Azure, uma VM que executa um sistema operacional de sua escolha, o AKS (Serviço de Contêiner do Azure) para o gerenciamento com o Kubernetes, uma Instância de Contêiner usando o Docker e muito mais. Para obter mais detalhes sobre cada uma dessas opções, confira [Computação](https://azure.microsoft.com/product-categories/compute/).

Neste tutorial, você implantará o aplicativo no [Serviço de Aplicativo do Linux](/azure/app-service/containers/app-service-linux-intro).
O Serviço de Aplicativo do Linux implanta um contêiner do Docker do Linux para executar o aplicativo Node.js (ao contrário do Serviço de Aplicativo do Windows, que executa os aplicativos Node.js com a proteção do IIS no Windows).

Este tutorial mostra como criar um aplicativo Node.js com base em um modelo instalado com as Ferramentas Node.js para Visual Studio, efetuar push do código para um repositório no GitHub e, em seguida, provisionar um Serviço de Aplicativo do Azure por meio do portal da Web do Azure, de modo você possa realizar a implantação por meio do repositório GitHub. Para usar a linha de comando para provisionar o Serviço de Aplicativo do Azure e efetuar push do código por meio de um repositório Git local, confira [Criar aplicativo Node.js](/azure/app-service/containers/quickstart-nodejs).

Neste tutorial, você aprenderá como:
> [!div class="checklist"]
> * Criar um projeto Node.js
> * Criar um repositório GitHub para o código
> * Criar um Serviço de Aplicativo do Linux no Azure
> * Implantar no Linux

## <a name="prerequisites"></a>Pré-requisitos

* Você precisa ter o Visual Studio instalado e a carga de trabalho de desenvolvimento de Node.js.

    ::: moniker range=">=vs-2019"
    Se você ainda não instalou o Visual Studio 2019, vá para a página de [downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/) para instalá-lo gratuitamente.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Se você ainda não tiver instalado o Visual Studio 2017, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/) para instalá-lo gratuitamente.
    ::: moniker-end

    Se você precisar instalar a carga de trabalho, mas já tiver o Visual Studio, vá para **ferramentas**  >  **obter ferramentas e recursos...**, que abre o instalador do Visual Studio. Escolha a carga de trabalho **Desenvolvimento de Node.js** e, em seguida, selecione **Modificar**.

    ![Carga de trabalho Node.js no instalador do VS](../ide/media/quickstart-nodejs-workload.png)

* Você precisa ter o runtime do Node.js instalado.

    Se não o tiver instalado, instale a versão LTS do site do [Node.js](https://nodejs.org/en/download/). Em geral, o Visual Studio detecta automaticamente o runtime do Node.js instalado. Se ele não detectar um runtime instalado, você poderá configurar seu projeto para fazer referência ao runtime instalado na página de propriedades (depois de criar um projeto, clique com botão direito do mouse no nó do projeto e escolha **Propriedades**).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Criar um projeto Node.js para execução no Azure

1. Abra o Visual Studio.

1. Criar um novo aplicativo TypeScript Express.

    ::: moniker range=">=vs-2019"
    Pressione **Esc** para fechar a janela de início. Digite **Ctrl + Q** para abrir a caixa de pesquisa, digite **Node.js** e, em seguida, escolha **Criar um novo Aplicativo Básico Azure Node.js Express 4** (TypeScript). Na caixa de diálogo que aparece, escolha **Criar**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na barra de menus superior, escolha **arquivo**  >  **novo**  >  **projeto**. No painel esquerdo da caixa de diálogo **Novo Projeto**, expanda **TypeScript** e escolha **Node.js**. No painel central, escolha **Aplicativo Azure Node.js Express 4 básico** e, em seguida, **OK**.

    ![Criar um aplicativo TypeScript Express](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    Se você não vir o modelo de projeto **Aplicativo Azure Node.js Express 4 básico**, adicione a carga de trabalho de **desenvolvimento do Node.js**. Confira instruções detalhadas nos [Pré-requisitos](#prerequisites).

    O Visual Studio criará o projeto e o abrirá no Gerenciador de Soluções (painel direito).

1. Pressione **F5** para criar e executar o aplicativo e verifique se tudo está funcionando conforme esperado.

1. Selecione **arquivo**  >  **Adicionar ao controle do código-fonte** para criar um repositório git local para o projeto.

    Neste ponto, um aplicativo Node.js que usa a estrutura Express e é escrito em TypeScript está funcionando e fez o check-in no controle do código-fonte local.

1. Edite o projeto conforme desejado antes de continuar com as próximas etapas.

## <a name="push-code-from-visual-studio-to-github"></a>Efetuar push do código por meio do Visual Studio para o GitHub

Para configurar o GitHub para o Visual Studio:

1. Verifique se a [Extensão do GitHub para Visual Studio](https://visualstudio.github.com/) está instalada e habilitada usando o item de menu **Ferramentas** > **Extensões e Atualizações**.

2. No menu, selecione **Exibir**  >  **outro**  >  **GitHub** do Windows.

    A janela do GitHub será aberta.

3. Se o botão **Introdução** não for exibido na janela do GitHub, clique em **Arquivo** > **Adicionar ao Controle do Código-fonte** e aguarde até que a interface do usuário seja atualizada.

    ![Abrir a janela do GitHub](../javascript/media/azure-github-get-started.png)

4. Clique em **Introdução**.

    Se você já estiver conectado ao GitHub, a caixa de ferramentas será exibida como na ilustração a seguir.

    ![Configurações do repositório GitHub](../javascript/media/azure-github-publish.png)

5. Preencha os campos a serem publicados pelo novo repositório e, em seguida, clique em **Publicar**.

    Após alguns instantes, uma faixa informando "Repositório criado com êxito" será exibida.

    Na próxima seção, você aprenderá a fazer uma publicação por meio desse repositório em um Serviço de Aplicativo do Azure no Linux.

## <a name="create-a-linux-app-service-in-azure"></a>Criar um Serviço de Aplicativo do Linux no Azure

1. Entre no [portal do Azure](https://portal.azure.com).

2. Selecione **Serviços de Aplicativos** na lista de serviços à esquerda e, em seguida, clique em **Adicionar**.

3. Se necessário, crie um Grupo de Recursos e um plano do Serviço de Aplicativo para hospedar o novo aplicativo.

4. Defina o **Sistema Operacional** como **Linux** e a **Pilha de Runtime** como a versão necessária do Node.js, conforme mostrado na ilustração.

    ![Criar um Serviço de Aplicativo do Linux](../javascript/media/azure-create-appservice-annotated.png)

5. Clique em **Criar** para criar o Serviço de Aplicativo.

    A implantação pode levar alguns minutos.

6. Após a implantação, acesse a seção **Configurações de aplicativo** e adicione uma configuração com o nome `SCM_SCRIPT_GENERATOR_ARGS` e o valor `--node`.

    ![Configurações do aplicativo](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > O processo de implantação do Serviço de Aplicativo usa um conjunto de heurísticas para determinar qual tipo de aplicativo ele deve tentar executar. Se um arquivo *.sln* for detectado no conteúdo implantado, ele presumirá que um projeto baseado no MSBuild está sendo implantado. A configuração adicionada acima substitui essa lógica e especifica explicitamente que se trata de um aplicativo Node.js. Sem essa configuração, o aplicativo Node.js não será implantado se o arquivo *.sln* fizer parte do repositório que está sendo implantado no Serviço de Aplicativo.

7. Em **configurações do aplicativo**, adicione outra configuração com um nome `WEBSITE_NODE_DEFAULT_VERSION` e um valor de `8.9.0` .

8. Após a implantação, abra o Serviço de Aplicativo e selecione **Opções de implantação**.

    ![Opções de implantação](../javascript/media/azure-deployment-options.png)

9. Clique em **Escolher fonte** e, em seguida, escolha **GitHub** e configure as permissões necessárias.

    ![Permissões do GitHub](../javascript/media/azure-choose-source.png)

10. Selecione o repositório e o branch a serem publicados e, em seguida, selecione **OK**.

    ![Publicar no Serviço de Aplicativo do Linux](../javascript/media/azure-repo-and-branch.png)

    A página **Opções de implantação** será exibida durante a sincronização.

    ![Implantando e sincronizando com o GitHub](../javascript/media/azure-deployment-options-sync.png)

    Após a conclusão da sincronização, uma marca de seleção será exibida.

    O site agora está executando o aplicativo Node.js por meio do repositório GitHub e é acessível na URL criada para o Serviço de Aplicativo do Azure (por padrão, o nome fornecido para o Serviço de Aplicativo do Azure seguido de ".azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Modificar o aplicativo e efetuar push das alterações

1. Adicione o código mostrado aqui a *app.ts* após a linha `app.use('/users', users);`. Isso adiciona uma API REST à */api* URL.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Compile o código e teste-o localmente. Em seguida, faça check-in dele e efetue push do código para o GitHub.

    No portal do Azure, são necessários alguns instantes para que as alterações sejam detectadas no repositório GitHub. Em seguida, uma nova sincronização da implantação será iniciada. Isso é semelhante à ilustração a seguir.

    ![Modificar e sincronizar](../javascript/media/azure-changes-detected.png)

3. Após a conclusão da implantação, navegue para o site público e acrescente */api* à URL. A resposta JSON será retornada.

## <a name="troubleshooting"></a>Solução de problemas

* Se o processo do node.exe se tornar inativo (ou seja, uma exceção sem tratamento ocorrer), o contêiner será reinicializado.
* Quando o contêiner for iniciado, ele percorrerá várias heurísticas para descobrir como iniciar o processo do Node.js. Veja os detalhes da implementação em [generateStartupCommand.js](https://github.com/Azure/app-service-builtin-images/blob/master/node/8.9.4/startup/generateStartupCommand.js).
* Conecte-se ao contêiner em execução por meio do SSH para fazer investigações. Faça isso com facilidade usando o portal do Azure. Selecione o Serviço de Aplicativo e role a lista de ferramentas para baixo até chegar a **SSH**, na seção **Ferramentas de Desenvolvimento**.
* Para ajudar com a solução de problemas, vá para as configurações de **Logs de diagnóstico** do Serviço de Aplicativo e altere a configuração de **Log de contêiner do Docker** de **Desativado** para **Sistema de Arquivos**. Os logs são criados no contêiner em */home/LogFiles/* _docker.log* e podem ser acessados na caixa usando o SSH ou FTP(S).
* Um nome de domínio personalizado pode ser atribuído ao site, em vez da URL *.azurewebsites.net atribuída por padrão. Para obter mais detalhes, confira o tópico [Mapear domínio personalizado](/azure/app-service/app-service-web-tutorial-custom-domain).
* A implantação em um site de preparo para a execução de testes adicionais antes da migração para a produção é uma melhor prática. Para obter detalhes sobre como configurar isso, confira o tópico [Criar ambientes de preparo](/azure/app-service/web-sites-staged-publishing).
* Confira as [Perguntas frequentes sobre o Serviço de Aplicativo do Linux](/azure/app-service/containers/app-service-linux-faq) para ver mais perguntas frequentes.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a criar um Serviço de Aplicativo do Linux e implantar um aplicativo Node.js no serviço. Talvez você deseje saber mais sobre o Serviço de Aplicativo do Linux.

> [!div class="nextstepaction"]
> [Serviço de Aplicativo do Linux](/azure/app-service/containers/app-service-linux-intro)
