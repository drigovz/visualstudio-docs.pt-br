---
title: Acessar o objeto DTE por meio de uma extensão do editor
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269088"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Walkthrough: acessar o objeto DTE a partir de uma extensão do editor

No VSPackages, você pode obter o objeto DTE chamando o método <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> com o tipo do objeto DTE. Em extensões Managed Extensibility Framework (MEF), você pode importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e, em seguida, chamar o método <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> com um tipo de <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

Para seguir este passo a passos, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obter o objeto DTE

1. Crie um C# projeto VSIX e nomeie-o **DTETest**. Adicione um modelo de item de **classificação do editor** e nomeie-o **DTETest**.

   Para obter mais informações, consulte [criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Adicione as seguintes referências de assembly ao projeto:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. No arquivo *DTETestProvider.cs* , adicione as seguintes diretivas de `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Na classe `DTETestProvider`, importe um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. No método `GetClassifier()`, adicione o seguinte código antes da instrução `return`:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Adicione as seguintes referências de assembly ao projeto:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. No arquivo *DTETestProvider.cs* , adicione as seguintes diretivas de `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Na classe `DTETestProvider`, importe um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. No método `GetClassifier()`, adicione o seguinte código antes da instrução `return`:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Veja também

- [Pontos de extensão do serviço de linguagem e do editor](../extensibility/language-service-and-editor-extension-points.md)
- [Iniciar o Visual Studio usando DTE](launch-visual-studio-dte.md)
