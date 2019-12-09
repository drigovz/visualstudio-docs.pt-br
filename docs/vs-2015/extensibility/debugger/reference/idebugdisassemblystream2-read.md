---
title: IDebugDisassemblyStream2::Read | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 520c801a0603f2c6d3228ae95ad144827eac0088
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203000"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Lê a partir da posição atual no fluxo de desmontagem de instruções.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
