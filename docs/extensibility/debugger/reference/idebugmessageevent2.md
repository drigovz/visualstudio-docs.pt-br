---
title: IDebugMessageEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2
helpviewer_keywords:
- IDebugMessageEvent2 interface
ms.assetid: a9ff3d00-e9ac-4cd6-bda9-584a4815aff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180162988cbb09f98b7fc2e8f33f6b5d0ed322ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727366"
---
# <a name="idebugmessageevent2"></a>IDebugMessageEvent2
Esta interface é usada pelo mecanismo de depuração (DE) para enviar uma mensagem ao Visual Studio que requer uma resposta do usuário.

## <a name="syntax"></a>Sintaxe

```
IDebugMessageEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O DE implementa esta interface para enviar uma mensagem ao Visual Studio que requer uma resposta do usuário. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que esta interface. O SDM usa [queryInterface](/cpp/atl/queryinterface) para acessar a `IDebugEvent2` interface.

 A implementação desta interface deve comunicar a chamada do Visual Studio de [SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md) para o DE. Por exemplo, isso pode ser feito com uma mensagem postada no segmento de manipulação de mensagens do DE, ou o objeto `IDebugMessageEvent2::SetResponse`que implementa essa interface pode conter uma referência ao DE e chamar de volta para o DE com a resposta transmitida para .

## <a name="notes-for-callers"></a>Observações para chamadores
 O DE cria e envia este objeto de evento para exibir uma mensagem ao usuário que requer uma resposta. O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é fornecida pelo SDM quando é anexada ao programa que está sendo depurado.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugMessageEvent2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)|Faz com que a mensagem seja exibida.|
|[SetResponse](../../../extensibility/debugger/reference/idebugmessageevent2-setresponse.md)|Define a resposta, se houver, da caixa de mensagens.|

## <a name="remarks"></a>Comentários
 O DE usará esta interface se exigir uma resposta específica do usuário para uma mensagem específica. Por exemplo, se o DE receber uma mensagem "Acesso negado" após uma tentativa de anexar remotamente a um programa, o DE envia esta mensagem específica para o Visual Studio em um `IDebugMessageEvent2` evento com o estilo `MB_RETRYCANCEL`caixa de mensagem . Isso permite que o usuário tente novamente ou cancele a operação de conexão.

 O DE especifica como essa mensagem deve ser tratada seguindo as `MessageBox` convenções da função Win32 (consulte [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) para obter detalhes).

 Use a interface [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) para enviar mensagens ao Visual Studio que não exijam uma resposta do usuário.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
