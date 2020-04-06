---
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c47a920e99ece3fb0853e4e6a26dba3c8d0c45c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726023"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
Esta interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de depuração de sessão (SDM) para produzir uma seqüência.

## <a name="syntax"></a>Sintaxe

```
IDebugOutputStringEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O DE implementa esta interface para enviar uma seqüência de string para a janela **Saída** do IDE. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que esta interface. O SDM usa [queryInterface](/cpp/atl/queryinterface) para acessar a `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 O DE cria e envia esse objeto de evento para enviar uma seqüência de string sacada na janela **Saída.** O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é fornecida pelo SDM quando é anexada ao programa que está sendo depurado.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugOutputStringEvent2`mostra o método de .

|Método|Descrição|
|------------|-----------------|
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Recebe a mensagem exibivel.|

## <a name="remarks"></a>Comentários
 Por exemplo, em código não gerenciado, a seqüência de séries a ser originada `OutputDebugString` pode ser originada quando o programa que está sendo depurado envia uma seqüência para a função Win32. Esta seqüência é interceptada pelo DE e `IDebugOutputStringEvent2` enviada para o SDM como evento.

 Use [o IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) para enviar uma mensagem que exija uma resposta do usuário.

 Use [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) para enviar uma mensagem de erro que não exija uma resposta.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
