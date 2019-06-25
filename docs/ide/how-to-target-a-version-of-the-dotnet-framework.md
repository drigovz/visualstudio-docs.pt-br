---
title: Definir uma versão do .NET como destino
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET [Visual Studio]
- .NET version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2c316610fc007e3e8642567c01a5172feb461bda
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747131"
---
# <a name="how-to-target-a-version-of-net"></a>Como: Definir uma versão do .NET como destino

Este artigo descreve como definir uma versão específica do .NET Framework como destino ao criar um projeto do .NET Framework. Ele também descreve como alterar a versão de destino em uma versão existente de um projeto do Visual Basic, C# ou F#.

> [!IMPORTANT]
> Para obter informações sobre como alterar a versão de destino de projetos do C++, confira [Como: Modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="target-a-version-when-you-create-a-project"></a>Destinar para uma versão ao criar um projeto

Quando você cria um projeto do .NET Framework, as versões do .NET Framework disponíveis dependem de quais versões estão instaladas e no modelo de projeto selecionado.

1. Na barra de menus, selecione **Arquivo** > **Novo** > **Projeto**.

1. Escolha um modelo do .NET Framework para o tipo de projeto que deseja criar.

1. Na lista suspensa de **Framework** na parte inferior da caixa de diálogo, escolha a versão do .NET Framework que você deseja que o projeto tenha como destino.

   A lista de estruturas mostra somente as versões que são aplicáveis para o modelo que você escolheu.

   > [!NOTE]
   > Alguns tipos de projeto, como .NET Core, não exibem a lista suspensa **Framework**.

   ::: moniker range="vs-2017"

   ![Lista suspensa Framework na caixa de diálogo Novo Projeto do Visual Studio 2017](media/vside-newproject-framework.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Seletor de Framework no VS 2019](media/vs-2019/configure-new-project-framework.png)

   ::: moniker-end

1. Continue com a [criação do projeto](create-new-project.md).

## <a name="change-the-targeted-version"></a>Alterar a versão de destino

Altere a versão de destino do .NET em um projeto do Visual Basic, C# ou F# seguindo este procedimento.

1. No **Gerenciador de Soluções**, abra o menu de atalho do projeto que você deseja alterar e, em seguida, escolha **Propriedades**.

    ![Propriedades do Gerenciador de Soluções do Visual Studio](../ide/media/vs_slnexplorer_properties.png)

1. Na coluna esquerda da janela **Propriedades**, escolha a guia **Aplicativo**.

    ![Guia Aplicativo de Propriedades de Aplicativo do Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png)

    > [!NOTE]
    > Depois de criar um aplicativo UWP, você não poderá alterar a versão de destino do Windows ou do .NET.

1. Na lista **Estrutura de Destino**, escolha a versão desejada.

1. Na caixa de diálogo de verificação exibida, escolha o botão **Sim**.

    O projeto é descarregado. Quando ele é recarregado, ele é direcionado à versão do .NET recém-escolhida.

    > [!NOTE]
    > Se o código contiver referências a outra versão do .NET que não seja a que você o direcionou, poderão ser exibidas mensagens de erro quando você compilar ou executar o código. Para resolver esses erros, você deverá modificar as referências. Confira [Solução de problemas de erros de direcionamento do .NET](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Consulte também

- [Visão geral do direcionamento de estrutura](../ide/visual-studio-multi-targeting-overview.md)
- [Solução de problemas de erros de definição de destino do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)
- [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Página Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Como: Modificar a estrutura de destino e o conjunto de ferramentas da plataforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)