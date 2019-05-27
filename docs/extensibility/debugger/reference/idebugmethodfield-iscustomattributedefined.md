---
title: IDebugMethodField::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0dfbe855f5bdcbfda384e7a9a180fc8f86595b85
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211946"
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
[in] Uma cadeia de caracteres que contém o nome do atributo personalizado para localizar.

## <a name="return-value"></a>Valor de retorno
 Retorna que S_OK se o atributo personalizado é definido neste método, caso contrário retorna S_FALSE.

## <a name="see-also"></a>Consulte também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)