---
title: Criar uma extensão com um VSPackage | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b66aef72d9af1ef40a061d1a82d18161a416586
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345354"
---
# <a name="create-an-extension-with-a-vspackage"></a>Criar uma extensão com um VSPackage

Este passo a passo mostra como criar um projeto VSIX e adicione um item de projeto de VSPackage. Usaremos o VSPackage para obter o serviço de Shell de interface do usuário para mostrar uma caixa de mensagem.

## <a name="prerequisites"></a>Prerequisites

A partir do Visual Studio 2015, você não instale o SDK do Visual Studio no Centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Crie um VSPackage

1. Crie um projeto do VSIX chamado **FirstPackage**. Você pode encontrar o modelo de projeto VSIX na **novo projeto** diálogo pesquisando por "vsix".

2. Quando o projeto aberto, adicione um modelo de item de pacote do Visual Studio denominado **FirstPackage**. No **Gerenciador de soluções**, clique com botão direito no nó do projeto e selecione **Add** > **Novo Item**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual c#**  > **extensibilidade** e selecione **Visual Studio Package**. No **nome** campo na parte inferior da janela, altere o nome do arquivo de comando para *FirstPackage.cs*.

3. Compile o projeto e comece a depuração.

    A instância experimental do Visual Studio é exibida. Para obter mais informações sobre a instância experimental, consulte [a instância experimental](../extensibility/the-experimental-instance.md).

4. Na instância experimental, abra o **ferramentas** > **extensões e atualizações** janela. Você deve ver a **FirstPackage** extensão aqui. (Se você abrir **extensões e atualizações** em sua instância de trabalho do Visual Studio, você não verá **FirstPackage**).

## <a name="load-the-vspackage"></a>Carregar o VSPackage

Neste ponto, a extensão não carregar porque não há nada que faz com que ele seja carregado. Em geral, você pode carregar uma extensão ao interagir com sua interface do usuário (clicando em um comando de menu, abrindo uma janela de ferramentas), ou especificando que o VSPackage deverá carregar em um contexto específico de interface do usuário. Para obter mais informações sobre como carregar VSPackages contextos de interface do usuário, consulte [carregar VSPackages](../extensibility/loading-vspackages.md). Para este procedimento, mostraremos como carregar um VSPackage quando uma solução é aberta.

1. Abra o *FirstPackage.cs* arquivo. Procure a declaração do `FirstPackage` classe. Substitua os atributos existentes com os seguintes atributos:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Vamos adicionar uma mensagem que nos informa que carregou o VSPackage. Usamos o VSPackage `Initialize()` somente depois que o VSPackage foi colocado no local de serviços de método para fazer isso, porque você pode obter o Visual Studio. (Para obter mais informações sobre como obter os serviços, consulte [como: Obtenha um serviço](../extensibility/how-to-get-a-service.md).) Substitua o `Initialize()` método de `FirstPackage` com o código que obtém a <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> de serviço, obtém o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface e chama seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> método.

    ```csharp
    protected override void Initialize()
    {
        base.Initialize();

        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(
            0,
            ref clsid,
            "FirstPackage",
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result));
    }
    ```

3. Compile o projeto e comece a depuração. A instância experimental é exibida.

4. Abra uma solução na instância experimental. Você deve ver uma caixa de mensagem que diz **primeiro pacote dentro Initialize ()** .
