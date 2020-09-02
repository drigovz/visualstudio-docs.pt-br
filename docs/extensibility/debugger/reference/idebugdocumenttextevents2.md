---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a1736890ac78e7aaf20b4a639b1794fc63b5ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731370"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Essa interface é usada para notificar o Visual Studio sobre alterações no documento de origem que são fornecidas pelo mecanismo de depuração.

## <a name="syntax"></a>Syntax

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O DE implementa essa interface para dar suporte à realização de alterações no código-fonte. Normalmente, essa interface é implementada no mesmo objeto que implementa a interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="notes-for-callers"></a>Observações para chamadores
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Obtém essa interface por meio de uma chamada para o <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> método. A <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface é Obtida de uma chamada para o <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> método. A <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface é obtida chamando o método [QueryInterface](/cpp/atl/queryinterface) em uma interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A tabela a seguir mostra os métodos de `IDebugDocumentTextEvents2` .

|Método|Descrição|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indica que o documento inteiro foi destruído.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Notifica o pacote de depuração que o texto foi inserido no documento.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Notifica o pacote de depuração que o texto foi removido do documento.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Notifica o pacote de depuração que o texto foi substituído no documento.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Notifica o pacote de depuração que os atributos de texto foram atualizados no documento.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Notifica o destinatário sobre o evento de que os atributos do documento foram atualizados.|

## <a name="remarks"></a>Comentários
 Somente os mecanismos de depuração que fornecem seus próprios documentos tiraram proveito da `IDebugDocumentTextEvent2` interface. Um exemplo disso seria um mecanismo de depuração de scripts. No processo de interpretação de scripts, o novo código-fonte pode ser gerado e não está presente em nenhum arquivo de disco e só é conhecido como de.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
