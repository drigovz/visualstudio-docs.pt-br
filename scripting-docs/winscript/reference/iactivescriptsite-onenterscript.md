---
title: IActiveScriptSite::OnEnterScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ccef1b2bf63c4421843d3a33cab2e4f471a48251
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094062"
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informa ao host que o mecanismo de script foi iniciado executando o código de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK` se houver êxito.  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de script deve chamar esse método em cada entrada ou reentrada no mecanismo de script. Por exemplo, se o script chama um objeto que, em seguida, aciona um evento como manipulado pelo mecanismo de script, o mecanismo de script deve chamar `IActiveScriptSite::OnEnterScript` antes de executar o evento e deve chamar o [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) método depois de executar o evento, mas antes de retornar para o objeto que disparou o evento. Chamadas para esse método podem ser aninhadas. Todas as chamadas para esse método requer uma chamada correspondente para `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)