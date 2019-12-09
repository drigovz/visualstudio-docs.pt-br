---
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fad77ca1d649e7ffdda02c7145dc11666619f232
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320314"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Recupera uma lista dos quadros de pilhas para este thread.

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
[in] Uma combinação de sinalizadores do [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) enumeração que especifica quais campos da [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estruturas devem ser preenchidos. Especifique o `FIF_FUNCNAME_FORMAT` sinalizador para formatar o nome da função em uma única cadeia de caracteres.

`nRadix`\
[in] Base usada na formatação informações numéricas no enumerador.

`ppEnum`\
[out] Retorna um [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) objeto que contém uma lista de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estruturas que descrevem o quadro de pilhas.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Os quadros do thread são enumerados na ordem, com o quadro atual enumeradas primeiro e o quadro mais antigo enumerados pela última vez.

## <a name="see-also"></a>Consulte também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)