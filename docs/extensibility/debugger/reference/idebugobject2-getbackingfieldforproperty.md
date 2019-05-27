---
title: IDebugObject2::GetBackingFieldForProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac19bd3ed139b15744e408b7114c6879a17e2c61
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199859"
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