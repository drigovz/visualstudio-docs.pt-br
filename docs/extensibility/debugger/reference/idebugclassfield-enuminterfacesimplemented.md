---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a5c951ac4f6f33495dad4136a1a09c11e639e029
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335359"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Cria um enumerador para as interfaces implementadas por esta classe.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`ppEnum`\
[out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de interfaces implementadas. Retorna um valor nulo se não houver nenhuma interface.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhuma interface implementado nesta classe. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Cada elemento da enumeração é um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que descreve uma interface. Observe que não gerenciados [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] código não usa interfaces como uma entidade separada para que esse método sempre retorna um valor nulo para não gerenciado [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] código.

## <a name="see-also"></a>Consulte também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)