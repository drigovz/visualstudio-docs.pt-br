---
title: Usar uma versão do .NET Framework como destino
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8bdcade321c3660e89ab6b7cf6e0b79471b393
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548607"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Como: Direcionar a uma versão do .NET Framework

Este artigo descreve como destinar para uma versão do .NET Framework quando você cria um projeto. Ele também descreve como alterar a versão de destino em uma versão existente de um projeto do Visual Basic, C# ou F#.

> [!IMPORTANT]
> Para obter informações sobre como alterar a versão de destino de projetos do C++, confira [Como: Modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Destinar para uma versão ao criar um projeto

Quando você cria um projeto, as versões do .NET Framework disponíveis dependem de quais versões estão instaladas e no modelo de projeto selecionado.

1. Na barra de menus, selecione **Arquivo** > **Novo** > **Projeto**.

1. Escolha um modelo para o tipo de projeto que você deseja criar. Insira um nome para o projeto.

1. Na lista suspensa de **Framework** na parte inferior da caixa de diálogo, escolha a versão do .NET Framework que você deseja que o projeto tenha como destino.

   A lista de estruturas mostra somente as versões que são aplicáveis para o modelo que você escolheu. Alguns tipos de projeto, como .NET Core, não exigem o .NET Framework. Nesses casos, a lista suspensa **Framework** está oculta.

   ::: moniker range="vs-2017"

   ![A lista suspensa Estrutura na caixa de diálogo Novo Projeto](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Seletor de Framework no VS 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Continue com a [criação do projeto](create-new-project.md).

## <a name="change-the-targeted-version"></a>Alterar a versão de destino

É possível alterar a versão de destino do .NET Framework em um projeto do Visual Basic, C# ou F# seguindo este procedimento.

1. No **Gerenciador de Soluções**, abra o menu de atalho do projeto que você deseja alterar e, em seguida, escolha **Propriedades**.

    ![Propriedades do Gerenciador de Soluções do Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. Na coluna esquerda da janela **Propriedades**, escolha a guia **Aplicativo**.

    ![Guia Aplicativo de Propriedades de Aplicativo do Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Depois de criar um aplicativo UWP, não é possível alterar a versão de destino do Windows ou do .NET Framework.

1. Na lista **Estrutura de Destino**, escolha a versão desejada.

1. Na caixa de diálogo de verificação exibida, escolha o botão **Sim**.

    O projeto é descarregado. Quando é recarregado, ele se destina à versão do .NET Framework que você acabou de escolher.

    > [!NOTE]
    > Se seu código contiver referências a outra versão do .NET Framework que não seja a que você o destinou, mensagens de erro poderão aparecer quando você compilar ou executar o código. Para resolver esses erros, você deverá modificar as referências. Consulte [Solução de problemas de erros de definição de destino do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Consulte também

- [Visão geral de multiplataforma no Visual Studio](../ide/visual-studio-multi-targeting-overview.md)
- [Solução de problemas de erros de definição de destino do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Página Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Como: Modificar a estrutura de destino e o conjunto de ferramentas da plataforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)