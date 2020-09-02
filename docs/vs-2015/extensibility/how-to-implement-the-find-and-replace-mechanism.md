---
title: 'Como: implementar o mecanismo de localização e substituição | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4362d0b0c3f013ce6f38d13265dcc181c77012c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62548684"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Como implementar o mecanismo de localizar e substituir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Visual Studio fornece duas maneiras de implementar localizar/substituir. Uma maneira é passar uma imagem de texto para o Shell e permitir que ele lide com a pesquisa, o realce e a substituição de texto. Isso permite que os usuários especifiquem vários intervalos de texto. Como alternativa, seu VSPackage pode controlar essa funcionalidade em si. Em ambos os casos, você deve notificar o Shell sobre o destino atual e os destinos de todos os documentos abertos.  
  
### <a name="to-implement-findreplace"></a>Para implementar localizar/substituir  
  
1. Implemente a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interface em um dos objetos retornados pelas propriedades do quadro <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> ou <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> . Se você estiver criando um editor personalizado, deverá implementar essa interface como parte da classe do editor personalizado.  
  
2. Use o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> método para especificar as opções às quais o editor oferece suporte e para indicar se ele implementa a pesquisa de imagens de texto.  
  
     Se o seu editor oferecer suporte à pesquisa de imagem de texto, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A> .  
  
     Caso contrário, implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> .  
  
3. Se você implementar os <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> métodos e, poderá simplificar suas tarefas de pesquisa chamando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interface.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
