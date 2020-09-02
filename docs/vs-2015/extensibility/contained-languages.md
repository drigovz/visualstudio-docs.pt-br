---
title: Idiomas contidos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184283"
---
# <a name="contained-languages"></a>Linguagens contidas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

Os *idiomas contidos* são idiomas contidos em outras linguagens. Por exemplo, HTML em [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] páginas pode conter [!INCLUDE[csprcs](../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] scripts ou. Uma arquitetura de linguagem dupla é necessária para o editor de arquivo. aspx fornecer IntelliSense, colorização e outros recursos de edição para o HTML e a linguagem de script.  
  
## <a name="implementation"></a>Implementação  
 A interface mais importante que você precisa implementar para idiomas contidos é a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Essa interface é implementada por qualquer linguagem que possa ser hospedada dentro de um idioma primário. Ele dá acesso ao Colorizer do serviço de linguagem, ao filtro de exibição de texto e à ID do serviço de idioma principal. O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> permite que você crie uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. As etapas a seguir mostram como implementar um idioma contido:  
  
1. Use `QueryService()` para obter a ID do serviço de idioma e a ID de interface do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> .  
  
2. Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> método para criar uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interface. Passe uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface, uma ou mais [IDs de item](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) e uma <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface.  
  
3. A <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interface, que é o objeto coordenador de buffer de texto, fornece os serviços básicos que são necessários para mapear locais em um arquivo primário para o buffer do idioma secundário.  
  
     Por exemplo, em um único arquivo. aspx, o arquivo primário inclui o ASP, HTML e todo o código contido. No entanto, o buffer secundário inclui apenas o código contido, junto com as definições de classe, para tornar o buffer secundário um arquivo de código válido. O coordenador de buffer lida com o trabalho de coordenar edições de um buffer para o outro.  
  
4. O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> método, que é o idioma principal, informa ao coordenador de buffer qual texto em seu buffer é mapeado para o texto correspondente no buffer secundário.  
  
     O idioma passa em uma matriz da <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> estrutura, que atualmente inclui apenas um Span primário e um secundário.  
  
5. O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> método e o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> método fornecem o mapeamento do buffer primário para o secundário e vice-versa.
