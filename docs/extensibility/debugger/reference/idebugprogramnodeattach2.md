---
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85f5e63c9b41bae3066a6585a9e3e96fd9aa0ce4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989816"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Permite que um nó de programa ser notificado de uma tentativa de anexar ao programa associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada na mesma classe que implementa o [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface para receber a notificação de uma operação de anexação e oferecem uma oportunidade de cancelar a operação de anexação.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Obtenha essa interface por meio da chamada a `QueryInterface` método em um [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objeto. O [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método deve ser chamado antes do [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método para permitir que o nó de programa para interromper o processo de anexação.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Anexa ao programa associado ou adia o processo de anexação para o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é a alternativa preferida para preteridas [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) método. Todos os mecanismos de depuração são sempre carregados com o `CoCreateInstance` de função, ou seja, eles são instanciados fora do espaço de endereço do programa que está sendo depurado.  
  
 Se uma implementação anterior da `IDebugProgramNode2::Attach_V7` método era simplesmente definindo o `GUID` do programa que está sendo depurado, em seguida, somente os [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método precisa ser implementado.  
  
 Se uma implementação anterior da `IDebugProgramNode2::Attach_V7` método usado a interface de retorno de chamada que foi fornecida, em seguida, essa funcionalidade precisa ser movidos para uma implementação do [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método e o `IDebugProgramNodeAttach2` interface não a serem implementadas.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)