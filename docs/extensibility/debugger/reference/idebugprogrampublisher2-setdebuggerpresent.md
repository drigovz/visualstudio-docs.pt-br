---
title: IDebugProgramPublisher2::SetDebuggerPresente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b551c644346b66d907fa4f75b11b24c8b9538e27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721607"
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
Diz ao editor do programa que um depurador está presente e em execução.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetDebuggerPresent(
   BOOL fDebuggerPresent
);
```

```csharp
int SetDebuggerPresent(
   int fDebuggerPresent
);
```

## <a name="parameters"></a>parâmetros
`fDebuggerPresent`\
[em] Não-zero`TRUE`( ) se um depurador`FALSE`estiver presente, zero ( ) se não estiver.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A presença ou ausência de um depurador é refletida nos dados retornados do método [GetProviderProcessData:](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) o `SetDebuggerPresent` valor devolvido lá é definido ou compensado por uma chamada anterior ao método.

## <a name="see-also"></a>Confira também
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
