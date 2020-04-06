---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721826"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permite que um nó de programa seja notificado de uma tentativa de anexar ao programa associado.

## <a name="syntax"></a>Sintaxe

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esta interface é implementada na mesma classe que implementa a interface [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para receber notificação de uma operação de attach e para fornecer uma oportunidade de cancelar a operação de conexão.

## <a name="notes-for-callers"></a>Observações para chamadores
 Obtenha esta interface `QueryInterface` chamando o método em um objeto [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md) O método [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) deve ser chamado antes do método [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md) para dar ao nó do programa a chance de interromper o processo de anexação.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Esta interface implementa o seguinte método:

|Método|Descrição|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Anexa-se ao programa associado ou adia o processo de anexação ao método [Anexar.](../../../extensibility/debugger/reference/idebugengine2-attach.md)|

## <a name="remarks"></a>Comentários
 Esta interface é a alternativa preferida ao método [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) depreciado. Todos os motores de depuração estão sempre carregados com a `CoCreateInstance` função, ou seja, eles são instanciados fora do espaço de endereço do programa que está sendo depurado.

 Se uma implementação `IDebugProgramNode2::Attach_V7` anterior do `GUID` método estava simplesmente definindo o programa sendo depurado, então apenas o método [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) precisa ser implementado.

 Se uma implementação `IDebugProgramNode2::Attach_V7` prévia do método usou a interface de retorno de chamada fornecida, então essa `IDebugProgramNodeAttach2` funcionalidade precisa ser movida para uma implementação do método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) e a interface não precisa ser implementada.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
