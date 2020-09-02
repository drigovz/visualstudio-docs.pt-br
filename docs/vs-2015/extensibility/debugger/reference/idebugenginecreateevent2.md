---
title: IDebugEngineCreateEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8878bbbfd7c2cef6f23fd433e46985db60ab34f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195706"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

O mecanismo de depuração (DE) envia essa interface para o SDM (Gerenciador de depuração de sessão) quando uma instância do de é criada.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngineCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O DE implementa essa interface como parte de suas operações normais. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que essa interface (o SDM usa o `QueryInterface` método para acessar a `IDebugEvent2` interface).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento quando o DE foi instanciado. O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é fornecida pelo SDM quando anexada ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugEngineCreateEvent2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Recupera o objeto que representa o mecanismo DE depuração recém-criado (DE).|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
