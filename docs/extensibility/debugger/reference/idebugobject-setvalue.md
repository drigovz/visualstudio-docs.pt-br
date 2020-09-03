---
title: 'IDebugObject:: SetValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e4652eb3c77a1871063dfa71b464fb1f7c43f94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726360"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Define o valor do objeto a partir de uma série de bytes consecutivos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>Parâmetros
`pValue`\
no Uma matriz de bytes que representa o novo valor.

`nSize`\
no O tamanho do valor em bytes.

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Os valores na matriz são copiados para esse objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , substituindo qualquer valor existente. O tamanho do novo valor pode ser maior ou menor do que o valor existente. Essa `IDebugObject` não pode ser uma referência nula.

## <a name="see-also"></a>Confira também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
