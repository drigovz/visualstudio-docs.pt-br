---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551945ded9d1ba3e973f18c21463a896cbd478c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730243"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Este método usa uma pesquisa insensível a casos para devolver o valor associado ao nome de uma constante de enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>parâmetros
`pszValue`\
[em] Uma seqüência especificando o nome para qual obter o valor. Note que para C++, esta é uma seqüência de caracteres ampla.

`pValue`\
[fora] Retorna o valor numérico associado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, `S_FALSE`retorna, se o nome não faz parte da enumeração, ou um código de erro.

## <a name="remarks"></a>Comentários
 Este método é insensível a casos. Se for necessária uma pesquisa sensível a maiúsculas e minúsculas (por exemplo, em um idioma como C++ onde os nomes são sensíveis a maiúsculas e minúsculas), use [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Confira também
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
