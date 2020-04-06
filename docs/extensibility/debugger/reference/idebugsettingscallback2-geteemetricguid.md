---
title: IDebugSettingsCallback2::GetEEMetricGuid | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d95842ecde264accd8989a83ae652ac540183ef1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720007"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
Recupera o identificador exclusivo para uma métrica avaliadora de expressão dado o seu nome.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetEEMetricGuid(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   GUID*   pguidValue
);
```

```csharp
HRESULT GetEEMetricGuid(
   ref Guid guidLang,
   ref Guid guidVendor,
   string   pszMetric,
   out Guid pguidValue
);
```

## <a name="parameters"></a>parâmetros
`guidLang`\
[em] Identificador único da linguagem de programação.

`guidVendor`\
[em] Identificador exclusivo do fornecedor.

`pszMetric`\
[em] Nome da métrica.

`pguidValue`\
[fora] Retorna o identificador exclusivo da métrica.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
