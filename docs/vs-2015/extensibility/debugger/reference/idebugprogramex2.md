---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d3abc956d736f5c9273134b41c0fc9c2dc7db62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688937"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface permite que o SDM (Gerenciador de depuração de sessão) se conecte a um programa e obtenha o nó de programa associado a um programa.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 Um fornecedor de porta personalizado implementa essa interface no mesmo objeto que a interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) para permitir que o SDM anexe a um programa enquanto, ao mesmo tempo, permite que o fornecedor de porta acompanhe todas as sessões anexadas ao programa. O fornecedor da porta personalizada pode implementar essa interface se escolher.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O SDM chama [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) em uma `IDebugProgram2` interface para obter essa interface para controlar as sessões que foram anexadas a programas.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugProgramEx2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Anexa um programa a uma sessão.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtém o nó de programa associado a um programa.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é privada entre o SDM e o programa.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Portpriv. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
