---
title: 'IDebugModule3:: IsUserCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c8b313ecdbc1168238bad517f34350a420fb30ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929765"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Recupera informações sobre se o módulo representa ou não o código do usuário.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Parâmetros
`pfUser`\
fora Diferente de zero ( `TRUE` ) se o módulo representar o código de usuário, zero ( `FALSE` ) se não tiver.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro.

## <a name="see-also"></a>Confira também
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
