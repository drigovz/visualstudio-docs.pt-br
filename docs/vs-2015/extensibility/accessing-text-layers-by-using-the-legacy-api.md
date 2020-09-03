---
title: Acessando camadas de texto usando a API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148020"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>Acessar as camadas de texto usando a API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma camada de texto normalmente encapsula algum aspecto do layout de texto. Por exemplo, uma camada de "função em tempo" oculta o texto antes e depois de uma função que contém o cursor (ponto de inserção de texto).  
  
 Uma camada de texto reside entre um buffer e uma exibição e modifica a maneira como a exibição vê o conteúdo do buffer.  
  
## <a name="text-layer-information"></a>Informações da camada de texto  
 A lista a seguir descreve como as camadas de texto funcionam em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :  
  
- O texto em uma camada de texto pode ser adornado com cores de sintaxe e marcadores.  
  
- No momento, você não pode implementar suas próprias camadas.  
  
- Uma camada expõe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , que é derivada de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . O buffer de texto em si também é implementado como uma camada, o que permite que uma exibição lide com as camadas subjacentes do polimorficamente.  
  
- Qualquer número de camadas pode estar entre a exibição e o buffer. Cada camada lida apenas com a camada abaixo dela, e a exibição lida amplamente com a camada superior. (A exibição tem algumas informações sobre o buffer.)  
  
- Uma camada pode afetar apenas as camadas que estão abaixo dela. Ele não pode afetar as camadas acima dela além dos eventos padrão de origem.  
  
- No editor, o texto oculto, o texto sintético e o encapsulamento de palavras são implementados como camadas. Você pode implementar texto oculto e sintético sem interagir diretamente com as camadas. Para obter mais informações, consulte [estrutura de tópicos em um serviço de idioma herdado](../extensibility/internals/outlining-in-a-legacy-language-service.md) e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession> .  
  
- Cada camada de texto tem seu próprio sistema de coordenadas local exposto por meio da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> interface. A camada de quebra de linha, por exemplo, pode conter duas linhas, enquanto o buffer de texto subjacente pode conter apenas uma linha.  
  
- A exibição se comunica com camadas por meio da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> interface. Use essa interface para reconciliar as coordenadas de exibição com as coordenadas de buffer.  
  
- Qualquer camada como a camada de texto sintética que origina o texto deve fornecer uma implementação local do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A> .  
  
- Além disso <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> , uma camada de texto deve implementar <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e acionar os eventos na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> interface.  
  
## <a name="see-also"></a>Consulte Também  
 [Cores de sintaxe em editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Usando marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalizar menus e controles do editor usando a API herdada](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
