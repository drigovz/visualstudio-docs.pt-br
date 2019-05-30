---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eb92e7076c308663ddf9ec760d1f2276affd0c87
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320846"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Esse método obtém a atualização de editar e continuar (ENC) para este programa. Um mecanismo de depuração personalizado sempre retorna `E_NOTIMPL`.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>Parâmetros
`ppUpdate`\
[out] Retorna uma interface interna que pode ser usada para atualizar este programa.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

> [!NOTE]
> Um mecanismo de depuração personalizado deve sempre retornar `E_NOTIMPL`.

## <a name="see-also"></a>Consulte também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)