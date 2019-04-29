---
title: IDebugReference2::SetValueAsString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsString
helpviewer_keywords:
- IDebugReference2::SetValueAsString
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67e3ac6bda70a25baf7546c709849c650372c649
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869003"
---
# <a name="idebugreference2setvalueasstring"></a>IDebugReference2::SetValueAsString
Define o valor de uma referência de uma cadeia de caracteres. Reservado para uso futuro.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   DWORD     dwRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   dwRadix,
   uint   dwTimeout
);
```

#### <a name="parameters"></a>Parâmetros
 `pszValue`

 [in] O valor como uma cadeia de caracteres.

 `dwRadix`

 [in] A base a ser usada na formatação de todas as informações numéricas.

 `dwTimeout`

 [in] Tempo máximo, em milissegundos, para aguardar antes de retornar do método. Use `INFINITE` para aguardar indefinidamente.

## <a name="return-value"></a>Valor de retorno
 Sempre retorna `E_NOTIMPL`.

## <a name="see-also"></a>Consulte também
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)