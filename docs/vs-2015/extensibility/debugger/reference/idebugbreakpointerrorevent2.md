---
title: IDebugBreakpointErrorEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22ad0a7e1b14b036239d7b6a5931badb5787b752
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684814"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface diz ao SDM (Gerenciador de depuração de sessão) que um ponto de interrupção pendente não pôde ser associado a um programa carregado, devido a um aviso ou erro.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O DE implementa essa interface como parte de seu suporte para pontos de interrupção. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que essa interface (o SDM usa [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para acessar a `IDebugEvent2` interface).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia este objeto DE evento quando um ponto de interrupção pendente não pode ser associado ao programa que está sendo depurado. O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornecida pelo SDM quando ele é anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugBreakpointErrorEvent2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Obtém a interface [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) que descreve o aviso ou erro.|  
  
## <a name="remarks"></a>Comentários  
 Sempre que um ponto de interrupção é associado, um evento é enviado para o SDM. Se o ponto de interrupção não puder ser associado, um `IDebugBreakpointErrorEvent2` será enviado; caso contrário, um [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) será enviado.  
  
 Por exemplo, quando a condição associada ao ponto de interrupção pendente falha ao analisar ou avaliar, um aviso é enviado de que o ponto de interrupção pendente não pode ser associado no momento. Isso pode ocorrer se o código para o ponto de interrupção ainda não tiver sido carregado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
