---
title: Acessar o objeto DTE de uma extensão do editor
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
ms.openlocfilehash: 1fb22793c3bfa805fae11c8bbea7f07c06fd5a85
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322784"
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