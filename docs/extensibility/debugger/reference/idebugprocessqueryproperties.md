---
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08abf401b4e8f0e7a33d882e8178d77e6f248318
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723283"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Esta interface é uma interface de extensão implementada pelos implementadores [IDebugProcess2.](../../../extensibility/debugger/reference/idebugprocess2.md) Ele permite que o implementador obtenha informações sobre o ambiente do processo de depuração.

## <a name="syntax"></a>Sintaxe

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Implemente esta interface para obter informações sobre o ambiente de execução de um processo de depuração.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugProcessQueryProperties`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Consultas para um valor de propriedade.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Consultas para valores de propriedade.|

## <a name="remarks"></a>Comentários
 Esta interface raramente é implementada.

## <a name="requirements"></a>Requisitos
 Cabeçalho: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
