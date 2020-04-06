---
title: IDebugProperty2::SetValueAsReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721259"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Define o valor desta propriedade para o valor da referência dada.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>parâmetros
`rgpArgs`\
[em] Uma série de argumentos para passar para o definidor de propriedade de código gerenciado. Se o definidor de propriedades não aceitar argumentos ou se este objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) não se referir a tal definidor de propriedade, `rgpArgs` deve ser um valor nulo. Este parâmetro é tipicamente um valor nulo.

`dwArgCount`\
[em] O número de argumentos na `rgpArgs` matriz.

`pValue`\
[em] Uma referência, na forma de um objeto [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) ao valor a ser usado para definir esta propriedade.

`dwTimeout`\
[em] Quanto tempo levar para definir o valor, em milissegundos. Um valor `INFINITE`típico é . Isso afeta o tempo que qualquer avaliação possível pode levar.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro, tipicamente um dos seguintes:

|Erro|Descrição|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|A definição do valor de uma referência não é suportada.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|O valor não pode ser definido, pois esta propriedade se refere a um método.|
|`E_SETVALUE_VALUE_IS_READONLY`|O valor é somente leitura e não pode ser definido.|
|`E_NOTIMPL`|O método não é implementado.|

## <a name="see-also"></a>Confira também
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
