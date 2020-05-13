---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84db1b672a9460ef3809162a2a1433f269796046
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726733"
---
# <a name="idebugmodule3"></a>IDebugModule3
Esta interface representa um módulo que suporta locais alternativos de símbolos e estados JustMyCode.

## <a name="syntax"></a>Sintaxe

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface para suportar locais alternativos de símbolos e para trabalhar com estados JustMyCode (consulte o [Glossário do Debugger do Estúdio Visual](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) para uma definição de "JustMyCode").

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) retorna esta interface. O DE envia a interface [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) para o SDM (Session Debug Manager, gerenciador de depuração de sessão) usando o método [Evento.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) Além disso, uma chamada para [QueryInterface](/cpp/atl/queryinterface) em uma interface [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) retorna esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos na interface [IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Retorna uma lista de caminhos pesquisados por símbolos e os resultados da pesquisa de cada caminho.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Carrega e inicializa símbolos para o módulo atual.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Retorna o sinalizador especificando se o módulo representa o código do usuário.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Especifica se o módulo deve ser considerado código de usuário ou não.|

## <a name="remarks"></a>Comentários
 Visual Studio é o consumidor típico desta interface.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
