---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f364b6aa622bf9c7481d61e7646e955cebe00933
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695397"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

O mecanismo de depuração (DE) envia essa interface para o SDM (Gerenciador de depuração de sessão) quando uma exceção é lançada no programa que está sendo executado no momento.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O DE implementa essa interface para relatar que ocorreu uma exceção no programa que está sendo depurado. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que essa interface. O SDM usa [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para acessar a `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia este objeto de evento para relatar uma exceção. O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é fornecida pelo SDM quando anexada ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugExceptionEvent2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Obtém informações detalhadas sobre a exceção que disparou este evento.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtém uma descrição legível para a exceção gerada que disparou este evento.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Determina se o mecanismo de depuração (DE) dá suporte à opção de passar essa exceção para o programa que está sendo depurado quando a execução é retomada.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Especifica se a exceção deve ser passada para o programa que está sendo depurado quando a execução é retomada ou se a exceção deve ser descartada.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Comentários  
 Antes de enviar o evento, o DE verifica para ver se esse evento DE exceção foi designado como uma exceção de primeira chance ou de segunda chance por uma chamada anterior para [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Se tiver sido designado para ser uma exceção de primeira chance, o `IDebugExceptionEvent2` evento será enviado para o SDM. Caso contrário, o DE dá ao aplicativo uma chance de lidar com a exceção. Se nenhum manipulador de exceção for fornecido, e se a exceção tiver sido designada como uma exceção de segunda chance, o `IDebugExceptionEvent2` evento será enviado para o SDM. Caso contrário, o DE retoma a execução do programa e o sistema operacional ou o tempo de execução trata a exceção.  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Setexceptioning](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
