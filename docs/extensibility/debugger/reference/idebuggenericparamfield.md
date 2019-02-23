---
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab5cb19475ae92ab1e89bdce5c833e0f18a2cccb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720699"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Representa um parâmetro para um tipo genérico do código gerenciado.

## <a name="syntax"></a>Sintaxe

```
IDebugGenericParamField : IDebugField
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Usado para oferecer suporte a genéricos.

## <a name="methods"></a>Métodos
 Além dos métodos na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Retorna o número de restrições que estão associados esse parâmetro genérico.|
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Recupera as restrições que estão associadas esse parâmetro genérico.|
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Recupera os sinalizadores para esse parâmetro genérico.|
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Recupera o índice desse parâmetro genérico.|
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Recupera o nome desse parâmetro genérico.|
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Recupera o proprietário do tipo ou método desse parâmetro genérico.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll