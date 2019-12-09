---
title: Como definir uma versão do .NET Framework como destino | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7aae21e2c959939262b88db3b90367c4860d8a74
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670618"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Como destinar uma versão do .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este documento descreve como destinar uma versão do .NET Framework quando você cria um projeto e como alterar a versão de destino em um projeto existente do Visual Basic, Visual C# ou Visual F#.

> [!IMPORTANT]
> Para obter informações sobre como alterar a versão de destino de projetos do C++, consulte [Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

 **Neste tópico**

- [Definindo uma versão como destino ao criar um projeto](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)

- [Alterando a versão de destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)

## <a name="bkmk_new"></a> Definindo uma versão como destino ao criar um projeto
 Ao criar um projeto, a versão do .NET Framework à qual você o destina determina quais modelos é possível usar.

> [!NOTE]
> Nas edições Express do Visual Studio, é necessário criar o projeto primeiro e, em seguida, é possível alterar o destino, conforme descrito em [Alterando a versão de destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing), mais adiante neste tópico.

#### <a name="to-target-a-version-when-you-create-a-project"></a>Para destinar uma versão ao criar um projeto

1. Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.

2. Na lista da parte superior da caixa de diálogo **Novo Projeto**, escolha a versão do .NET Framework que você deseja que o projeto tenha como destino.

    > [!NOTE]
    > Normalmente, somente uma versão do .NET Framework é instalada com o Visual Studio. Se desejar destinar outra versão, primeiramente, você deve verificar se ela está instalada. Consulte [Visão geral do Visual Studio Multi-Targeting](../ide/visual-studio-multi-targeting-overview.md).

3. Na lista de modelos instalados, escolha o tipo de projeto que você deseja criar, nomeie o projeto e escolha o botão **OK**.

     A lista de modelos mostra somente os projetos que são aceitos pela versão do .NET Framework que você escolheu.

## <a name="bkmk_existing"></a> Alterando a versão de destino
 É possível alterar a versão de destino do .NET Framework em um projeto do Visual Basic, Visual C# ou Visual F# seguindo este procedimento.

#### <a name="to-change-the-targeted-version"></a>Para alterar a versão de destino

1. No **Gerenciador de Soluções**, abra o menu de atalho do projeto que você deseja alterar e, em seguida, escolha **Propriedades**.

     ![Propriedades de Gerenciador de Soluções do Visual Studio](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")

    > [!IMPORTANT]
    > Para obter informações sobre como alterar a versão de destino de projetos do C++, consulte [Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

2. Na coluna esquerda da janela Propriedades, escolha a guia **Aplicativo**.

     ![Guia aplicativo de propriedades do aplicativo do Visual Studio](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > Depois de criar um aplicativo da Windows Store, não é possível alterar a versão de destino do Windows ou do .NET Framework.

3. Na lista **Estrutura de Destino**, escolha a versão desejada.

4. Na caixa de diálogo de verificação exibida, escolha o botão **Sim**.

     O projeto é descarregado. Quando é recarregado, ele se destina à versão do .NET Framework que você acabou de escolher.

    > [!NOTE]
    > Se seu código contiver referências a outra versão do .NET Framework que não seja a que você o destinou, mensagens de erro poderão aparecer quando você compilar ou executar o código. Para resolver esses erros, você deverá modificar as referências. Consulte [Solução de problemas de erros de definição de destino do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Consulte também
 [Visão geral de multiplataforma do Visual Studio](../ide/visual-studio-multi-targeting-overview.md) [.NET Framework a criação de vários destinos para projetos Web ASP.net solução de](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) [problemas .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md) página de aplicativos de erros, página de aplicativo [Designer de projeto (C#)](../ide/reference/application-page-project-designer-csharp.md) [, Designer de projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [Configurando projetos](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526) [como modificar o Framework de destino e o conjunto de ferramentas de plataforma](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)
