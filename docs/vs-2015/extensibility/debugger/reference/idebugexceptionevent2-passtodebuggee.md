---
title: IDebugExceptionEvent2::P assToDebuggee | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecc7eb3830522cdee0022f4193482daab3780230
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150404"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica se a exceção deve ser passada para o programa que está sendo depurado quando a execução é retomada ou se a exceção deve ser descartada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT PassToDebuggee(  
   BOOL fPass  
);  
```  
  
```csharp  
int PassToDebuggee(  
   int fPass  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fPass`  
 no Zero ( `TRUE` ) se a exceção deve ser passada para o programa que está sendo depurado quando a execução é retomada, ou zero ( `FALSE` ) se a exceção deve ser descartada.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chamar esse método, na verdade, não faz com que qualquer código seja executado no programa que está sendo depurado. A chamada é simplesmente definir o estado para a próxima execução de código. Por exemplo, as chamadas para o método [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) podem retornar `S_OK` com o [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` conjunto de campos como `EXCEPTION_STOP_SECOND_CHANCE` .  
  
 O IDE pode receber o evento [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) e chamar o método [continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) . O mecanismo de depuração (DE) deve ter um comportamento padrão para manipular o caso se o `PassToDebuggee` método não for chamado.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)   
 [Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
