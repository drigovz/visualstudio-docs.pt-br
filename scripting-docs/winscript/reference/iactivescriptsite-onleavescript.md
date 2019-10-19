---
title: 'IActiveScriptSite:: OnLeaveScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9d872948fea14998f9c6f8140467d6e4c83d056
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570323"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informa ao host que o mecanismo de script retornou da execução do código de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se houver êxito.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de script deve chamar esse método antes de retornar o controle a um aplicativo de chamada que inseriu o mecanismo de script. Por exemplo, se o script chama um objeto que dispara um evento manipulado pelo mecanismo de script, o mecanismo de script deve chamar o método [IActiveScriptSite:: OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) antes de executar o evento e deve chamar `IActiveScriptSite::OnLeaveScript` depois de executar o evento antes de retornar ao objeto que disparou o evento. Chamadas para este método podem ser aninhadas. Cada chamada para `IActiveScriptSite::OnEnterScript` requer uma chamada correspondente para esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)