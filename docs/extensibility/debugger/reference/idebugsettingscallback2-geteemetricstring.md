---
title: IDebugSettingsCallback2::GetEEMetricString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2091cd052923fe375bf9ba90ffdad50c993f5b4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703832"
---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
Recupera a cadeia de caracteres do valor de uma métrica de avaliador de expressão dada seu nome.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetEEMetricString(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricString(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

#### <a name="parameters"></a>Parâmetros
 `guidLang`

 [in] Identificador exclusivo da linguagem de programação.

 `guidVendor`

 [in] Identificador exclusivo do fornecedor.

 `pszMetric`

 [in] Nome da métrica.

 `pbstrValue`

 [out] Retorna a cadeia de caracteres do valor de métrica.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)