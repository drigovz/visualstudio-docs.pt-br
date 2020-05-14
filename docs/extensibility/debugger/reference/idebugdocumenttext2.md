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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731564"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Esta interface representa um documento de texto.

## <a name="syntax"></a>Sintaxe

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um mecanismo de depuração (DE) implementa essa interface quando o código-fonte necessário para fornecer está na forma de texto. Uma vez que este é o caso mais típico, se um DE implementa a interface [IDebugDocument2,](../../../extensibility/debugger/reference/idebugdocument2.md) ele também deve implementar a `IDebugDocumentText2` interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use `QueryInterface` o método para obter `IDebugDocument2` esta interface a partir de uma interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos na `IDebugDocument2` interface, esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera o tamanho do texto nesta posição no documento.|
|[Gettext](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera o texto da posição especificada no documento.|

## <a name="remarks"></a>Comentários
 Um objeto que implementa essa <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface também deve <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> implementar a interface, que fornece a interface para um objeto [IDebugDocumentEvents2.](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
