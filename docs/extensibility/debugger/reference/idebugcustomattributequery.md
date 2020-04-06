---
title: IDebugCustomAttributeQuery | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 598db5ad711c8b61339e188311c1a437a24d013c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732615"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
Representa uma consulta para atributos personalizados em um método ou tipo.

## <a name="syntax"></a>Sintaxe

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>Métodos
 Esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Recupera um atributo personalizado dado seu nome.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Determina-se no atributo personalizado especificado é definido.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
