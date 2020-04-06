---
title: Criando uma extensão com um VSPackage | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739532"
---
# <a name="create-an-extension-with-a-vspackage"></a>Crie uma extensão com um VSPackage

Este passo a passo mostra como criar um projeto VSIX e adicionar um item de projeto VSPackage. Usaremos o VSPackage para obter o serviço UI Shell para mostrar uma caixa de mensagens.

## <a name="prerequisites"></a>Pré-requisitos

A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Criar um VSPackage

1. Crie um projeto VSIX chamado **FirstPackage**. Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Projeto Novo** procurando por "vsix".

2. Quando o projeto for aberto, adicione um modelo de item de pacote visual studio chamado **FirstPackage**. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Na **caixa de diálogo Adicionar novo item,** vá para A**Extensibilidade** **Visual C#** > e selecione **Visual Studio Package**. No **campo Nome,** na parte inferior da janela, altere o nome do arquivo de comando para *FirstPackage.cs*.

3. Compile o projeto e comece a depuração.

    A instância experimental do Visual Studio aparece. Para obter mais informações sobre a instância experimental, consulte [A instância experimental](../extensibility/the-experimental-instance.md).

4. No caso experimental, abra a janela**Extensões e Atualizações de** **Ferramentas.** >  Você deve ver a extensão **FirstPackage** aqui. (Se você abrir **extensões e atualizações** em sua instância de trabalho do Visual Studio, você não verá **FirstPackage**).

## <a name="load-the-vspackage"></a>Carregar o VSPackage

Neste ponto, a extensão não carrega porque não há nada que faça com que ele carregue. Você geralmente pode carregar uma extensão quando interage com sua interface do usuário (clicando em um comando de menu, abrindo uma janela de ferramenta) ou especificando que o VSPackage deve carregar em um contexto específico de interface do usuário. Para obter mais informações sobre o carregamento de contextos VSPackages e UI, consulte [Loading VSPackages](../extensibility/loading-vspackages.md). Para este procedimento, mostraremos como carregar um VSPackage quando uma solução estiver aberta.

1. Abra o arquivo *FirstPackage.cs.* Procure a declaração `FirstPackage` da classe. Substitua os atributos existentes pelos seguintes atributos:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Vamos adicionar uma mensagem que nos permite saber que o VSPackage foi carregado. Usamos o método do `Initialize()` VSPackage para fazer isso, porque você só pode obter serviços do Visual Studio depois que o VSPackage estiver disponível. (Para obter mais informações sobre como obter serviços, [consulte Como: Obter um serviço](../extensibility/how-to-get-a-service.md).) Substitua `Initialize()` o `FirstPackage` método de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> código que <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> obtém o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> serviço, obtenha a interface e chame seu método.

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

3. Compile o projeto e comece a depuração. A instância experimental aparece.

4. Abra uma solução na instância experimental. Você deve ver uma caixa de mensagem que diz **Primeiro Pacote Dentro inicializar()**.
