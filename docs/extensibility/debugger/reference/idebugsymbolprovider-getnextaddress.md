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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ea45e3aa1f59353e0a395a61b0309144b413227
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223994"
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

## <a name="parameters"></a>Parâmetros
 `pAddress`\

 [in] Dado o endereço de depuração.

 `fStatementOnly`\

 [in] Se for TRUE, limita os endereços de depuração para uma única instrução.

 `ppAddress`\

 [out] Retorna o próximo endereço de depuração.

## <a name="return-value"></a>Valor de retorno
 Retorna um válidas `HRESULT`, normalmente S_OK.

## <a name="see-also"></a>Consulte também
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)