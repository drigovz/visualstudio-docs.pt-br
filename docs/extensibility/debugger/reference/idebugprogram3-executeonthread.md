---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cbb2650fc2c001e57de7b1820cff238c8963e8cc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889430"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Executa o programa do depurador. O thread é retornado para fornecer as informações do depurador em qual thread o usuário está exibindo ao executar o programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 [in] Uma [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Há três maneiras diferentes que um depurador pode retomar a execução após a interrupção:  
  
- Execute: Cancele qualquer etapa anterior e seja executada até que o próximo ponto de interrupção e assim por diante.  
  
- Etapa: Cancelar qualquer etapa antiga e executar até que a nova etapa seja concluída.  
  
- Continue: Execute novamente e deixar qualquer etapa antiga ativa.  
  
  O thread é passado para `ExecuteOnThread` é útil ao decidir qual etapa para cancelar. Se você não souber o thread em execução executar cancela todas as etapas. Com conhecimento do thread, você só precisará cancelar a etapa no thread ativo.  
  
## <a name="see-also"></a>Consulte também  
 [Executar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)