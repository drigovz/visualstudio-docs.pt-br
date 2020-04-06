---
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b04b0805aec5ecee818fa42e1d76a76cce12b66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727846"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Representa um parâmetro para um tipo genérico de código gerenciado.

## <a name="syntax"></a>Sintaxe

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Usado para apoio de genéricos.

## <a name="methods"></a>Métodos
 Além dos métodos na interface [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Retorna o número de restrições que estão associadas a este parâmetro genérico.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Recupera as restrições que estão associadas a este parâmetro genérico.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Recupera as bandeiras para este parâmetro genérico.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Recupera o índice deste parâmetro genérico.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Recupera o nome deste parâmetro genérico.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Recupera o tipo ou o método proprietário deste parâmetro genérico.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
