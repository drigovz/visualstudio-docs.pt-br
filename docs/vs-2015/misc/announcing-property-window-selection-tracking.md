---
title: Anunciando acompanhamento de seleção de janela de propriedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002446"
---
# <a name="announcing-property-window-selection-tracking"></a>Anunciando o acompanhamento da seleção da janela Propriedades
Se você quiser trabalhar com a janela **Propriedades** ou com as **páginas de propriedades,** por exemplo, um formulário, texto ou uma seleção para a qual você deseja ver as propriedades, você deve ter conhecimento completo de como coordenar a seleção. Por exemplo, você deve saber se tem seleção única ou várias seleções. Em seguida, você precisa anunciar seu tipo de seleção (único ou múltiplo) para o IDE usando a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface. Essa interface fornece as informações necessárias para a janela **Propriedades** .  
  
### <a name="to-announce-selection-to-the-environment"></a>Para anunciar a seleção para o ambiente  
  
1. Chamada `QueryInterface` para <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> .  
  
    1. Para fazer isso, use o ponteiro do site passado para a exibição quando ele foi criado.  
  
    2. Chame `QueryService` a partir do modo de exibição para o `SID_STrackSelection` serviço.  
  
         Isso retorna um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Chame o <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> método toda vez que sua seleção for alterada e passe um ponteiro para um objeto que implementa <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
     O objeto contêiner Selection pode usar uma ou várias seleções e contém as informações de seleção em um `IDispatch` objeto. Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> método notifica a janela **Propriedades** de que a seleção foi alterada. A janela **Propriedades** usa os objetos em <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para determinar se ocorreram uma ou várias seleções e quais são as seleções de objeto reais.  
  
     Se você especificar uma seleção múltipla, a janela **Propriedades** localizará a interseção entre as propriedades comuns dos objetos. Se você especificar uma única seleção de objeto, a janela **Propriedades** exibirá todas as propriedades de um objeto.  
  
## <a name="see-also"></a>Consulte Também  
 [Estendendo propriedades](../extensibility/internals/extending-properties.md)   
 [Páginas de propriedade](../extensibility/internals/property-pages.md)