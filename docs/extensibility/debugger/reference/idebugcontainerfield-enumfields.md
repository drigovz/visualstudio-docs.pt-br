---
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6d3edeb677af728b1a0fd0e9cf8685e7919d79e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317937"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Cria um enumerador para os campos do contêiner.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`dwKindFilter`\
[in] Uma combinação de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constantes que selecione os campos a serem enumerados. Tipos de campo podem descrever os tipos de armazenamento, como classe ou informações primitivas ou específicas, como local, parâmetro ou ponteiro "this".

`dwModifiersFilter`\
[in] Uma combinação de [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) constantes que selecione os campos a serem enumerados. Modificadores de campo podem ser permissões de acesso, como público ou privado ou informações de armazenamento, como virtual, estático ou final.

`pszNameFilter`\
[in] O nome do campo a ser enumerado. Isso pode ser um valor nulo se todos os campos devem ser retornados.

`nameMatch`\
[in] Um valor a partir de [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) enumeração que controla se a pesquisa diferencia maiusculas de minúsculas ou não.

`ppEnum`\
[out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de campos. Retorna um valor nulo se não houver nenhum campo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, Retorna S_OK ou S_FALSE se não houver nenhum campo. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 O `dwKindFilter`, `dwModifiersFilter`, e `pszNameFilter` parâmetros podem ser combinados, por exemplo, para selecionar todos os métodos virtuais públicos denominados "MyMethod".

## <a name="see-also"></a>Consulte também
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)