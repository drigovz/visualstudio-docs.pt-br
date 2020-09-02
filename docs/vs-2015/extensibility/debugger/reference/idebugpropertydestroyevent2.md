---
title: IDebugPropertyDestroyEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 034040ecd8df3368f53cb7a3bf99197e962e2b56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702300"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface é enviada pelo mecanismo de depuração (DE) para o SDM (Gerenciador de depuração de sessão) quando uma propriedade associada a um documento específico está prestes a ser destruída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPropertyDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O DE implementa essa interface para relatar que uma propriedade foi destruída. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que essa interface. O SDM usa [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para acessar a `IDebugEvent2` interface. Essa interface é implementada se a DE já tiver criado uma propriedade associada a um script; a destruição da propriedade Remove o script associado do IDE.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia este objeto de evento para relatar que uma propriedade foi destruída. O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é fornecida pelo SDM quando ele é anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra o método de `IDebugPropertyDestroyEvent2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Obtém a propriedade a ser destruída.|  
  
## <a name="remarks"></a>Comentários  
 Consulte os comentários para [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) para obter detalhes sobre por que esses eventos são usados.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
