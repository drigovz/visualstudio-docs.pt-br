---
title: 'IDebugMethodField:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63351a106497121c40fa7fb04d95b59494e4575e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941821"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Determina se um atributo personalizado específico foi definido.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parâmetros
`pszCustomAttributeName`\
no Uma cadeia de caracteres que contém o nome do atributo personalizado a ser localizado.

## <a name="return-value"></a>Valor retornado
 Retorna S_OK se o atributo personalizado for definido nesse método; caso contrário, retorna S_FALSE.

## <a name="see-also"></a>Consulte também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
