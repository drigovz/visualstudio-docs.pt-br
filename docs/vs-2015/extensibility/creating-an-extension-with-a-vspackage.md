---
title: Criando uma extensão com um VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddad7149db75aa662f9427a301c04eaf925146f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197429"
---
# <a name="creating-an-extension-with-a-vspackage"></a>Criando uma extensão com um VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial mostra como criar um projeto VSIX e adicionar um item de projeto VSPackage. Usaremos o VSPackage para obter o serviço de Shell da interface do usuário para mostrar uma caixa de mensagem.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instala o SDK do Visual Studio a partir do centro de download. Ele é incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS mais tarde. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Criando um VSPackage  
  
1. Crie um projeto VSIX chamado **FirstPackage**. Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **novo projeto** em **Visual C#/extensibilidade**.  
  
2. Quando o projeto for aberto, adicione um modelo de item de pacote do Visual Studio chamado **FirstPackage**. Na **Gerenciador de soluções**, clique com o botão direito do mouse no nó do projeto e selecione **Adicionar/novo item**. Na caixa de diálogo **Adicionar novo item** , vá para **Visual C#/extensibilidade** e selecione **pacote do Visual Studio**. No campo **nome** na parte inferior da janela, altere o nome do arquivo de comando para **FirstPackage.cs**.  
  
3. Compile o projeto e comece a depuração.  
  
     A instância experimental do Visual Studio é exibida. Para obter mais informações sobre a instância experimental, consulte [a instância experimental](../extensibility/the-experimental-instance.md).  
  
4. Na instância experimental, abra a janela **ferramentas/extensões e atualizações** . Você deve ver a extensão **FirstPackage** aqui. (Se você abrir **extensões e atualizações** em sua instância de trabalho do Visual Studio, não verá **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Carregando o VSPackage  
 Neste ponto, a extensão não é carregada, porque não há nada que faça com que ela seja carregada. Geralmente, é possível carregar uma extensão quando você interage com sua interface do usuário (clicando em um comando de menu, abrindo uma janela de ferramentas) ou especificando que o VSPackage deve ser carregado em um contexto de interface do usuário específico. Para obter mais informações sobre como carregar VSPackages e contextos de interface do usuário, consulte [carregando VSPackages](../extensibility/loading-vspackages.md). Para este procedimento, mostraremos como carregar um VSPackage quando uma solução estiver aberta.  
  
1. Abra o arquivo FirstPackage.cs. Procure a declaração da classe FirstPackage. Substitua os atributos existentes pelo seguinte:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2. Vamos adicionar uma mensagem que nos permite saber que o VSPackage foi carregado. Usamos o método Initialize () do VSPackage para fazer isso, pois você pode obter os serviços do Visual Studio somente depois que o VSPackage tiver sido site. (Para obter mais informações sobre como obter serviços, consulte [como: obter um serviço](../extensibility/how-to-get-a-service.md).) Substitua o método Initialize () de FirstPackage pelo código que obtém o <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> serviço, obtenha a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface e chame seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> método.  
  
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
  
4. Abra uma solução na instância experimental. Você deverá ver uma caixa de mensagem que diz **primeiro pacote dentro de Initialize ()**.
