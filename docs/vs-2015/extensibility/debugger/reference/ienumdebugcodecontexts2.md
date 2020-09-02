---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f36da19e6bc47d70010dd96a26256537803ccb29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551612"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface enumera os contextos de código associados à sessão de depuração ou com um programa ou documento específico.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar uma lista de contextos de código para uma determinada posição de texto em um programa ou uma lista de contextos de código para um determinado contexto de documento.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chame [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para obter essa interface representando uma lista de contextos de código para uma posição de texto específica no documento de origem de um programa.  
  
 Chame [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) para obter essa interface representando uma lista de todos os contextos de código em um documento de origem específico.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugCodeContexts2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[Próximo](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera um número especificado de contextos de código em uma sequência de enumeração.|  
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Ignora um número especificado de contextos de código em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtém o número de contextos de código em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 O Visual Studio chama [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para popular uma lista de contextos de código que o usuário pode escolher ao definir a próxima instrução ou mostrar a desmontagem de um arquivo de origem. Vários contextos de código podem ocorrer, por exemplo, quando há várias instâncias de um modelo em estilo C++.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
