---
title: IDebugProperty2::GetReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4f119a00139e2af44f771fa0903c73b8003dd77f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721363"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
Retorna uma referência ao valor da propriedade.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

## <a name="parameters"></a>parâmetros
`ppRererence`\
[fora] Retorna um objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) representando uma referência ao valor da propriedade.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código `E_NOTIMPL` `E_GETREFERENCE_NO_REFERENCE`de erro, tipicamente ou .

## <a name="see-also"></a>Confira também
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
