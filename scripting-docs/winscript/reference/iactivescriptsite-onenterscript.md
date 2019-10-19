---
title: 'IActiveScriptSite:: OnEnterScript | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e4f221014d90478bbbc7bb5771276706c764c0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570368"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informa ao host que o mecanismo de script começou a executar o código de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Valor retornado  
 Retorna `S_OK` se houver êxito.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de script deve chamar esse método em cada entrada ou reentrada no mecanismo de script. Por exemplo, se o script chama um objeto que dispara um evento manipulado pelo mecanismo de script, o mecanismo de script deve chamar `IActiveScriptSite::OnEnterScript` antes de executar o evento e deve chamar o método [IActiveScriptSite:: OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) depois de executar o evento Mas antes de retornar ao objeto que disparou o evento. Chamadas para este método podem ser aninhadas. Cada chamada para esse método requer uma chamada correspondente para `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)