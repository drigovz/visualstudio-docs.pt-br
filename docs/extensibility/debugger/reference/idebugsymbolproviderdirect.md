---
title: IDebugSymbolProviderDirect | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd1201007b27d3c7c51b5b0d862b36ba0549429b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718907"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Representa um provedor de símbolos que tem acesso direto a metadados e interfaces de símbolos principais.

## <a name="syntax"></a>Sintaxe

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Métodos
 Esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Recupera o identificador de domínio do aplicativo dado o endereço de depuração.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Recupera informações sobre os módulos no grupo símbolo.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Recupera informações sobre o grupo símbolo do qual o provedor de símbolos é membro.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Recupera as informações de importação de metadados.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Recupera informações sobre o método no endereço de depuração especificado.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Recupera um leitor de símbolos para código não gerenciado.|

## <a name="remarks"></a>Comentários
 Esta interface pode ser usada em vez da maioria das outras interfaces do provedor de símbolos. Ele fornece acesso direto aos `CorSym` metadados e interfaces.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
