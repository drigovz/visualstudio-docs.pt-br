---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fad5f1936312b91c69377064b17f844ba254f81a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009720"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Obtém uma representação depende do computador do intervalo de endereços físicos associados a um quadro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```csharp  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `paddrMin`  
 [out] Retorna o endereço físico mais baixo associado deste quadro de pilhas.  
  
 `paddrMax`  
 [out] Retorna o endereço físico mais alto associado deste quadro de pilhas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As informações retornadas por esse método são usadas pelo Gerenciador de depuração de sessão (SDM) para classificar os registros de ativação.  
  
 Supõe-se que a pilha de chamadas cresce para baixo, ou seja, para que novos registros de ativação são adicionados a cada vez mais inferiores endereços de memória. Uma arquitetura de tempo de execução deve fornecer os intervalos de pilha física que correspondem a essa suposição.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)