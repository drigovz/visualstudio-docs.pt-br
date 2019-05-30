---
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c2fbce0154a5ebefd04ea3614d16db16799510
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333428"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Essa interface representa uma posição abstrata em um arquivo de origem.

## <a name="syntax"></a>Sintaxe

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Normalmente, o Visual Studio implementa essa interface. Um mecanismo de depuração (DES) também deve implementar essa interface se ele deve fornecer seu próprio código-fonte (como quando o DE implementa o [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface).

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é passada como um argumento para [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Ele também é fornecido como parte de um [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) união (especificamente, um [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) estrutura) que por sua vez faz parte dos [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estrutura, que é usado na criação de um ponto de interrupção pendente.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugDocumentPosition2`.

|Método|Descrição|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtém o nome do arquivo do arquivo de origem que contém essa posição do documento.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Obtém a que contém o documento.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina se essa posição está contida em um determinado documento.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtém o intervalo para essa posição do documento.|

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)