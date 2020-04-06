---
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 163718fda344ba5f3f44ef630b4eba3e5613dc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724790"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Esta interface descreve uma porta. Esta descrição é usada para adicionar a porta a um fornecedor de porta.

## <a name="syntax"></a>Sintaxe

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O Visual Studio normalmente implementa essa interface no processo de obter uma porta de depuração de um fornecedor de porta.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é passada para [o AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) para criar uma porta de depuração. Uma chamada para [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) retorna esta interface, representando a solicitação usada para criar a porta em primeiro lugar.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugPortRequest2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Recebe o nome da porta para criar.|

## <a name="remarks"></a>Comentários
 Um mecanismo de depuração normalmente não interage com um fornecedor de porta e não terá uso para esta interface.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
