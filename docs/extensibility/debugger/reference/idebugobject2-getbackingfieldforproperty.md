---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9aaf4111670ad67f6a01bde60bf5f35c3b793983
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317352"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtém o campo ou variável (se houver) que pode ser fazendo a propriedade representada por este objeto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parâmetros
`ppObject`\
[out] Uma [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objeto que descreve o campo de suporte.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 O [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) objeto representa uma propriedade de classe do código gerenciado, ou seja, um método com um get e/ou o acessador set. Essas propriedades geralmente requerem uma variável para conter o valor manipulado pela propriedade. Essa variável é conhecida como o campo de suporte. Se não houver nenhum campo de suporte para o objeto, em seguida, certifique-se de retornar um valor nulo: alguns chamadores não podem pagar a atenção para o valor de retorno, mas ficará em vez disso, para ver se um valor nulo foi retornado no `ppObject`.

## <a name="see-also"></a>Consulte também
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)