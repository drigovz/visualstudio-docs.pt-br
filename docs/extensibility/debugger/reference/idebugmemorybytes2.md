---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2a9434f7464d4c13d0c4085a3ad195ba8b1bd2f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007575"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Essa interface representa bytes de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DES) implementa essa interface para representar os bytes na memória.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) retorna essa interface para fornecer acesso à memória do sistema. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) e [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) retornar essa interface para fornecer acesso aos bytes do objeto.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugMemoryBytes2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Lê uma sequência de bytes, começando em um determinado local.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Grava `dwCount` bytes, começando em `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Obtém o tamanho, em bytes, da memória representado por esta interface.|  
  
## <a name="remarks"></a>Comentários  
 Para propriedades, uma [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface que representa uma matriz fornece um `IDebugMemoryBytes2` interface para acessar os valores na matriz.  
  
 Visual Studio **modo de exibição de memória** chamadas [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) para recuperar um `IDebugMemoryBytes2` interface para acessar a memória do sistema. O endereço a ser acessado é obtido ao analisar a expressão inserida como um endereço para a exibição de memória e, em seguida, avaliar a expressão analisada usando [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obter um `IDebugProperty2` interface. Uma chamada para [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) retorna o [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que descreve o endereço de memória. Nesse contexto de memória é então passado para [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)