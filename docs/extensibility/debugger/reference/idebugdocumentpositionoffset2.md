---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 69fbdef70fc9c95ef571ce0ce796199292417ca0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933551"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Representa uma posição em um arquivo de origem como um deslocamento de caractere.

## <a name="syntax"></a>Sintaxe

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Implementado pelo IDE e consumido pelos mecanismos de depuração.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugDocumentPositionOffset2` .

|Método|Descrição|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera o intervalo para a posição atual do documento.|

## <a name="remarks"></a>Comentários
 Isso retorna as mesmas informações que o [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) , mas em `char` deslocamentos do início do documento. Isso apresenta o documento como ele existiria em um disco, ou seja, uma matriz unidimensional de caracteres, em vez das informações de linha e coluna que normalmente são retornadas.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
