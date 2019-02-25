---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 866b3718ac6071b5e7bd5cc44ed2ca17dd54dc8e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687634"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Essa interface enumera os programas em execução na sessão de depuração atual.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração (DES) implementa essa interface para fornecer uma lista de programas sendo depurado por DE.

## <a name="notes-for-callers"></a>Observações para chamadores
 Chamadas do Visual Studio [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) para obter essa interface. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) não é usado pelo Visual Studio.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IEnumDebugPrograms2`.

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera um número especificado de programas em uma sequência de enumeração.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignora um número especificado de programas em uma sequência de enumeração.|
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Redefine uma sequência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtém o número de programas em um enumerador.|

## <a name="remarks"></a>Comentários
 O Visual Studio usa esta interface:

-   Popular o **módulos** janela (chamando [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) e, em seguida, chamando [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) em cada programa).

-   Popular o **anexar ao processo** lista (chamando `IDebugProcess2::EnumPrograms` e, em seguida, chamar [QueryInterface](/cpp/atl/queryinterface) em cada [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface para obter um [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interface).

-   Gerar uma lista de DEs que pode depurar cada programa no processo (usando [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

-   Aplicar atualizações de editar e continuar (ENC) para cada programa (chamando IDebugProcess2::EnumPrograms e, em seguida, chamar [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)