---
title: IDebugApplication::HandleBreakPoint | Microsoft Docs
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
ms.openlocfilehash: 5e3444e6eedde9576216552e41abb0e97aafa2d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412389"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Faz com que o thread atual bloquear e envia uma notificação do ponto de interrupção para o IDE do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `br`  
 [in] O motivo para a interrupção.  
  
 `pbra`  
 [out] Ação a ser tomada quando o depurador retoma o aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um mecanismo de linguagem chama esse método no contexto de um thread que atinge um ponto de interrupção. Esse método bloqueia o thread atual e envia uma notificação de ponto de interrupção para o IDE do depurador. Quando o depurador retoma o aplicativo, o `pbra` parâmetro especifica qual ação será tomada.  
  
> [!NOTE]
> O mecanismo de linguagem pode ser chamado pelo thread de realizar tarefas tais como enumerar a pilha de quadros ou avaliam expressões durante o ponto de interrupção.  
  
 Esse método faz com que `IApplicationDebugger::onHandleBreakPoint` a ser chamado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Enumeração BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [BREAKRESUMEACTION Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)