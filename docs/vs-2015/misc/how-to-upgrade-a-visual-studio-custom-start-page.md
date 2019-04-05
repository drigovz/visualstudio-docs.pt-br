---
title: 'Como: Atualizar uma página inicial personalizada | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: 4e17ed6ac15dbaee08c596b67a70b53f440a1e1e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58999999"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Como: Atualizar uma página de início personalizados do Visual Studio
Você pode atualizar um Visual Studio 2010 ou Visual Studio 2012 personalizado a página inicial para Visual Studio 2015, seguindo as etapas listadas abaixo.

> [!WARNING]
>  A página inicial personalizada atualizada neste procedimento é aquele criado com o [página inicial personalizada](http://visualstudiogallery.msdn.microsoft.com/f655a5dc-1a2d-4eca-b774-76c352c03b87) modelo na Galeria do Visual Studio. Sua página inicial pode ter outros recursos que precisam ser atualizados.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Para atualizar uma página inicial personalizada para o Visual Studio 2015

1.  Certifique-se de que o Visual Studio 2015 e o SDK do Visual Studio 2015 estão instalados. Você pode baixar do VSSDK [SDK do Microsoft Visual Studio 2013](https://my.visualstudio.com/Downloads?pid=1436).

2.  Abra seu projeto de modelo personalizado. Você verá uma mensagem informando que o projeto deve ser atualizado. Clique em **Okey** e aguarde até que a atualização seja concluída.

3.  Nas propriedades do projeto para o projeto de página de início e o projeto de controle, certifique-se de que a estrutura de destino é pelo menos .NET Framework 4.5.

4.  Na categoria depuração das propriedades do projeto para o projeto de página inicial, defina o caminho para a versão do Visual Studio 2015 do devenv.exe.

5.  Nas referências do projeto para ambos os projetos, remova as referências para Microsoft.VisualStudio.Shell.11.0 e adicionar referências a Microsoft.VisualStudio.Shell.14.0.

6.  Abra StartPage com o editor de XML e faça as seguintes alterações:

    1.  Atualize os namespaces. Altere as seguintes linhas:

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

7.  Abra MyControl.xaml e altere a referência ao namespace `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` para `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .