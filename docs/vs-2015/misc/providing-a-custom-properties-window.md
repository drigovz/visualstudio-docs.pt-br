---
title: Fornecendo uma janela de propriedades personalizadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810690"
---
# <a name="providing-a-custom-properties-window"></a>Fornecendo uma janela Propriedades personalizada
É possível fornecer sua própria janela de **Propriedades** para um determinado sistema de projeto, em vez de estender a janela **Propriedades** fornecida pelo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE (ambiente de desenvolvimento integrado). O cenário mais frequentemente encontrado é quando você mesmo implementa o objeto no quadro da janela.  
  
 No caso de você não implementar o objeto no quadro da janela, mas ainda tiver acesso a ele por outros meios, há várias maneiras de acessar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interface, conforme listado no último procedimento desta página...  
  
### <a name="to-provide-your-properties-window"></a>Para fornecer seu janela Propriedades  
  
1. Defina um GUID que represente a implementação da janela **Propriedades** .  
  
2. Em sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementação, use o <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> serviço para oferecer a janela **Propriedades** como um serviço para o ambiente do Visual Studio.  
  
### <a name="to-call-your-properties-window"></a>Para chamar a janela Propriedades  
  
1. Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> .  
  
2. `QueryService` para a <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> partir do <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> passado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> método.  
  
3. Obter <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> do <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> serviço.  
  
4. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> com o primeiro parâmetro definido como `SEID_PropertyBrowserSID` (extraído da <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> Enumeração) e o terceiro parâmetro, `varValue` , representando uma forma de cadeia de caracteres do GUID que representa a janela de **Propriedades** . Faça essa chamada apenas uma vez na primeira criação da janela do documento da janela **Propriedades** . Após a chamada, essa janela de **Propriedades** é associada ao quadro da janela.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>Para obter o objeto de quadro de janela quando você não for o implementador  
  
- Você pode `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> o serviço <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> com o parâmetro `propid` definido como <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
- Você pode obter a janela do documento ativo chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> por meio do serviço SVsMonitorSelection. Defina o parâmetro `elementid` como `SEID_WindowFrame` , extraído da <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> enumeração.  
  
## <a name="see-also"></a>Consulte Também  
 [Estendendo propriedades](../extensibility/internals/extending-properties.md)   
 [Interfaces e campos da janela Propriedades](../extensibility/internals/properties-window-fields-and-interfaces.md)