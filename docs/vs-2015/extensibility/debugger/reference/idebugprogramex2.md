---
title: IDebugProgramEx2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb8009203a4d97ef5ecce37751495300b3b9248c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49241509"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface permite que a sessão de depuração SDM (Gerenciador) anexar a um programa e colocar o nó de programa associado com um programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface no mesmo objeto como o [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface para permitir que o SDM anexar a um programa enquanto ao mesmo tempo permitindo que o fornecedor de porta acompanhar todas as sessões anexado a programa. O fornecedor de porta personalizada pode implementar essa interface se optar por.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 As chamadas SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) em um `IDebugProgram2` interface para obter essa interface para rastrear as sessões que anexados aos programas.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugProgramEx2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Anexar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Anexa um programa para uma sessão.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtém o nó de programa associado com um programa.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é privada entre o SDM e o programa.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

