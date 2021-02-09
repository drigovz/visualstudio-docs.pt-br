---
title: IDebugComPlusSymbolProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 658d7e5b8660a738616dc89be567f01c17406267
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928582"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
Representa um provedor de símbolos COM+ com métodos que são específicos do código gerenciado e estende o [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) **IDebugComPlusSymbolProvider**.

## <a name="syntax"></a>Sintaxe

```
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider
```

## <a name="methods"></a>Métodos
 Além dos métodos na interface [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) , essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Determina se o método especificado tem informações de linha.|
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Recupera um tipo dado seu nome.|
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Recupera um tipo dado seu token.|
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Determina se o endereço de depuração especificado é um ponto de sequência.|
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Carrega símbolos de depuração usando o método de retorno de chamada especificado.|
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|Carregue os símbolos de depuração de um fluxo de dados, dado o objeto **ICorDebugModule** .|
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|Carrega símbolos de depuração de acordo com o objeto **ICorDebugModule** .|

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
