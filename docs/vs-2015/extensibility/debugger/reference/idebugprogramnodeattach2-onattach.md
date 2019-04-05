---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 845ec66215c5d999aaf3b5c9658bc0fb8e7295a7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926396"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Anexa ao programa associado ou adia o processo de anexação para o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidProgramId`  
 [in] `GUID` para atribuir ao programa associado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método não deve ser chamado. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado durante o processo de anexação, antes de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método é chamado. O `OnAttach` método pode executar o processo de anexação (nesse caso, esse método retorna `S_FALSE`) ou adiar o processo de anexação para o `IDebugEngine2::Attach` método (o `OnAttach` retorno do método `S_OK`). Em ambos os casos, o `OnAttach` método pode definir o `GUID` do programa que está sendo depurado a determinado `GUID`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
