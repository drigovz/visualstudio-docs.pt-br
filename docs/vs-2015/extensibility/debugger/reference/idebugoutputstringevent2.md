---
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa62889e2af87325c124fa8e8af1cd9cc4cff253
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922971"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de sessão de depuração (SDM) para uma cadeia de caracteres de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para enviar uma cadeia de caracteres para o **saída** janela do IDE. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto como essa interface. Usa o SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para acessar o `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento para enviar uma cadeia de caracteres para o **saída** janela. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando ele é anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra o método de `IDebugOutputStringEvent2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Obtém a mensagem que pode ser exibida.|  
  
## <a name="remarks"></a>Comentários  
 Por exemplo, no código não gerenciado, a cadeia de caracteres de saída pode se originar quando o programa que está sendo depurado envia uma cadeia de caracteres para o Win32 `OutputDebugString` função. Essa cadeia de caracteres é interceptada por DE e enviada ao SDM como o `IDebugOutputStringEvent2` eventos.  
  
 Use [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) para enviar uma mensagem que exige uma resposta do usuário.  
  
 Use [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) para enviar uma mensagem de erro que não requer uma resposta.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
