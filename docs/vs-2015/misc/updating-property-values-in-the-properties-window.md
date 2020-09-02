---
title: Atualizando valores de propriedade na janela Propriedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 18ecf0a21c5b2d73bdf8e439d25765b6b275cbd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434183"
---
# <a name="updating-property-values-in-the-properties-window"></a>Atualizando valores de propriedade na janela Propriedades
Há duas maneiras de manter a janela **Propriedades** em sincronia com as alterações no valor da propriedade. A primeira é chamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface, que fornece acesso à funcionalidade básica de janelas, incluindo acesso e criação de ferramentas e janelas de documentos fornecidas pelo ambiente. As etapas a seguir descrevem esse processo de sincronização.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Atualizando valores de propriedade usando IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Para atualizar valores de propriedade usando a interface IVsUIShell  
  
1. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (por meio do <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> serviço) sempre que VSPackages, projetos ou editores precisarem criar ou enumerar janelas de ferramentas ou documentos.  
  
2. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> para manter a janela **Propriedades** em sincronia com as alterações de propriedade de um projeto (ou qualquer outro objeto selecionado que esteja sendo navegado pela janela **Propriedades** ) sem implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e acionar <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> eventos.  
  
3. Implemente os <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> estabeleça e desabilite, respectivamente, a notificação do cliente de eventos de hierarquia sem exigir que a hierarquia seja implementada <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
## <a name="updating-property-values-using-iconnection"></a>Atualizando valores de propriedade usando IConnection  
 A segunda maneira de manter a janela **Propriedades** em sincronia com as alterações no valor da propriedade é implementar `IConnection` no objeto connectável para indicar a existência das interfaces de saída. Se você quiser localizar o nome da propriedade, derive o objeto de <xref:System.ComponentModel.ICustomTypeDescriptor> . A <xref:System.ComponentModel.ICustomTypeDescriptor> implementação pode modificar os descritores de propriedade que ele retorna e alterar o nome de uma propriedade. Para localizar a descrição, crie um atributo que deriva de <xref:System.ComponentModel.DescriptionAttribute> e substitua a propriedade Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considerações sobre a implementação da interface IConnection  
  
1. `IConnection` fornece acesso a um subobjeto enumerador com a <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. Ele também fornece acesso a todos os subobjetos de ponto de conexão, cada um implementando a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface.  
  
2. Qualquer objeto de procura é responsável pela implementação de um <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> evento. A janela **Propriedades** aconselhará o conjunto de eventos por meio de `IConnection` .  
  
3. Um ponto de conexão controla quantas conexões (um ou mais) ela permite em sua implementação de <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> . Um ponto de conexão que permite que apenas uma interface possa retornar <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> do <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> método.  
  
4. Um cliente pode chamar a `IConnection` interface para obter acesso a um subobjeto do enumerador com a <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface. A <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interface pode então ser chamada para enumerar pontos de conexão para cada ID de interface de saída (IID).  
  
5. `IConnection` também pode ser chamado para obter acesso a subobjetos de ponto de conexão com a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface para cada IID de saída. Por meio da <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface, um cliente inicia ou termina um loop de consultoria com o objeto que pôde ser conectado e a própria sincronização do cliente. O cliente também pode chamar a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface para obter um objeto de enumerador com a <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interface para enumerar as conexões que ele conhece.  
  
## <a name="see-also"></a>Consulte Também  
 [Anunciando rastreamento de seleção de janela de propriedade](../misc/announcing-property-window-selection-tracking.md)   
 [Estendendo propriedades](../extensibility/internals/extending-properties.md)