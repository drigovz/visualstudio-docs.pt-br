---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43716ce3b01464d2937fd75ce90ec5028679ef47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330640"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Essa interface representa um documento de texto.

## <a name="syntax"></a>Sintaxe

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Um mecanismo de depuração (DES) implementa essa interface quando ele precisa fornecer o código-fonte está na forma de texto. Como esse é o caso mais comum, se a DE implementa o [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface, ele deve implementar também a `IDebugDocumentText2` interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use o `QueryInterface` método para obter essa interface de um `IDebugDocument2` interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos no `IDebugDocument2` interface, essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera o tamanho do texto nessa posição no documento.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera o texto da posição especificada no documento.|

## <a name="remarks"></a>Comentários
 Um objeto que implementa essa interface deve implementar também a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> da interface, que fornece a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface para um [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) objeto.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)