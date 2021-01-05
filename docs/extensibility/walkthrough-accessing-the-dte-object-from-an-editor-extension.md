---
title: Acessar o objeto DTE por meio de uma extensão do editor
description: Saiba como acessar o objeto DTE por meio de uma extensão do editor usando o exemplo de código neste passo a passos.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a0ee789590bd411fe7955cf739683d016164f49
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863716"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Walkthrough: acessar o objeto DTE a partir de uma extensão do editor

No VSPackages, você pode obter o objeto DTE chamando o <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método com o tipo do objeto DTE. Em extensões Managed Extensibility Framework (MEF), você pode importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e, em seguida, chamar o <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método com um tipo de <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>Pré-requisitos

Para seguir este passo a passos, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obter o objeto DTE

1. Crie um projeto VSIX em C# e nomeie-o **DTETest**. Adicione um modelo de item de **classificação do editor** e nomeie-o **DTETest**.

   Para obter mais informações, consulte [criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Adicione as seguintes referências de assembly ao projeto:

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. imutável. 10.0

3. No arquivo *DTETestProvider.cs* , adicione as seguintes `using` diretivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Na `DTETestProvider` classe, importe um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. No `GetClassifier()` método, adicione o seguinte código antes da `return` instrução:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Adicione as seguintes referências de assembly ao projeto:

   - EnvDTE
   - Microsoft. VisualStudio. Shell. Framework

3. No arquivo *DTETestProvider.cs* , adicione as seguintes `using` diretivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Na `DTETestProvider` classe, importe um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. No `GetClassifier()` método, adicione o seguinte código antes da `return` instrução:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Consulte também

- [Pontos de extensão do serviço de linguagem e do editor](../extensibility/language-service-and-editor-extension-points.md)
- [Iniciar o Visual Studio usando DTE](launch-visual-studio-dte.md)
