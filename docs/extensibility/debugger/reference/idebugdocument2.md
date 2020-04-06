---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c959c018dd4da0ff088c4fb52c0420de83b4eac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731997"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Esta interface representa um documento de origem.

## <a name="syntax"></a>Sintaxe

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]normalmente implementa essa interface. Um mecanismo de depuração (DE) também pode implementar essa interface quando precisa fornecer o código-fonte e a fonte não existe no disco.  Nesses casos, o DE também implementaria interfaces [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) e [IDebugActivateDocumentEvent2,](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) bem como alguns métodos adicionais nas interfaces [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) e [IDebugDocumentPosition2.](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

## <a name="notes-for-callers"></a>Observações para chamadores
 Métodos nas `IDebugDocumentContext2` `IDebugDisassemblyStream2`interfaces `IDebugDocumentPosition2` `IDebugActivateDocumentEvent2` retornam esta interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugDocument2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Obtém o nome do documento em uma das várias formas.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Obtém o identificador de classe do documento.|

## <a name="remarks"></a>Comentários
 Esta interface só é implementada quando o DE fornece o código fonte. Por exemplo, quando você está depurando script em uma página HTML, o DE fornece o código-fonte porque a fonte é baixada ou gerada dinamicamente e não existe como um arquivo de disco. Ao depurar idiomas tradicionais, como C++, essa interface não precisa ser implementada.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
