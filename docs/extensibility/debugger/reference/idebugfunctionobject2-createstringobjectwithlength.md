---
title: IDebugFunctionObject2:CreateStringObjectWithLength | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 937d325f8637a3260121def189d472dcfb3e1309
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728472"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Cria um objeto de string que tem o comprimento especificado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>parâmetros
`pcstrString`\
[em] O valor da seqüência para o objeto de seqüência.

`uiLength`\
[em] O comprimento da corda em bytes.

`ppObject`\
[fora] Retorna um objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa o objeto de seqüência recém-criado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
