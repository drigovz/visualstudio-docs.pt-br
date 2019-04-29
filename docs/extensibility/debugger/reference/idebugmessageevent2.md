---
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49224ad0018286fffd365857364bf1b37300788f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918846"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Essa interface é usada pelo mecanismo de depuração (DE) para enviar uma mensagem para o Visual Studio que requer uma resposta do usuário.

## <a name="syntax"></a>Sintaxe

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O DE implementa essa interface para enviar uma mensagem para o Visual Studio que requer uma resposta do usuário. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto como essa interface. Usa o SDM [QueryInterface](/cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface.

 A implementação dessa interface deve se comunicar a chamada do Visual Studio [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) para a Alemanha. Por exemplo, isso pode ser feito com uma mensagem publicada à mensagem do DE tratamento de thread ou o objeto que implementa essa interface pode conter uma referência para o DE e retornar a chamada para o DE com a resposta passada para `IDebugMessageEvent2::SetResponse`.

## <a name="notes-for-callers"></a>Observações para chamadores
 O DE cria e envia esse objeto de evento para exibir uma mensagem para o usuário que requer uma resposta. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando ele é anexado ao programa que está sendo depurado.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugMessageEvent2`.

|Método|Descrição|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Obtém a mensagem a ser exibida.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Define a resposta, se houver, da caixa de mensagem.|

## <a name="remarks"></a>Comentários
 O DE usará essa interface se ele requer uma resposta específica do usuário para uma mensagem específica. Por exemplo, se o DE uma mensagem de "Acesso negado" após uma tentativa de se conectar remotamente a um programa, o DE envia essa mensagem específica para o Visual Studio em um `IDebugMessageEvent2` eventos com o estilo de caixa de mensagem `MB_RETRYCANCEL`. Isso permite que o usuário tente novamente ou cancelar a operação de anexação.

 O DE Especifica como essa mensagem deve ser tratada pelo segue as convenções da função Win32 `MessageBox` (consulte [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) para obter detalhes).

 Use o [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) interface para enviar mensagens para o Visual Studio que não exigem uma resposta do usuário.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)