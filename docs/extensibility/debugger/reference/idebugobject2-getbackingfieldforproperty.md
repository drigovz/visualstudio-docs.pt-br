---
title: idebugobject2::GetbackingfieldForProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726248"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtém o campo ou variável (se houver) que pode estar apoiando a propriedade representada por este objeto.

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

## <a name="parameters"></a>parâmetros
`ppObject`\
[fora] Um objeto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) descrevendo o campo de backup.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O objeto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) representa uma propriedade de classe de código gerenciada, ou seja, um método com um acessório get and/or set. Tais propriedades geralmente requerem uma variável para conter o valor manipulado pela propriedade. Esta variável é conhecida como o campo de apoio. Se não houver campo de apoio para o objeto, certifique-se de retornar um valor nulo: alguns chamadores podem `ppObject`não prestar atenção ao valor de retorno, mas, em vez disso, procurarão ver se um valor nulo foi devolvido em .

## <a name="see-also"></a>Confira também
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
