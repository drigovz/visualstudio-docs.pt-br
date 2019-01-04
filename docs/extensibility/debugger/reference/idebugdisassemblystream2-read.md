---
title: IDebugDisassemblyStream2::Read | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ce82bc81ef54cff9dbfb0a6282411e03775ebc9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892008"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Lê a partir da posição atual no fluxo de desmontagem de instruções.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwInstructions`  
 [in] O número de instruções para desmontar. Esse valor também é o comprimento máximo da `prgDisassembly` matriz.  
  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) enumeração que indicam quais campos de `prgDisassembly` devem ser preenchidos.  
  
 `pdwInstructionsRead`  
 [out] Retorna o número de instruções, na verdade, desmontado.  
  
 `prgDisassembly`  
 [out] Uma matriz de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estruturas que será preenchido com o código desmontado, uma estrutura por instrução desmontada. O comprimento dessa matriz é determinado pelo `dwInstructions` parâmetro.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O número máximo de instruções que estão disponíveis no escopo atual pode ser obtido chamando o [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md) método.  
  
 A posição atual em que a próxima instrução é lido do pode ser alterada por meio da chamada a [busca](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) método.  
  
 O `DSF_OPERANDS_SYMBOLS` sinalizador pode ser adicionado para o `DSF_OPERANDS` sinalizador no `dwFields` parâmetro para indicar que os nomes de símbolos devem ser usados quando a desmontagem de instruções.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [Buscar](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)