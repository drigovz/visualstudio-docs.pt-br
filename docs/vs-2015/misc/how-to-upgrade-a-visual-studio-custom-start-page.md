---
title: Como atualizar uma página inicial personalizada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: a7854de705a961463b1e8435e7340548cfc23bf3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74293375"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Como atualizar uma página de início personalizada do Visual Studio
Você pode atualizar uma página inicial personalizada do Visual Studio 2010 ou do Visual Studio 2012 para o Visual Studio 2015 seguindo as etapas listadas abaixo.

> [!WARNING]
> A página inicial personalizada atualizada neste procedimento é aquela criada com o modelo de [página inicial personalizada](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.CustomStartPageProjectTemplate) na galeria do Visual Studio. Sua página inicial pode ter outros recursos que precisam ser atualizados.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Para atualizar uma página inicial personalizada para o Visual Studio 2015

1. Verifique se o Visual Studio 2015 e o SDK do Visual Studio 2015 estão instalados. Você pode baixar o VSSDK do [SDK do Microsoft Visual Studio 2013](https://my.visualstudio.com/Downloads?pid=1436).

2. Abra seu projeto de modelo personalizado. Você verá uma mensagem notificando que o projeto deve ser atualizado. Clique em **OK** e aguarde a conclusão da atualização.

3. Nas propriedades do projeto para o projeto de página inicial e o projeto de controle, certifique-se de que a estrutura de destino seja pelo menos .NET Framework 4,5.

4. Na categoria depurar das propriedades do projeto para o projeto página inicial, defina o caminho para a versão do Visual Studio 2015 do devenv.exe.

5. Nas referências de projeto para ambos os projetos, remova as referências a Microsoft. VisualStudio. Shell. 11.0 e adicione referências a Microsoft. VisualStudio. Shell. 14.0.

6. Abra StartPage. XAML com o editor de XML e faça as seguintes alterações:

    1. Atualize os namespaces. Altere as seguintes linhas:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         para o seguinte:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. Abra MyControl. XAML e altere a referência do namespace `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` para `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .