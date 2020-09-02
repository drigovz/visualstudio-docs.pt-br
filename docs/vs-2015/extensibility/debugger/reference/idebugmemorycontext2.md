---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f5a0533e2f7ce50dce7ccdf1285e4ab28a4b7a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146364"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface representa uma posição no espaço de endereço do computador que está executando o programa que está sendo depurado.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar um endereço na memória.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) ou [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) retorna essa interface. Além disso, as chamadas para [Adicionar](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) e [subtrair](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) retornam novas cópias dessa interface após a aplicação da operação aritmética apropriada.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugMemoryContext2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtém o nome da exibição do usuário para este contexto.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtém informações que descrevem esse contexto.|  
|[Adicionar](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Adiciona um valor especificado ao endereço do contexto atual para criar um novo contexto.|  
|[Subtrair](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Subtrai um valor especificado do endereço do contexto atual para criar um novo contexto.|  
|[Comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compara dois contextos da maneira indicada por sinalizadores de comparação.|  
  
## <a name="remarks"></a>Comentários  
 A janela de **memória** do Visual Studio chama [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) para obter a `IDebugMemoryContext2` interface que contém a expressão avaliada usada para o endereço de memória. Esse contexto é passado para [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) e [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) para especificar o endereço a ser lido ou gravado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
