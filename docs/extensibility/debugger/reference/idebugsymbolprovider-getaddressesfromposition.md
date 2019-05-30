---
title: IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dcaef1e9675ae395826865604833fdb6683df944
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310179"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Esse método mapeia uma posição do documento em uma matriz de endereços de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parâmetros
`pDocPos`\
[in] A posição do documento.

`fStatmentOnly`\
[in] Se for TRUE, limita os endereços de depuração para uma única instrução.

`ppEnumBegAddresses`\
[out] Retorna um enumerador para os endereços iniciais de depuração associados com essa linha ou a instrução.

`ppEnumEndAddresses`\
[out] Retorna um [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) enumerador para os endereços de depuração final associados a essa linha ou a instrução.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Uma posição de documento normalmente indica um intervalo de linhas de código-fonte. Esse método fornece inicial e endereços de depuração finais associados a essas linhas. Algumas linguagens permitem que as instruções que abrangem várias linhas, ou linhas que contém mais de uma instrução. Esse método fornece um sinalizador para limitar os endereços de depuração para uma única instrução.

 É possível que uma única instrução ter vários endereços de depuração, como no caso de modelos.

## <a name="see-also"></a>Consulte também
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)