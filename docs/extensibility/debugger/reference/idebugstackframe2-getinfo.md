---
title: 'IDebugStackFrame2:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 161796827507cf40f7ac7124ae3376d4252fb3d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837522"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Obtém uma descrição do quadro de pilhas.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetInfo ( 
   FRAMEINFO_FLAGS dwFieldSpec,
   UINT            nRadix,
   FRAMEINFO*      pFrameInfo
);
```

```csharp
int GetInfo ( 
   enum_FRAMEINFO_FLAGS dwFieldSpec,
   uint                 nRadix,
   FRAMEINFO[]          pFrameInfo
);
```

## <a name="parameters"></a>Parâmetros
`dwFieldSpec`\
no Uma combinação de sinalizadores da enumeração [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) que especifica quais campos do `pFrameInfo` parâmetro devem ser preenchidos.

`nRadix`\
no A base a ser usada na formatação de qualquer informação numérica.

`pFrameInfo`\
fora Uma estrutura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que é preenchida com a descrição do quadro de pilhas.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
