---
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83f70a9fe027f004ef3829827ba8af40f7fb72e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340319"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Essa interface descreve uma porta. Esta descrição é usada para adicionar a porta para um fornecedor de porta.

## <a name="syntax"></a>Sintaxe

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Normalmente, o Visual Studio implementa essa interface no processo de obtenção de uma porta de depuração de um fornecedor de porta.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é passada para [adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) para criar uma porta de depuração. Uma chamada para [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) retorna essa interface, que representa a solicitação usada para criar a porta em primeiro lugar.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugPortRequest2`.

|Método|Descrição|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtém o nome da porta para criar.|

## <a name="remarks"></a>Comentários
 Normalmente, um mecanismo de depuração não interage com um fornecedor de porta e não terá nenhum uso para essa interface.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)