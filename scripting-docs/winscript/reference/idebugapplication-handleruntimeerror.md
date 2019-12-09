---
title: 'IDebugApplication:: HandleRuntimeError | Microsoft Docs'
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
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574325"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Faz com que o thread atual bloqueie e envie uma notificação do erro para o IDE do depurador.  
  
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
 no O erro que ocorreu.  
  
 `pScriptSite`  
 no O site de script do thread.  
  
 `pbra`  
 fora Ação a ser tomada quando o depurador retomar o aplicativo.  
  
 `perra`  
 fora Ação a ser tomada quando o depurador retomar o aplicativo se houver um erro.  
  
 `pfCallOnScriptError`  
 fora Sinalizador que é `TRUE` se o mecanismo deve chamar o método `IActiveScriptSite::OnScriptError`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um mecanismo de linguagem chama esse método no contexto de um thread que causa um erro em tempo de execução. Esse método faz com que o thread atual bloqueie e envie uma notificação de erro a ser enviada para o IDE do depurador. Quando o IDE do depurador retoma o aplicativo, esse método retorna com a ação a ser executada.  
  
> [!NOTE]
> Durante a falha de tempo de execução, o mecanismo de linguagem pode ser chamado pelo thread para realizar tarefas como enumerar quadros de pilha ou avaliar expressões.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 @No__t_1 de [interface IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)  
 @No__t_1 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)  
 @No__t_1 de [Enumeração BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)  
 [ERRORRESUMEACTION Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)