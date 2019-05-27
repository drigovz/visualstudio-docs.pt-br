---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca6afee5cce069b212a2f1a88335d2fbce2e0427
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206893"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Chamado por um manipulador de eventos para recuperar os resultados de um processo de carregamento de símbolo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>Parâmetros
`pModule`\
[out] Um objeto IDebugModule3 que representa o módulo para o qual os símbolos foram carregados.

`pbstrDebugMessage`\
[no, out] Retorna uma cadeia de caracteres que contém todas as mensagens de erro do módulo. Se não houver nenhum erro, essa cadeia de caracteres conterá apenas o nome do módulo, mas nunca está vazia.

> [!NOTE]
> [C++] `pbstrDebugMessage` não pode ser `NULL` e deve ser liberado com `SysFreeString`.

`pdwModuleInfoFlags`\
[out] Uma combinação de sinalizadores do [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) enumeração que indica se todos os símbolos foram carregados.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Quando um manipulador recebe o [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) evento após uma tentativa para carregar símbolos de depuração para um módulo, o manipulador pode chamar esse método para determinar os resultados do que a carga.

## <a name="see-also"></a>Consulte também
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)