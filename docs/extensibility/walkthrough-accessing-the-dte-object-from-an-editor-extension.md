---
title: Acessar o objeto DTE de uma extensão do editor
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3e21ea3d05350a59d62fc9da9e0387f072ec16
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878196"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Passo a passo: Acessar o objeto DTE de uma extensão do editor

Em VSPackages, você pode obter o objeto DTE chamando o <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método com o tipo do objeto DTE. Nas extensões do Managed Extensibility Framework (MEF), você pode importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e, em seguida, chamar o <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método com um tipo de <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Pré-requisitos

Para seguir este passo a passo, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obtenha o objeto DTE

1. Criar um C# VSIX do projeto e denomine **DTETest**. Adicionar um **classificador de Editor** modelo de item e nomeie-o **DTETest**.

   Para obter mais informações, consulte [criar uma extensão com um modelo de item editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Adicione a seguinte referência de assembly ao projeto:

    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. No *DTETestProvider.cs* do arquivo, adicione o seguinte `using` diretivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. No `DTETestProvider` classe, importar um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. No `GetClassifier()` método, adicione o seguinte código antes do `return` instrução:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Adicione as seguintes referências de assembly ao projeto:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. No *DTETestProvider.cs* do arquivo, adicione o seguinte `using` diretivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. No `DTETestProvider` classe, importar um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. No `GetClassifier()` método, adicione o seguinte código antes do `return` instrução:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Consulte também

- [Pontos de extensão de editor e o serviço de linguagem](../extensibility/language-service-and-editor-extension-points.md)
- [Inicie o Visual Studio usando DTE](launch-visual-studio-dte.md)