---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720924"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Essa interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de depuração de sessão (SDM) quando cria uma propriedade associada a um documento específico.

## <a name="syntax"></a>Sintaxe

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O DE implementa essa interface para informar que uma propriedade foi criada. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que esta interface. O SDM usa [queryInterface](/cpp/atl/queryinterface) para acessar a `IDebugEvent2` interface. Essa interface é implementada se o DE criou uma propriedade associada a um script que foi carregado ou criado e se esse script precisa aparecer no IDE.

## <a name="notes-for-callers"></a>Observações para chamadores
 O DE cria e envia este objeto de evento para informar que uma propriedade foi criada. O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é fornecida pelo SDM quando é anexada ao programa que está sendo depurado.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugPropertyCreateEvent2` mostra o método da interface.

|Método|Descrição|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Fica com a nova propriedade.|

## <a name="remarks"></a>Comentários
 Se uma propriedade tiver um documento ou script específico associado a ele, o DE pode enviar esse evento para o SDM, a fim de atualizar a janela **Documentos de script** com o nome do documento. O SDM chamará [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) com o argumento `guidDocument` de recuperar um `VARIANT` ponteiro [IUnknown.](/cpp/atl/iunknown) O SDM chamará [QueryInterface](/cpp/atl/queryinterface) neste ponteiro para recuperar a interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) que é usada para atualizar a janela **Documentos de script.**

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
