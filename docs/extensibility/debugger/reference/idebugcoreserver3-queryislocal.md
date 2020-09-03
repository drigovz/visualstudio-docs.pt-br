---
title: 'IDebugCoreServer3:: QueryIsLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e06cae53251be02ee63650ce7723e5915565be4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732826"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
Determina se o servidor é local para o chamador.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Valor retornado
 Retorna `S_OK` para indicar que o servidor é local. Retorna `S_FALSE` se o servidor está sendo executado a partir de uma instância do msvsmon.exe, que normalmente é usado para depuração remota.

## <a name="see-also"></a>Confira também
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
