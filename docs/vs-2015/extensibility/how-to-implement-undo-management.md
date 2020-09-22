---
title: 'Como: implementar o gerenciamento de desfazer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838700"
---
# <a name="how-to-implement-undo-management"></a>Como implementar o gerenciamento de desfazer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A interface primária usada para o gerenciamento de desfazer é <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> , que é implementada pelo ambiente. Para oferecer suporte ao gerenciamento de desfazer, implemente unidades de desfazer separadas (ou seja, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> , que podem conter várias etapas individuais.  
  
 A maneira como você implementa o gerenciamento de desfazer varia dependendo se o seu editor dá suporte a várias exibições ou não. Os procedimentos para cada implementação são detalhados nas seções a seguir.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Casos em que um editor dá suporte a uma única exibição  
 Nesse cenário, o editor não oferece suporte a várias exibições. Há apenas um editor e um documento, e eles dão suporte a desfazer. Use o procedimento a seguir para implementar o gerenciamento de desfazer.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Para dar suporte ao gerenciamento de desfazer para um editor de exibição única  
  
1. Chame `QueryInterface` na `IServiceProvider` interface no quadro de janela para `IOleUndoManager` , do objeto de exibição de documento para acessar o Gerenciador de desfazer ( `IID_IOLEUndoManager` ).  
  
2. Quando uma exibição é inserida em um quadro de janela, ela obtém um ponteiro de site, que pode ser usado para chamar `QueryInterface` `IServiceProvider` .  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Casos em que um editor dá suporte a várias exibições  
 Se você tiver separação de documento e exibição, normalmente haverá um Gerenciador de desfazer associado ao documento em si. Todas as unidades de desfazer são colocadas em um Gerenciador de desfazer associado ao objeto de dados do documento.  
  
 Em vez da consulta de exibição para o Gerenciador de desfazer, do qual há um para cada exibição, o objeto de dados de documento chama <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> para instanciar o Gerenciador de desfazer, especificando um identificador de classe de CLSID_OLEUndoManager. O identificador de classe é definido no arquivo OCUNDOID. h.  
  
 Ao usar o <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> para criar sua própria instância de desfazer Gerenciador, use o procedimento a seguir para conectar o Gerenciador de desfazer ao ambiente.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Para conectar o Gerenciador de desfazer ao ambiente  
  
1. Chamada `QueryInterface` no objeto retornado de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> para `IID_IOleUndoManager` . Armazene o ponteiro em <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> .  
  
2. Ligue `QueryInterface` `IOleUndoManager` para o para `IID_IOleCommandTarget` . Armazene o ponteiro em <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
3. Retransmita seu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> chame para a interface armazenada `IOleCommandTarget` para os seguintes comandos StandardCommandSet97:  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. Ligue `QueryInterface` `IOleUndoManager` para o para `IID_IVsChangeTrackingUndoManager` . Armazene o ponteiro em <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> .  
  
    Use o ponteiro para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> para chamar os <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> métodos, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5. Ligue `QueryInterface` `IOleUndoManager` para o para `IID_IVsLinkCapableUndoManager` .  
  
6. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> com seu documento, que também deve implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interface. Quando o documento for fechado, chame `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` .  
  
7. Quando o documento for fechado, chame `QueryInterface` no Gerenciador de desfazer para `IID_IVsLifetimeControlledObject` .  
  
8. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Quando forem feitas alterações no documento, chame <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> no Gerenciador com uma `OleUndoUnit` classe. O <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> método mantém uma referência ao objeto, portanto, em geral, você o libera logo após o <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> .  
  
   A `OleUndoManager` classe representa uma única instância de desfazer pilha. Portanto, há um objeto do Gerenciador de desfazer por entidade de dados que está sendo rastreado para desfazer ou refazer.  
  
> [!NOTE]
> Embora o objeto do Gerenciador de desfazer seja usado extensivamente pelo editor de texto, ele é um componente geral que não tem suporte específico para o editor de texto. Se você quiser dar suporte a desfazer ou refazer vários níveis, poderá usar esse objeto para fazer isso.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Como limpar a pilha de desfazer](../extensibility/how-to-clear-the-undo-stack.md)
