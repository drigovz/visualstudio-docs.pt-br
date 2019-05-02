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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924686"
---
# <a name="context-menus"></a>Menus de contexto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Menus de contexto são exibidos quando um usuário clica com o botão direito em uma região ativa da área de cliente e limpar quando o botão direito do mouse é liberado.  
  
## <a name="editor-context-menus"></a>Menus de Contexto do Editor  
 Interceptando `ECMD_SHOWCONTEXTMENU`, seu serviço de linguagem pode controlar os menus de contexto serão exibido no editor. Para exibir seu próprio menu de contexto, lidar com esse comando quando ele é passado para seus <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowContextMenu%2A>. Se você não tratar esse comando, o IDE exibirá um menu de contexto padrão fornecido para o editor. Você também pode controlar o conteúdo do menu de contexto em uma base por marcador. Para obter mais informações sobre isso, consulte [usando os marcadores de texto com a API herdada](../extensibility/using-text-markers-with-the-legacy-api.md) e [interceptar comandos de serviço de linguagem herdado](../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver um serviço de linguagem herdado](../extensibility/internals/developing-a-legacy-language-service.md)   
 [Ampliar menus e comandos](../extensibility/extending-menus-and-commands.md)
