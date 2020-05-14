---
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733228"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Cria um enumerador para os campos do recipiente.

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

## <a name="parameters"></a>parâmetros
`dwKindFilter`\
[em] Uma combinação de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) constantes que selecionam os campos a serem enumerados. Os tipos de campo podem descrever tipos de armazenamento, como classe ou primitivo, ou informações específicas, como ponteiro local, parâmetro ou "este".

`dwModifiersFilter`\
[em] Uma combinação de [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) constantes que selecionam os campos a serem enumerados. Modificadores de campo podem ser permissões de acesso, como informações públicas ou privadas, ou informações de armazenamento, como virtual, estática ou final.

`pszNameFilter`\
[em] O nome do campo a ser enumerado. Isso pode ser um valor nulo se todos os campos forem devolvidos.

`nameMatch`\
[em] Um valor da [enumeração NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) que controla se a pesquisa é sensível a maiúsculas e minúsculas.

`ppEnum`\
[fora] Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) representando a lista de campos. Retorna um valor nulo se não houver campos.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK ou S_FALSE se não houver campos. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Os `dwKindFilter` `dwModifiersFilter`parâmetros `pszNameFilter` e parâmetros podem ser combinados, por exemplo, para selecionar todos os métodos virtuais públicos chamados "MyMethod".

## <a name="see-also"></a>Confira também
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
