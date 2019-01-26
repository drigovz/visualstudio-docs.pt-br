---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 974466977995b866d70ad7e1619a6ae536886f6c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007601"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Essa interface representa uma posição no espaço de endereço do computador que executa o programa que está sendo depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DES) implementa essa interface para representar um endereço na memória.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) ou [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) retorna essa interface. Além disso, chamadas para [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) e [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) retornar novas cópias dessa interface depois que a operação aritmética apropriada foi aplicada.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugMemoryContext2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtém o nome de exibição de usuário para este contexto.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtém informações que descrevem neste contexto.|  
|[Adicionar](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Adiciona um valor especificado para o endereço do contexto atual para criar um novo contexto.|  
|[Subtração](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Subtrai um valor especificado do endereço do contexto atual para criar um novo contexto.|  
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compara dois contextos da maneira indicados pelo compara sinalizadores.|  
  
## <a name="remarks"></a>Comentários  
 Visual Studio **memória** janela chamadas [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) para obter o `IDebugMemoryContext2` interface que contém a expressão avaliada usada para o endereço de memória. Nesse contexto é então passado para [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) para especificar o endereço para ler ou gravar.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)