---
title: IDebugDisassemblyStream2::Leia | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a4f5c0250405c2e2a0314b52c4cbc64d749fc0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732101"
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
Leia as instruções a partir da posição atual no fluxo de desmontagem.

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

## <a name="parameters"></a>parâmetros
`dwInstructions`\
[em] O número de instruções para desmontar. Este valor também é o `prgDisassembly` comprimento máximo da matriz.

`dwFields`\
[em] Uma combinação de [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) bandeiras da enumeração `prgDisassembly` DISASSEMBLY_STREAM_FIELDS que indicam quais campos devem ser preenchidos.

`pdwInstructionsRead`\
[fora] Retorna o número de instruções realmente desmontadas.

`prgDisassembly`\
[fora] Uma matriz de estruturas de [DesmontagemData](../../../extensibility/debugger/reference/disassemblydata.md) que é preenchida com o código desmontado, uma estrutura por instrução desmontada. O comprimento desta matriz é `dwInstructions` ditado pelo parâmetro.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O número máximo de instruções disponíveis no escopo atual pode ser obtido ligando para o método [GetSize.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)

 A posição atual de onde a próxima instrução é lida pode ser alterada chamando o método [Buscar.](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)

 A `DSF_OPERANDS_SYMBOLS` bandeira pode ser `DSF_OPERANDS` adicionada `dwFields` à bandeira no parâmetro para indicar que os nomes dos símbolos devem ser usados ao desmontar as instruções.

## <a name="see-also"></a>Confira também
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
