---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs
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
ms.openlocfilehash: 50e8c7baa42d6f2f36dc71b768797dfe2a464bf3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160099"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Permite que um host inteligente determinar como tratar erros de tempo de execução.  
  
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
 [in] O erro de tempo de execução que ocorreu  
  
 `pfEnterDebugger`  
 [out] Sinalizador que indica se deve passar o erro para o depurador para fazer a depuração JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Sinalizador que indica se a chamada `IActiveScriptSite::OnScriptError` quando o usuário decidir continuar sem depurar.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os valores possíveis incluem, mas não estão limitados ao valor na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um host inteligente pode usar esse método para determinar como tratar erros de tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteDebug Interface](../../winscript/reference/iactivescriptsitedebug-interface.md)