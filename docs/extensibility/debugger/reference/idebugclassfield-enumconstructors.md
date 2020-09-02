---
title: 'IDebugClassField:: EnumConstructors | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 607f4f4af3021389628fcc1be446ebbe95628b7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734461"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Cria um enumerador para os construtores para esta classe.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`cMatch`\
no Um valor da enumeração [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) que especifica o tipo de construtores a serem enumerados.

`ppEnum`\
fora Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa a lista de construtores. Retorna um valor nulo se não houver construtores.

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retornará S_OK ou retornará S_FALSE se não houver nenhum construtor. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Cada elemento da enumeração é um objeto [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) que descreve um método de construtor.

 A lista de construtores normalmente não inclui os construtores padrão fornecidos por um compilador.

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
