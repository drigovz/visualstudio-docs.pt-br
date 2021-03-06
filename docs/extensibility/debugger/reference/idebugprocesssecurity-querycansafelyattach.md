---
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa3f2c02610b5fbe99335ccea6d7c566a0fe58df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931455"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Esse método permite que o fornecedor da porta exiba um aviso antes que o usuário se conecte a um processo não seguro.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Valor retornado
 Os valores de retorno são os seguintes:

- `S_OK`: A anexação ao processo é segura e nenhuma caixa de diálogo de aviso é mostrada.

- `S_FALSE`: A anexação pode ser um problema de segurança e uma caixa de diálogo com um aviso é mostrada.

- `FAILURE`: A anexação ao processo falha.

## <a name="see-also"></a>Confira também
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
