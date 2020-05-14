---
title: IDebugProcessEx2::Anexar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d70da2530a1677367a22968436a17eba809fd24a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723389"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Este método informa ao processo que uma sessão está depurando o processo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Attach( 
   IDebugSession2* pSession
);
```

```csharp
int Attach(
   IDebugSession2 pSession
);
```

## <a name="parameters"></a>parâmetros
`pSession`\
[em] Um valor que identifica exclusivamente a sessão anexada a esse processo.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A interface `pSession` passada deve ser tratada apenas como um cookie, um valor que identifica exclusivamente o gerenciador de depuração de sessão anexado a esse processo; nenhum dos métodos na interface fornecida é funcional.

## <a name="see-also"></a>Confira também
- [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)
