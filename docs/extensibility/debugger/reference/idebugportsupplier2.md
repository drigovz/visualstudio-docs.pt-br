---
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 947a311cb1e83eaa131730725aeb7938e5615f0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340060"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Essa interface fornece portas para o Gerenciador de sessão de depuração (SDM).

## <a name="syntax"></a>Sintaxe

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
Um fornecedor de porta personalizada implementa essa interface para representar um fornecedor de porta.

## <a name="notes-for-callers"></a>Observações para chamadores
Uma chamada para `CoCreateInstance` com um fornecedor de porta `GUID` retorna essa interface (essa é a maneira típica para obter essa interface). Por exemplo:

```cpp
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)
{
    IDebugPortSupplier2 *pPS = NULL;
    if (pPortSupplierGuid != NULL) {
        CComPtr<IDebugPortSupplier2> spPortSupplier;
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);
        if (spPortSupplier != NULL) {
            pPS = spPortSupplier.Detach();
        }
    }
    return (pPS);
}
```

Uma chamada para [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) retorna essa interface, que representa o fornecedor de porta atual que está sendo usado por [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) retorna essa interface, que representa o fornecedor de porta que criou a porta.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) representa uma lista de `IDebugPortSupplier` interfaces (o `IEnumDebugPortSuppliers` interface é obtido do [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), que representa todos os fornecedores de porta registrados com [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).

Um mecanismo de depuração normalmente não interage com um fornecedor de porta.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
A tabela a seguir mostra os métodos de `IDebugPortSupplier2`.

|Método|Descrição|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Obtém o nome do fornecedor de porta.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Obtém o identificador de fornecedor de porta.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Obtém uma porta de um fornecedor de porta.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumera as portas que já existem.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Verifica se um fornecedor de porta dá suporte à adição de novas portas.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Adiciona uma porta.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Remove uma porta.|

## <a name="remarks"></a>Comentários
Um fornecedor de porta pode identificar-se por nome e ID, adicionar e remover as portas e enumerar todas as portas que fornece o fornecedor de porta.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
