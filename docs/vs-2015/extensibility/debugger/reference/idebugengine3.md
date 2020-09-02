---
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e43da0b05062c6c7b1c4d3cfe771ff0b93f83a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195787"
---
# <a name="idebugengine3"></a>IDebugEngine3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Representa um único mecanismo DE depuração (DE) que controla a depuração de um ou mais módulos.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 Essa interface é implementada por um DE um personalizado (se oferecer suporte a símbolos) para habilitar o estado JustMyCode. Essa interface deve ser implementada pelo DE se oferecer suporte a símbolos e JustMyCode.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é chamada pelo SDM (Gerenciador de depuração de sessão) para passar as opções do usuário para locais dos quais carregar símbolos. Também é chamado para definir o GUID do mecanismo quando ele é instanciado (esse GUID é baseado nas métricas do momento do registro do mecanismo). O SDM também chama essa interface para definir o estado JustMyCode e definir todas as exceções conhecidas pelo depurador para um estado especificado.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 Além dos métodos herdados de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), a `IDebugEngine3` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Define o caminho ou caminhos que o deve usar para procurar símbolos de depuração.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carrega os símbolos para todos os módulos que ainda não tinham seus símbolos carregados.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Informa o sobre as informações de JustMyCode.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Define o GUID de da métrica.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Defina todas as exceções atualmente pendentes para um estado especificado.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
