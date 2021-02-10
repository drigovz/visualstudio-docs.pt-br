---
title: IDebugProcessEx2::D Etach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62ca404442d6bf6080972f03c3e2fd0da2621e20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954885"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Esse método informa ao processo que uma sessão não está mais Depurando o processo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Detach( 
   IDebugSession2* pSession
);
```

```csharp
int Detach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>Parâmetros
`pSession`\
no Um valor que identifica exclusivamente a sessão da qual desanexar esse processo.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A interface passada deve `pSession` ser tratada apenas como um cookie, um valor que identifica exclusivamente o Gerenciador de depuração de sessão que foi anexado originalmente a esse processo; nenhum dos métodos na interface fornecida é funcional.

## <a name="see-also"></a>Confira também
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
