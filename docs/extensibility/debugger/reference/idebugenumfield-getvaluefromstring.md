---
title: IDebugEnumField::GetValueFromString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e714e6b2028605eb9c820f904cedf9ed4c23eab8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716019"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Esse método retorna o valor associado com o nome de uma constante de enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
   string    pszValue,
   out ulong pValue
);
```

#### <a name="parameters"></a>Parâmetros
 `pszValue`

 [in] Uma cadeia de caracteres especificando o nome para o qual obter o valor. Observe que, para C++, isso é uma cadeia de caracteres largos.

 `pValue`

 [out] Retorna o valor numérico associado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE`, se o nome não é parte de enumeração ou um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é diferencia maiusculas de minúsculas. Se uma pesquisa diferencia maiusculas de minúsculas (por exemplo, em uma linguagem como Visual Basic em que os nomes não diferenciam maiusculas de minúsculas), use [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Consulte também
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)