---
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f502479d4c74eb0b5cfa71db52698121830e66e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953468"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Obtém o campo ou variável (se houver) que pode estar fazendo backup da propriedade representada por esse objeto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parâmetros
`ppObject`\
fora Um objeto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) que descreve o campo de backup.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O objeto [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) representa uma propriedade de classe de código gerenciado, ou seja, um método com um acessador get e/ou set. Essas propriedades geralmente exigem uma variável para conter o valor manipulado pela propriedade. Essa variável é conhecida como o campo de backup. Se não houver nenhum campo de apoio para o objeto, certifique-se de retornar um valor nulo: alguns chamadores podem não prestar atenção ao valor de retorno, mas, em vez disso, verificará se um valor nulo foi retornado em `ppObject` .

## <a name="see-also"></a>Confira também
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
