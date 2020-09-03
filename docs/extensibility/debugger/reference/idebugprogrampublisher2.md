---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721530"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Essa interface permite que um mecanismo DE depuração (DE) ou fornecedores de porta personalizada registrem programas para depuração.

## <a name="syntax"></a>Syntax

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
O Visual Studio implementa essa interface para registrar programas que estão sendo depurados a fim de torná-los visíveis para depuração em vários processos.

## <a name="notes-for-callers"></a>Observações para chamadores
Chame `CoCreateInstance` a função de com `CLSID_ProgramPublisher` para obter essa interface (consulte o exemplo). Um fornecedor DE porta personalizada usa essa interface para registrar nós de programa que representam programas sendo depurados.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
Essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Torna um nó de programa disponível para DEs e o SDM (Gerenciador de depuração de sessão).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Remove um nó de programa para que ele não esteja mais disponível.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Disponibiliza um programa para DEs e o SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Remove um programa para que ele não esteja mais disponível.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Define um sinalizador que indica que um depurador está presente.|

## <a name="remarks"></a>Comentários
Essa interface torna os programas e os nós de programa disponíveis (ou seja, "publica-os") para uso pelo DEs e pelo SDM (Gerenciador de depuração de sessão). Para acessar programas publicados e nós de programas, use a interface [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) . Essa é a única maneira que o Visual Studio pode reconhecer que um programa está sendo depurado.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemplo
Este exemplo mostra como criar uma instância do editor do programa e registrar um nó de programa. Isso é tirado do tutorial, [publicando o nó do programa](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

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

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
