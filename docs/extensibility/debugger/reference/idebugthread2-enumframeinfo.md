---
title: 'IDebugThread2:: EnumFrameInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a254de60995eb5e7902eda80cf50c4af227a756f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940274"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Recupera uma lista de quadros de pilha para este thread.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`dwFieldSpec`\
no Uma combinação de sinalizadores da enumeração [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) que especifica quais campos das estruturas [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) devem ser preenchidos. Especifique o `FIF_FUNCNAME_FORMAT` sinalizador para formatar o nome da função em uma única cadeia de caracteres.

`nRadix`\
no Base usada na formatação de informações numéricas no enumerador.

`ppEnum`\
fora Retorna um objeto [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) que contém uma lista de estruturas [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) que descrevem o quadro de pilhas.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Os quadros do thread são enumerados em ordem, com o quadro atual enumerado primeiro e o quadro mais antigo enumerado por último.

## <a name="see-also"></a>Confira também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
