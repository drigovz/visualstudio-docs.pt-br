---
title: 'Como: Obter um Serviço | Microsoft Docs'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710951"
---
# <a name="how-to-get-a-service"></a>Como: Obter um serviço

Muitas vezes você precisa obter serviços do Visual Studio para acessar diferentes recursos. Em geral, um serviço visual studio fornece uma ou mais interfaces que você pode usar. Você pode obter a maioria dos serviços de um VSPackage.

Qualquer VSPackage que <xref:Microsoft.VisualStudio.Shell.Package> deriva e que tenha sido corretamente sited pode solicitar qualquer serviço global. Como `Package` a classe <xref:System.IServiceProvider>implementa, qualquer VSPackage que deriva também é um provedor de `Package` serviços.

Quando o Visual <xref:Microsoft.VisualStudio.Shell.Package>Studio carrega <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> um, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> ele passa um objeto para o método durante a inicialização. Isso é chamado *de siting* the VSPackage. A `Package` classe envolve este provedor <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> de serviços e fornece o método para obter serviços.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Obtendo um serviço a partir de um VSPackage inicializado

1. Toda extensão do Visual Studio começa com um projeto de implantação vsix, que conterá os ativos de extensão. Crie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] um projeto `GetServiceExtension`VSIX chamado . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Projeto Novo** procurando por "vsix".

2. Agora adicione um modelo de item de comando personalizado chamado **GetServiceCommand**. Na **caixa de diálogo Adicionar novo item,** vá para A**Extensibilidade** **Visual C#** > e selecione **Comando Personalizado**. No **campo Nome,** na parte inferior da janela, altere o nome do arquivo de comando para *GetServiceCommand.cs*. Para obter mais informações sobre como criar um comando personalizado, [crie uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

3. Em *GetServiceCommand.cs,* remova o `MenuItemCommand` corpo do método e adicione o seguinte código:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Esse código recebe um serviço SVsActivityLog <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> e o lança para uma interface, que pode ser usada para gravar no registro de atividades. Por exemplo, [veja Como: Usar o registro de atividades](../extensibility/how-to-use-the-activity-log.md).

4. Compile o projeto e comece a depuração. A instância experimental aparece.

5. No menu **Ferramentas** da instância experimental, encontre o botão **Invocar GetServiceCommand.** Quando você clica neste botão, você deve ver uma caixa de mensagem que diz **Found the activity log service.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Obtendo um serviço de uma janela de ferramenta ou recipiente de controle

Às vezes, você pode precisar obter um serviço de uma janela de ferramenta ou contêiner de controle que não tenha sido localizado, ou então tenha sido sited com um provedor de serviços que não sabe sobre o serviço que você deseja. Por exemplo, você pode querer escrever para o registro de atividades de dentro de um controle.

O <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método estático depende de um provedor de serviços em cache <xref:Microsoft.VisualStudio.Shell.Package> que é inicializado na primeira vez que qualquer VSPackage derivado é sited.

Como o construtor VSPackage é chamado antes do VSPackage ser sited, os serviços globais normalmente não estão disponíveis dentro do construtor VSPackage. [Veja Como: Solucionar problemas para](../extensibility/how-to-troubleshoot-services.md) uma solução de solução.

Aqui está um exemplo da maneira de obter um serviço em uma janela de ferramenta ou outro elemento não-VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Obtendo um serviço do objeto DTE

Você também pode <xref:EnvDTE.DTEClass> obter serviços do objeto. No entanto, você deve obter o objeto DTE como <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> um serviço de um VSPackage ou chamando o método estático.

O objeto DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>implementa , que você pode usar <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>para consultar um serviço usando .

Veja como obter um serviço do objeto DTE.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>Confira também

- [Como: Fornecer um serviço](../extensibility/how-to-provide-a-service.md)
- [Usar e prestar serviços](../extensibility/using-and-providing-services.md)
- [Essenciais de serviço](../extensibility/internals/service-essentials.md)
