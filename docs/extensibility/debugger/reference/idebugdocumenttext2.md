---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b5def7f6cc4ac5ced91ca0a273ce750003dca20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731564"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Essa interface representa um documento de texto.

## <a name="syntax"></a>Syntax

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um mecanismo DE depuração (DE) implementa essa interface quando o código-fonte que ele precisa fornecer está na forma de texto. Como esse é o caso mais comum, se um DE implementa a interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , ele também deve implementar a `IDebugDocumentText2` interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use o `QueryInterface` método para obter essa interface de uma `IDebugDocument2` interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 Além dos métodos na `IDebugDocument2` interface, essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera o tamanho do texto nesta posição no documento.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera o texto da posição especificada no documento.|

## <a name="remarks"></a>Comentários
 Um objeto que implementa essa interface também deve implementar a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface, que fornece a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface para um objeto [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) .

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
