---
title: IDebugApplication::HandleRuntimeError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2c9a8b15b5095ac346ba047d6668aada7647a31
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412434"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Faz com que o thread atual bloquear e envia uma notificação de erro para o IDE do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pErrorDebug`  
 [in] O erro que ocorreu.  
  
 `pScriptSite`  
 [in] O site de script do thread.  
  
 `pbra`  
 [out] Ação a ser tomada quando o depurador retoma o aplicativo.  
  
 `perra`  
 [out] Ação a ser tomada quando o depurador retoma o aplicativo se houver um erro.  
  
 `pfCallOnScriptError`  
 [out] Sinalizador que é `TRUE` se o mecanismo deve chamar o `IActiveScriptSite::OnScriptError` método.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um mecanismo de linguagem chama esse método no contexto de um thread que causa um erro de tempo de execução. Esse método faz com que o thread atual bloquear e envia uma notificação de erro a ser enviada para o IDE do depurador. Quando o IDE do depurador retoma o aplicativo, esse método retorna com a ação a ser executada.  
  
> [!NOTE]
> Enquanto estiver na falha de tempo de execução, o mecanismo de linguagem pode ser chamado pelo thread para executar tarefas, como enumerar os quadros de pilha ou avaliar expressões.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interface IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Enumeração BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)