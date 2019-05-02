---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a7547639fb2f7f3068dd7f738b0c0d10ea926f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916678"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Essa interface permite que um mecanismo de depuração (DES) ou fornecedores de porta personalizada para registrar os programas para depuração.

## <a name="syntax"></a>Sintaxe

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
Visual Studio implementa essa interface para registrar os programas que está sendo depurados para torná-las visíveis para depuração entre vários processos.

## <a name="notes-for-callers"></a>Observações para chamadores
Chamar do COM `CoCreateInstance` funcionar com `CLSID_ProgramPublisher` obter interface (veja o exemplo). A DE ou de um fornecedor de porta personalizada usa essa interface para registrar os nós de programa que representam os programas sendo depurado.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
Essa interface implementa os métodos a seguir:

|Método|Descrição|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Disponibiliza um nó de programa para DEs e a sessão de depuração SDM (Gerenciador).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Remove um nó de programa para que ele não está mais disponível.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Um programa torna disponível DEs e o SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Remove um programa para que ele não está mais disponível.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Define um sinalizador que indica se um depurador está presente.|

## <a name="remarks"></a>Comentários
Essa interface disponibiliza programas e nós de programa (ou seja, "Publicar") para uso por DEs e o Gerenciador de sessão de depuração (SDM). Para acessar programas publicados e nós de programa, use o [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interface. Isso é a única maneira de que Visual Studio pode reconhecer que um programa está sendo depurado.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemplo
Este exemplo mostra como instanciar o Editor de programa e registrar um nó de programa. Isso é obtido do Tutorial [o nó do programa de publicação](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
