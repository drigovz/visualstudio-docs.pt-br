---
title: IDebugProgram2::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19cb88a24a616a2a39bdcd7f292108493859a8b7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919038"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continua a execução deste programa de um estado parado. Qualquer estado de execução anterior (por exemplo, uma etapa) estiver desmarcado, e o programa inicia a execução novamente.  
  
> [!NOTE]
>  Este método foi preterido. Use o [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Quando o usuário inicia a execução de um estado parado no thread do algum outro programa, este método é chamado neste programa. Esse método também é chamado quando o usuário seleciona o **inicie** comando da **depurar** menu no IDE. A implementação desse método pode ser tão simple quanto chamar o [retomar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método no thread atual no programa.  
  
> [!WARNING]
>  Não enviar um evento de interrupção ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao manipular essa chamada; caso contrário, o depurador poderá parar de responder.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)