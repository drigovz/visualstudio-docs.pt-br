---
title: IDebugProgram2::GetProcess | Microsoft Docs
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
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 373a3f316d6eb6c034fc5219f04e9f1b22c2a9f0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865746"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtenha o que este programa está em execução no processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppProcess`  
 [out] Retorna o [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interface que representa o processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A menos que um mecanismo de depuração (DES) implementa o [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interface, a implementação do desse método deve retornar sempre `E_NOTIMPL` porque a DE não pode determinar qual processo está em execução em e, portanto, não é possível atender a uma implementação deste método.  
  
 Implementando o `IDebugEngineLaunch2` interface significa que o DE deve saber como criar um processo; portanto, a implementação do do [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface é capaz de saber a qual processo está executando no.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

