---
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 836b971963587aa89440c6e023ee255612d2a087
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923531"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`IDebugProcessSecurity` é implementado por um fornecedor de porta para avisar o usuário que é seguro anexando ao processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugProcessSecurity`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtém o nome de usuário do fornecedor de porta.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Avisa o usuário anexar ao processo de depuração é seguro.|  
  
## <a name="remarks"></a>Comentários  
 Implemente essa interface para mostrar um aviso e permitir que o usuário cancele se o processo ao qual você está anexando pode ser considerado não seguro.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Portas](../../../extensibility/debugger/ports.md)   
 [Fornecedores de porta](../../../extensibility/debugger/port-suppliers.md)   
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
