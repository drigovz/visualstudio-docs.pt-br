---
title: 'IDebugApplication:: HandleBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574959"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Faz com que o thread atual bloqueie e envie uma notificação do ponto de interrupção para o IDE do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `br`  
 no O motivo da interrupção.  
  
 `pbra`  
 fora Ação a ser tomada quando o depurador retomar o aplicativo.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um mecanismo de linguagem chama esse método no contexto de um thread que atinge um ponto de interrupção. Esse método bloqueia o thread atual e envia uma notificação de ponto de interrupção para o IDE do depurador. Quando o depurador retoma o aplicativo, o parâmetro `pbra` especifica a ação a ser tomada.  
  
> [!NOTE]
> O mecanismo de linguagem pode ser chamado pelo thread para realizar tarefas como enumerar quadros de pilha ou avaliar expressões durante o ponto de interrupção.  
  
 Esse método faz com que `IApplicationDebugger::onHandleBreakPoint` seja chamado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger:: onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)    
 @No__t_1 de [Enumeração BREAKREASON](../../winscript/reference/breakreason-enumeration.md)  
 [BREAKRESUMEACTION Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)