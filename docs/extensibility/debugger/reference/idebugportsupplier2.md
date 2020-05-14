---
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddce454e6634d8cc177019e9d30b0ffcc7e7f1cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724480"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Esta interface fornece portas para o Gerenciador de depuração de sessão (SDM).

## <a name="syntax"></a>Sintaxe

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
Um fornecedor de porto personalizado implementa essa interface para representar um fornecedor de porta.

## <a name="notes-for-callers"></a>Observações para chamadores
Uma chamada `CoCreateInstance` para com o `GUID` retorno de um fornecedor de porta esta interface (esta é a maneira típica de obter esta interface). Por exemplo:

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

Uma chamada para [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) retorna essa interface, representando [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]o fornecedor de porta atual que está sendo usado por .

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) retorna esta interface, representando o fornecedor de portas que criou a porta.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) representa uma `IDebugPortSupplier` lista de `IEnumDebugPortSuppliers` interfaces (a interface é obtida da [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]representando todos os fornecedores de portas registrados com ).

Um mecanismo de depuração normalmente não interage com um fornecedor de porta.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
A tabela a seguir `IDebugPortSupplier2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Pega o nome do fornecedor do porto.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Obtém o identificador do fornecedor do porto.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Obtém um porto de um fornecedor portuário.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Enumera os portos que já existem.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Verifica se um fornecedor portuário suporta a adição de novas portas.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Adiciona um porto.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Remove uma porta.|

## <a name="remarks"></a>Comentários
Um fornecedor portuário pode identificar-se por nome e ID, adicionar e remover portas e enumerar todas as portas que o fornecedor portuário fornece.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
