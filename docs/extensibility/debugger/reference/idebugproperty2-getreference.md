---
title: 'IDebugProperty2:: getReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 270a8cc755318578f680e4266ca01e35dee20bb9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850888"
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

## <a name="parameters"></a>Parâmetros
`ppRererence`\
fora Retorna um objeto [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) que representa uma referência ao valor da propriedade.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro, normalmente `E_NOTIMPL` ou `E_GETREFERENCE_NO_REFERENCE` .

## <a name="see-also"></a>Consulte também
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
