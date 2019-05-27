---
title: IDebugPortSupplier2::AddPort | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 05222901081fe3ba93f4648f3a2689d3d9a5c6ea
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204474"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Adiciona uma porta.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT AddPort( 
   IDebugPortRequest2* pRequest,
   IDebugPort2**       ppPort
);
```

```csharp
int AddPort( 
   IDebugPortRequest2 pRequest,
   out IDebugPort2    ppPort
);
```

## <a name="parameters"></a>Parâmetros
`pRequest`\
[in] Uma [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) objeto que descreve a porta a ser adicionado.

`ppPort`\
[out] Retorna um [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa a porta.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método cria, na verdade, a porta solicitada, bem como adicioná-lo à lista interna do fornecedor de porta de portas ativas. O [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) método pode ser chamado primeiro para evitar possíveis atrasos demorados.

## <a name="see-also"></a>Consulte também
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)