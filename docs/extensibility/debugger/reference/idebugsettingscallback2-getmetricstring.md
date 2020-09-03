---
title: 'IDebugSettingsCallback2:: getmetricstring | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricString
- GetMetricString
ms.assetid: ecc875a2-8ac6-444c-a839-5191a780fd6b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0c90f3261809bf41b3aa4bd3337a16c1190fcfc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719968"
---
# <a name="idebugsettingscallback2getmetricstring"></a>IDebugSettingsCallback2::GetMetricString
Recupera a cadeia de caracteres de valor da métrica de acordo com seu nome.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMetricString(
    LPCWSTR pszType,
    REFGUID guidSection,
    LPCWSTR pszMetric,
    BSTR*   pbstrValue
);
```

```csharp
private int GetMetricString(
    string     pszType,
    ref Guid   guidSection,
    string     pszMetric,
    out string pbstrValue
);
```

## <a name="parameters"></a>Parâmetros
`pszType`\
no Tipo da métrica.

`guidSection`\
no Identificador exclusivo da seção.

`pszMetric`\
no Nome da métrica.

`pbstrValue`\
fora Retorna a cadeia de caracteres de valor da métrica.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
