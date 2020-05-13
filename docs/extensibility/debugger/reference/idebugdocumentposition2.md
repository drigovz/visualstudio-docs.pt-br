---
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63742f220d5a776fca180a3f9f7fe9c15e04c66a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731643"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Esta interface representa uma posição abstrata em um arquivo de origem.

## <a name="syntax"></a>Sintaxe

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O Visual Studio normalmente implementa essa interface. Um mecanismo de depuração (DE) também implementaria essa interface se ele deve fornecer seu próprio código-fonte (como quando o DE implementa a interface [IDebugDocument2).](../../../extensibility/debugger/reference/idebugdocument2.md)

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface é passada como um argumento para [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Também é fornecido como parte de uma união [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (especificamente, uma estrutura [BP_LOCATION_CODE_FILE_LINE)](../../../extensibility/debugger/reference/bp-location-code-file-line.md) que, por sua vez, faz parte da estrutura [BP_REQUEST_INFO,](../../../extensibility/debugger/reference/bp-request-info.md) que é usada na criação de um ponto de ruptura pendente.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugDocumentPosition2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtém o nome do arquivo do arquivo de origem que contém esta posição do documento.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Obtém o documento contendo.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Determina se esta posição está contida no documento dado.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtém o alcance para esta posição de documento.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
