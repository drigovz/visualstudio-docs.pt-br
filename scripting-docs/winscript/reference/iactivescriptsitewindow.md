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
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575904"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Essa interface é implementada por hosts que dão suporte a uma interface do usuário no mesmo objeto que [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Os hosts que não dão suporte a uma interface do usuário, como servidores, não implementarão a interface `IActiveScriptSiteWindow`. O mecanismo de script acessa essa interface chamando `QueryInterface` de `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Recupera o identificador de janela que pode atuar como o proprietário de uma janela pop-up que o mecanismo de script deve exibir.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Faz com que o host habilite ou desabilite sua janela principal, bem como qualquer caixa de diálogo sem janela restrita.|  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de script ativo](../../winscript/reference/active-script-interfaces.md)