---
title: IDebugSymbolProvider::GetNextAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1bf0798e0f49d9e7b2871c5601f966bc282b186
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62421444"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Obtém o endereço de depuração que segue um endereço de depuração fornecido em um método.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

#### <a name="parameters"></a>Parâmetros
 `pAddress`

 [in] Dado o endereço de depuração.

 `fStatementOnly`

 [in] Se for TRUE, limita os endereços de depuração para uma única instrução.

 `ppAddress`

 [out] Retorna o próximo endereço de depuração.

## <a name="return-value"></a>Valor de retorno
 Retorna um válidas `HRESULT`, normalmente S_OK.

## <a name="see-also"></a>Consulte também
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)