---
title: Acesse o Objeto DTE a partir de uma extensão de editor
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
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697658"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Passo a passo: Acesse o objeto DTE a partir de uma extensão do editor

Em VSPackages, você pode obter o <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> objeto DTE chamando o método com o tipo de objeto DTE. Nas extensões MEF (Managed Extensibility Framework, framework de extensibilidade gerenciada), você pode importar <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> e, em seguida, chamar o <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método com um tipo de <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Pré-requisitos

Para acompanhar este passo a passo, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Obter o objeto DTE

1. Crie um projeto C# VSIX e nomeie-o **DTETest**. Adicione um modelo de item **do Editor Classifier** e nomeie-o **DTETest**.

   Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Adicione as seguintes referências de montagem ao projeto:

    - Microsoft.visualStudio.shell.framework
    - Microsoft.VisualStudio.Shell.Immutável.10.0

3. No arquivo *DTETestProvider.cs,* adicione `using` as seguintes diretivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Na `DTETestProvider` classe, importe um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. No `GetClassifier()` método, adicione o seguinte `return` código antes da declaração:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Adicione as seguintes referências de montagem ao projeto:

   - Envdte
   - Microsoft.visualStudio.shell.framework

3. No arquivo *DTETestProvider.cs,* adicione `using` as seguintes diretivas:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Na `DTETestProvider` classe, importe um <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. No `GetClassifier()` método, adicione o seguinte `return` código antes da declaração:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Confira também

- [Pontos de extensão de serviços de idiomas e editores](../extensibility/language-service-and-editor-extension-points.md)
- [Iniciar o Visual Studio usando DTE](launch-visual-studio-dte.md)
