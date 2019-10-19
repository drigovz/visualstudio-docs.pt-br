---
title: 'IActiveScriptSiteDebug:: OnScriptErrorDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 894767b3dae9db54e8bc438a82b27195308a4342
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572211"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Permite que um host inteligente determine como lidar com erros de tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pErrorDebug`  
 no O erro de tempo de execução que ocorreu  
  
 `pfEnterDebugger`  
 fora Sinalizador que indica se o erro deve ser passado para o depurador para fazer a depuração JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 fora Sinalizador que indica se deve chamar `IActiveScriptSite::OnScriptError` quando o usuário decide continuar sem depuração.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os valores possíveis incluem, mas não se limitam ao valor na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um host inteligente pode usar esse método para determinar como lidar com erros de tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteDebug Interface](../../winscript/reference/iactivescriptsitedebug-interface.md)