---
title: IActiveScriptSiteWindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3691a874121c00dcccc69958eb5746a2c1d78122
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149452"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Essa interface é implementada por hosts que dão suporte a uma interface do usuário no mesmo objeto como [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Hosts que não dão suporte a uma interface do usuário, como servidores, não implementaria o `IActiveScriptSiteWindow` interface. O mecanismo de script acessa essa interface chamando `QueryInterface` de `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Recupera o identificador de janela que pode atuar como o proprietário de uma janela pop-up que o mecanismo de script deve exibir.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Faz com que o host habilitar ou desabilitar a janela principal, bem como todas as caixas de diálogo sem janela restrita.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de script ativo](../../winscript/reference/active-script-interfaces.md)