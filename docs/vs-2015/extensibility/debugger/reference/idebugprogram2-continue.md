---
title: 'IDebugProgram2:: Continue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 461aa702350e1385e01df6f78e942bbe73b16402
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386193"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Continua executando este programa a partir de um estado parado. Qualquer estado de execução anterior (como uma etapa) é preservado e o programa começa a ser executado novamente.  
  
> [!NOTE]
> Esse método é preterido. Em vez disso, use o método [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 no Um objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o thread.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado nesse programa independentemente de quantos programas estão sendo depurados ou qual programa gerou o evento de interrupção. A implementação deve manter o estado de execução anterior (como uma etapa) e continuar a execução como se nunca tivesse sido interrompida antes de concluir sua execução anterior. Ou seja, se um thread neste programa estivesse realizando uma operação de depuração completa e foi interrompido porque algum outro programa foi interrompido e, em seguida, esse método foi chamado, o programa deve concluir a operação de etapa em etapas original.  
  
> [!WARNING]
> Não enviar um evento de interrupção ou um evento imediato (síncrono) para [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao lidar com essa chamada; caso contrário, o depurador pode parar de responder.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
