---
title: IDebugMethodField::EnumArguments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf62392118ed3ddfb2dfbfca06588f0935f3192d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719893"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Cria um enumerador para o tipo de cada argumento necessário para chamar o método.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

#### <a name="parameters"></a>Parâmetros
 `ppParams`

 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de tipos de argumento. Retorna um valor nulo se não houver nenhum argumento.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhum argumento. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Cada elemento é um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa os tipos de cada parâmetro. Chame o [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método para recuperar informações sobre o tipo de cada parâmetro.

 Se o nome do parâmetro é necessário juntamente com o tipo, em seguida, chame o [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) método.

## <a name="see-also"></a>Consulte também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)