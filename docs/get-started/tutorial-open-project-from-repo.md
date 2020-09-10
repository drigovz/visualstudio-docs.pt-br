---
title: 'Tutorial: abrir um projeto de um repositório'
description: Saiba como abrir um projeto em um repositório Git ou DevOps do Azure usando o Visual Studio.
ms.custom: get-started
ms.date: 03/30/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ad609e9cf6a00a1b966e5d63589592239f215b01
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743036"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Tutorial: abrir um projeto de um repositório

Neste tutorial, você usará o Visual Studio para se conectar a um repositório pela primeira vez e, em seguida, abrir um projeto nele.

::: moniker range="vs-2017"

Se você ainda não instalou o Visual Studio, vá para a página de [downloads do Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalá-lo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se você ainda não instalou o Visual Studio, vá para a página de [downloads do Visual Studio](https://visualstudio.microsoft.com/downloads) para instalá-lo gratuitamente.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Abrir um projeto de um repositório GitHub

::: moniker range="vs-2017"

1. Abra o Visual Studio 2017.

1. Na barra de menus superior, escolha **Arquivo** > **Abrir** > **Abrir do Controle do Código-Fonte**.

   O painel **Team Explorer – Conectar** é aberto.

    ![A janela do Team Explorer no IDE do Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Na seção **Repositórios Git Locais** , escolha **Clone**.

    ![Escolher Clone na seção Repositórios Git Locais](./media/open-proj-repo-local-git-repo-clone.png)

1. Na caixa que diz ***Insira a URL de um repositório Git para clonar***, digite ou cole a URL do seu repositório e pressione **Enter**. (Talvez você veja um prompt para entrar no GitHub; caso ocorra, entre).

   Depois que o Visual Studio clona o repositório, o Team Explorer é fechado e o Gerenciador de Soluções é aberto. É exibida uma mensagem que diz *Clique em Soluções e Pastas acima para exibir uma lista de Soluções*. Escolha **Soluções e Pastas**.

   ![Escolher "Soluções e Pastas" no Gerenciador de Soluções](./media/open-proj-repo-github-solutions-folders.png)

1. Se houver um arquivo de solução disponível, ele será exibido no menu suspenso "Soluções e Pastas". Escolha-o, e o Visual Studio abrirá sua solução.

   ![Escolha o que você deseja abrir na lista suspensa do Gerenciador de Soluções](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se você não tiver um arquivo de solução (especificamente, um arquivo .sln) no seu repositório, o menu suspenso mostrará a mensagem "Nenhuma solução encontrada". No entanto, você pode clicar duas vezes em qualquer arquivo no menu de pastas para abri-lo no editor de códigos do Visual Studio.

### <a name="review-your-work"></a>Examinar seu trabalho

Exiba a animação a seguir para verificar o trabalho que você concluiu a seção anterior.

   ![Animação da abertura de um projeto em um repositório GitHub usando o Visual Studio](./media/open-project-from-github.gif)

::: moniker-end

::: moniker range="vs-2019"

1. Abra o Visual Studio 2019.

1. Na janela de início, escolha **Clonar ou verificar código**.

   ![Exibir a janela 'Criar um novo projeto'](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Insira ou digite a localização do repositório e, em seguida, escolha **Clonar**.

   ![Exibir a janela 'Clonar ou verificar código'](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   O Visual Studio abre o projeto do repositório.

1. Se houver um arquivo de solução disponível, ele será exibido no menu suspenso "Soluções e Pastas". Escolha-o, e o Visual Studio abrirá sua solução.

   ![Escolha o que você deseja abrir na lista suspensa do Gerenciador de Soluções](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se você não tiver um arquivo de solução (especificamente, um arquivo .sln) no seu repositório, o menu suspenso mostrará a mensagem "Nenhuma solução encontrada". No entanto, você pode clicar duas vezes em qualquer arquivo no menu de pastas para abri-lo no editor de códigos do Visual Studio.

::: moniker-end

## <a name="open-a-project-from-an-azure-devops-repo"></a>Abrir um projeto de um repositório Azure DevOps

::: moniker range="vs-2017"

1. Abra o Visual Studio 2017.

1. Na barra de menus superior, escolha **Arquivo** > **Abrir** > **Abrir do Controle do Código-Fonte**.

   O painel **Team Explorer – Conectar** é aberto.

    ![A janela do Team Explorer no IDE do Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Há duas maneiras de se conectar ao repositório Azure DevOps:

      - Na seção **Provedores de Serviços Hospedados**, escolha **Conectar... **.

        ![A seção Provedores de Serviços Hospedados da janela Team Explorer no IDE do Visual Studio](./media/open-proj-repo-azure-devops.png)

      - Na lista suspensa **Gerenciar Conexões**, escolha **Conectar-se a um Projeto...**.

        ![A seção Gerenciar Conexões da janela Team Explorer no IDE do Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Na caixa de diálogo **Conectar-se a um Projeto**, escolha o repositório a que você deseja se conectar e escolha **Clone**.

      ![A caixa de diálogo "Conectar-se a um Projeto" gerada a partir do Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > O que é exibido na caixa de listagem depende dos repositórios Azure DevOps a que você tem acesso.

1. Depois que o Visual Studio clona o repositório, o Team Explorer é fechado e o Gerenciador de Soluções é aberto. É exibida uma mensagem que diz *Clique em Soluções e Pastas acima para exibir uma lista de Soluções*. Escolha **Soluções e Pastas**.

      ![A notificação "Soluções e Pastas" do Team Explorer no Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Um arquivo de solução (especificamente, um arquivo .sln) será exibido no menu suspenso "Soluções e Pastas". Escolha-o, e o Visual Studio abrirá sua solução.

   Se você não tiver um arquivo de solução no seu repositório, o menu suspenso mostrará a mensagem "Nenhuma solução encontrada". No entanto, você pode clicar duas vezes em qualquer arquivo no menu de pastas para abri-lo no editor de códigos do Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Abra o Visual Studio 2019.

1. Na janela de início, escolha **Clonar ou verificar código**.

   ![Exibir a janela 'Criar um novo projeto'](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Na seção **Navegar em um repositório**, escolha **Azure DevOps**.

   ![Exibir a janela 'Clonar ou verificar código'](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Se você vir uma janela de entrada, entre em sua conta.

1. Na caixa de diálogo **Conectar-se a um Projeto**, escolha o repositório a que você deseja se conectar e escolha **Clone**.

      ![A caixa de diálogo "Conectar-se a um Projeto" gerada a partir do Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > O que é exibido na caixa de listagem depende dos repositórios Azure DevOps a que você tem acesso.

   O Visual Studio abrirá o **Team Explorer** e uma notificação será exibida quando a clonagem for concluída.

     ![A janela do Team Explorer no Visual Studio após a conclusão da clonagem](./media/vs-2019/clone-complete-azure-devops.png)

1. Para exibir pastas e arquivos, escolha o link **Mostrar Exibição de Pasta**.

     ![A seção Soluções da janela do Team Explorer no Visual Studio após a conclusão da clonagem](./media/vs-2019/show-folder-view-azure-devops.png)

     O Visual Studio abre o **Gerenciador de Soluções**.

1. Escolha o link **Soluções e Pastas** para procurar um arquivo de solução (especificamente, um arquivo .sln) para abrir.

      ![A notificação "Soluções e Pastas" do Team Explorer no Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Se você não tiver um arquivo de solução no seu repositório, a mensagem "Nenhuma Solução Encontrada" aparecerá. No entanto, você pode clicar duas vezes em qualquer arquivo no menu de pastas para abri-lo no editor de códigos do Visual Studio.

::: moniker-end

## <a name="next-steps"></a>Próximas etapas

Se estiver pronto para codificar com o Visual Studio, aprofunde-se em qualquer um dos seguintes tutoriais específicos a um idioma:

- [Tutoriais do Visual Studio | **C#**](./csharp/index.yml)
- [Tutoriais do Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Tutoriais do Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Tutoriais do Visual Studio | **Python**](../python/index.yml)
- [Tutoriais do Visual Studio | **JavaScript**, **TypeScript** e **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Veja também

- [Azure DevOps Services: introdução ao Azure Repos e ao Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: introdução ao Azure DevOps](/learn/modules/get-started-with-devops/)