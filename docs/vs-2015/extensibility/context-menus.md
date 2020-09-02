---
title: Menus de contexto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - context menus
ms.assetid: 44fd9e6a-6d42-4aba-80ba-f37fa0070f1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9baab8ef64fa1952eff138165f608e25960c8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184271"
---
# <a name="context-menus"></a>Menus de contexto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os menus de contexto são exibidos quando um usuário clica com o botão direito do mouse em uma região ativa da área do cliente e limpa quando o botão direito do mouse é liberado.  
  
## <a name="editor-context-menus"></a>Menus de Contexto do Editor  
 Ao interceptar `ECMD_SHOWCONTEXTMENU` , o serviço de linguagem pode controlar os menus de contexto que serão exibidos no editor. Para exibir seu próprio menu de contexto, manipule esse comando quando ele for passado para seu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A> . Se você não tratar esse comando, o IDE exibirá um menu de contexto padrão fornecido para o editor. Você também pode controlar o conteúdo do menu de contexto por marcador. Para obter mais informações sobre isso, consulte [usando marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md) e [interceptando comandos de serviço de idioma herdado](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Desenvolvendo um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Estendendo comandos e menus](../extensibility/extending-menus-and-commands.md)
