---
title: IDebugProgram2::GetProgramId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67a132250d036be11c4b7db2f2352b1d6d86793b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938023"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Obtém um GUID para este programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```csharp  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pguidProgramId`  
 [out] Retorna o `GUID` para este programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um mecanismo de depuração (DES) deve retornar o identificador de programa originalmente passado para o [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) ou [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) métodos. Isso permite a identificação do programa em depurador componentes.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)