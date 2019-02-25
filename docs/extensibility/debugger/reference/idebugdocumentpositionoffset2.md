---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf713ea542901cbde588600d40f144f0fae843e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718840"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Representa uma posição em um arquivo de origem como um deslocamento de caractere.

## <a name="syntax"></a>Sintaxe

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Implementado pelo IDE e consumido por mecanismos de depuração.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugDocumentPositionOffset2`.

|Método|Descrição|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Recupera o intervalo para a posição atual do documento.|

## <a name="remarks"></a>Comentários
 Isso retorna as mesmas informações que [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) , mas na `char` deslocamentos do início do documento. Isso apresenta o documento como ele deve existir em um disco, ou seja, uma matriz unidimensional de caracteres, em vez das informações de linha e coluna que normalmente é retornado.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)