---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d967ec9cf406f7dae691c3f05eda514e0907c7e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731605"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Representa uma posição em um arquivo de origem como um deslocamento de caracteres.

## <a name="syntax"></a>Sintaxe

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Implementado pelo IDE e consumido por motores de depuração.

## <a name="methods"></a>Métodos
 A tabela a seguir `IDebugDocumentPositionOffset2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera o intervalo para a posição atual do documento.|

## <a name="remarks"></a>Comentários
 Isso retorna as mesmas informações `char` que [getrange,](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) mas em deslocamentos desde o início do documento. Isso apresenta o documento como se existisse em um disco, ou seja, uma matriz unidimensional de caracteres, em vez das informações de linha e coluna que normalmente são devolvidas.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
