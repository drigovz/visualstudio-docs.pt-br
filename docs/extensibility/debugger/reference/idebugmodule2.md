---
title: IDebugModule2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbbea1b52133de41dd26f437aeba31a0eff5a50a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726912"
---
# <a name="idebugmodule2"></a>IDebugModule2
Essa interface representa um módulo — ou seja, uma unidade executável de um programa — como uma DLL.

## <a name="syntax"></a>Sintaxe

```
IDebugModule2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa esta interface para representar um módulo e para fornecer acesso a informações sobre esse módulo.

## <a name="notes-for-callers"></a>Observações para chamadores
 Uma chamada para [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) retorna esta interface. O DE envia a interface [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) para o SDM (Session Debug Manager, gerenciador de depuração de sessão) usando o método [Evento.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

 Essa interface também pode ser retornada em uma estrutura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) (que é retornada por uma chamada para [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).

- [Next](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) também retorna esta interface ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) retorna a interface [IEnumDebugModules2).](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugModule2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Obtém o [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) que descreve este módulo.|
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETE. NÃO USE. Recarrega os símbolos deste módulo.|

## <a name="remarks"></a>Comentários
 As informações do módulo podem ser exibidas na janela **Módulos** do IDE.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [Getmodule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
