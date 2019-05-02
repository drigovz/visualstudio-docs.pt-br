---
title: IDebugSymbolProvider::GetLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b20222db9b007fbeee6daf0df1921e4c56744818
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915821"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Esse método obtém o idioma que foi usado para compilar o código no endereço de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetLanguage( 
   IDebugAddress* pAddress,
   GUID*          pguidLanguage,
   GUID*          pguidLanguageVendor
);
```

```csharp
int GetLanguage(
   IDebugAddress pAddress,
   out Guid      pguidLanguage,
   out Guid      pguidLanguageVendor
);
```

#### <a name="parameters"></a>Parâmetros
 `pAddress`

 [in] Um objeto de endereço representado por um [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

 `pguidLanguage`

 [out] Retorna um `GUID` que especifica o idioma.

 `pguidLanguageVendor`

 [out] Retorna um `GUID` que especifica o fornecedor de idioma.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O mecanismo de depuração chama esse método para obter as informações necessárias para selecionar o avaliador de expressão correto.

## <a name="see-also"></a>Consulte também
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)