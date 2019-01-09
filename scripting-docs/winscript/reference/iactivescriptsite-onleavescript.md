---
title: IActiveScriptSite::OnLeaveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 7d08d58fc788d2d10ed044808ca40a5f4ea929c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093152"
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informa ao host que o mecanismo de script retornou de executar o código de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se houver êxito.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de script deve chamar esse método antes de devolver o controle para um aplicativo de chamada que inseriu o mecanismo de script. Por exemplo, se o script chama um objeto que, em seguida, aciona um evento como manipulado pelo mecanismo de script, o mecanismo de script deve chamar o [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) método antes de executar o evento e deve chamar `IActiveScriptSite::OnLeaveScript`depois de executar o evento antes de retornar para o objeto que disparou o evento. Chamadas para esse método podem ser aninhadas. Todas as chamadas para `IActiveScriptSite::OnEnterScript` requer uma chamada correspondente para esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)