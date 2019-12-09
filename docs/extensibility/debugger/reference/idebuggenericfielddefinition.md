---
title: IDebugGenericFieldDefinition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2887333789a9a4eae89a9f3f7538cf5b29ba02e7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351246"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Representa a definição de um campo para um tipo genérico do código gerenciado.

## <a name="syntax"></a>Sintaxe

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Métodos
 Essa interface implementa os métodos a seguir:

|Método|Descrição|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Constrói uma instância do campo considerando uma matriz de argumentos de tipo.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Recupera os parâmetros de tipo dado o número de parâmetros.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Recupera o número de parâmetros de tipo associado ao campo genérico.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll