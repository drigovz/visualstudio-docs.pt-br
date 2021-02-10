---
title: 'IDebugSymbolProvider:: GetMethodFieldsByName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName
helpviewer_keywords:
- IDebugSymbolProvider::GetMethodFieldsByName method
ms.assetid: 1f781320-81ef-4037-b068-f1864b271258
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77f6aa9561642b59a4cf605485011ac3b3ac75ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963517"
---
# <a name="idebugsymbolprovidergetmethodfieldsbyname"></a>IDebugSymbolProvider::GetMethodFieldsByName
Esse método obtém o campo que representa um nome de método totalmente qualificado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMethodFieldsByName( 
   LPCOLESTR          pszFullName,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetMethodFieldsByName(
   string               pszFullName,
   NAME_MATCH           nameMatch,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`pszFullName`\
no O nome do método.

`nameMatch`\
no Seleciona o tipo de correspondência, por exemplo, diferencia maiúsculas de minúsculas.

`ppEnum`\
fora Retorna um enumerador [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) para os campos associados a este método.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um método pode ser associado a vários campos se estiver sobrecarregado, por exemplo.

## <a name="see-also"></a>Confira também
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
