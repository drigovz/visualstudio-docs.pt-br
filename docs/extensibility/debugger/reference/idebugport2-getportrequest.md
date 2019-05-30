---
title: IDebugPort2::GetPortRequest | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: feaebf01b30876572ec0cbcf2bd33c141978fb26
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343729"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Obtém a descrição de uma porta que foi usada anteriormente para criar a porta (se disponível).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Parâmetros
`ppRequest`\
[out] Retorna um [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) objeto que representa a solicitação que foi usada para criar a porta.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  Retorna `E_PORT_NO_REQUEST` se uma porta não foi criada usando um [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) solicitação de porta.

## <a name="see-also"></a>Consulte também
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)