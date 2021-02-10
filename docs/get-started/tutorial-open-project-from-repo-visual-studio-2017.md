---
title: 'Tutorial: abrir um projeto de um repositório no Visual Studio 2017'
description: Saiba como abrir um projeto em um repositório do git ou DevOps do Azure usando o Visual Studio 2017.
ms.custom: get-started
ms.date: 01/25/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
monikerRange: vs-2017
ms.openlocfilehash: 97bfe7178d3bd744d1e441f8428cd38e8241b721
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951921"
---
# <a name="tutorial-open-a-project-from-a-repo-in-visual-studio-2017"></a>Tutorial: abrir um projeto de um repositório no Visual Studio 2017

Neste tutorial, você usará o Visual Studio 2017 para se conectar a um repositório pela primeira vez e, em seguida, abrir um projeto a partir dele.

> [!TIP]
> Há uma maneira nova e mais totalmente integrada de se conectar com um repositório GitHub no [Visual Studio 2019](https://visualstudio.microsoft.com/downloads). Para obter mais informações, consulte a [**nova experiência de git na página do Visual Studio 2019**](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true) .

## <a name="open-a-project-from-a-github-repo-by-using-visual-studio-2017"></a>Abrir um projeto de um repositório GitHub usando o Visual Studio 2017

1. Abra o Visual Studio 2017.

1. Na barra de menus superior, selecione **arquivo**  >  **abrir**  >  **Abrir do controle do código-fonte**.

   O painel **Team Explorer – Conectar** é aberto.

    ![A janela do Team Explorer no IDE do Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Na seção **repositórios git locais** , selecione **clonar**.

    ![Escolher Clone na seção Repositórios Git Locais](./media/open-proj-repo-local-git-repo-clone.png)

1. Na caixa que diz ***Insira a URL de um repositório Git para clonar**, digite ou cole a URL do seu repositório e pressione _ * Enter * *. (Talvez você veja um prompt para entrar no GitHub; caso ocorra, entre).

   Depois que o Visual Studio clona o repositório, o Team Explorer é fechado e o Gerenciador de Soluções é aberto. É exibida uma mensagem que diz *Clique em Soluções e Pastas acima para exibir uma lista de Soluções*. Escolha **Soluções e Pastas**.

   ![Escolher "Soluções e Pastas" no Gerenciador de Soluções](./media/open-proj-repo-github-solutions-folders.png)

1. Se houver um arquivo de solução disponível, ele será exibido no menu suspenso "Soluções e Pastas". Escolha-o, e o Visual Studio abrirá sua solução.

   ![Escolha o que você deseja abrir na lista suspensa do Gerenciador de Soluções](./media/open-proj-repo-github-solutions-folders-picker.png)

   Se você não tiver um arquivo de solução (especificamente, um arquivo .sln) no seu repositório, o menu suspenso mostrará a mensagem "Nenhuma solução encontrada". No entanto, você pode clicar duas vezes em qualquer arquivo no menu de pastas para abri-lo no editor de códigos do Visual Studio.

### <a name="review-your-work"></a>Examinar seu trabalho

Exiba a animação a seguir para verificar o trabalho que você concluiu a seção anterior.

   ![Animação da abertura de um projeto em um repositório GitHub usando o Visual Studio](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo-by-using-visual-studio-2017"></a>Abrir um projeto de um repositório DevOps do Azure usando o Visual Studio 2017

1. Abra o Visual Studio 2017.

1. Na barra de menus superior, selecione **arquivo**  >  **abrir**  >  **Abrir do controle do código-fonte**.

   O painel **Team Explorer – Conectar** é aberto.

    ![A janela do Team Explorer no IDE do Visual Studio](./media/open-proj-repo-team-explorer.png)

1. Há duas maneiras de se conectar ao repositório Azure DevOps:

      - Na seção **provedores de serviço hospedado** , selecione **conectar...**.

        ![A seção Provedores de Serviços Hospedados da janela Team Explorer no IDE do Visual Studio](./media/open-proj-repo-azure-devops.png)

      - Na lista suspensa **gerenciar conexões** , selecione **conectar a um projeto...**.

        ![A seção Gerenciar Conexões da janela Team Explorer no IDE do Visual Studio](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Na caixa de diálogo **conectar a um projeto** , escolha o repositório ao qual você deseja se conectar e, em seguida, selecione **clonar**.

      ![A caixa de diálogo ' conectar-se a um projeto ' gerada no Visual Studio](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > O que é exibido na caixa de listagem depende dos repositórios Azure DevOps a que você tem acesso.

1. Depois que o Visual Studio clona o repositório, o Team Explorer é fechado e o Gerenciador de Soluções é aberto. É exibida uma mensagem que diz *Clique em Soluções e Pastas acima para exibir uma lista de Soluções*. Escolha **Soluções e Pastas**.

      ![A notificação "Soluções e Pastas" do Team Explorer no Visual Studio](./media/open-proj-repo-solutions-folders.png)

   Um arquivo de solução (especificamente, um arquivo .sln) será exibido no menu suspenso "Soluções e Pastas". Escolha-o, e o Visual Studio abrirá sua solução.

   Se você não tiver um arquivo de solução no seu repositório, o menu suspenso mostrará a mensagem "Nenhuma solução encontrada". No entanto, você pode clicar duas vezes em qualquer arquivo no menu de pastas para abri-lo no editor de códigos do Visual Studio.

## <a name="next-steps"></a>Próximas etapas

Se você estiver pronto para codificar com o Visual Studio 2017, aprofunde-se em qualquer um dos seguintes tutoriais específicos de idioma:

- [Tutoriais do Visual Studio | **C#**](./csharp/index.yml)
- [Tutoriais do Visual Studio | **Visual Basic**](./visual-basic/index.yml)
- [Tutoriais do Visual Studio | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Tutoriais do Visual Studio | **Python**](../python/index.yml)
- [Tutoriais do Visual Studio | **JavaScript**, **TypeScript** e **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Confira também

- [Azure DevOps Services: introdução ao Azure Repos e ao Visual Studio](/azure/devops/repos/git/gitquickstart/)
- [Microsoft Learn: introdução ao Azure DevOps](/learn/modules/get-started-with-devops/)
- [Nova experiência de git no Visual Studio 2019](../ide/git-with-visual-studio.md?view=vs-2019&preserve-view=true)
