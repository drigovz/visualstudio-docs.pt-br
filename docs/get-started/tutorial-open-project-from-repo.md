---
title: 'Tutorial: Abrir um projeto de um repositório'
description: Saiba como abrir um projeto em um repositório Git ou DevOps do Azure usando o Visual Studio.
ms.custom: get-started
ms.date: 03/13/2019
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
ms.openlocfilehash: f017e0ef3d7b76ba4d5de18ecab614f030b07501
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070068"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Tutorial: Abrir um projeto de um repositório

Neste tutorial, você usará o Visual Studio para se conectar a um repositório pela primeira vez e, em seguida, abrir um projeto nele.

::: moniker range="vs-2017"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) para instalá-lo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+rc) para instalá-lo gratuitamente.

::: moniker-end

## <a name="open-a-project-from-a-github-repo"></a>Abrir um projeto de um repositório GitHub

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

### <a name="review-your-work"></a>Revisar seu trabalho

Exiba a animação a seguir para verificar o trabalho que você concluiu a seção anterior.

   ![Animação da abertura de um projeto em um repositório GitHub usando o Visual Studio](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo"></a>Abrir um projeto de um repositório Azure DevOps

1. Abra o Visual Studio 2017.

1. Na barra de menus superior, escolha **Arquivo** > **Abrir** > **Abrir do Controle do Código-Fonte**.

   O painel **Team Explorer – Conectar** é aberto.

    ![A janela do Team Explorer no IDE do Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Há duas maneiras de se conectar ao repositório Azure DevOps:

      - Na seção **Provedores de Serviços Hospedados**, escolha **Conectar...** .

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
  
## <a name="next-steps"></a>Próximas etapas

Se estiver pronto para codificar com o Visual Studio, aprofunde-se em qualquer um dos seguintes tutoriais específicos a um idioma:

- [Tutoriais do Visual Studio | **C#**](./csharp/index.yml)
- [Tutoriais do Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Tutoriais do Visual Studio | **C++**](/cpp/get-started/)
- [Tutoriais do Visual Studio | **Python**](/visualstudio/python/)
- [Tutoriais do Visual Studio | **JavaScript**, **TypeScript** e **Node.js**](/visualstudio/javascript/)

## <a name="see-also"></a>Consulte também

- [Azure DevOps Services: introdução ao Azure Repos e ao Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: introdução ao Azure DevOps](/learn/modules/get-started-with-devops/)