---
title: 'IDebugProgram2:: GetProcess | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 366b35a90eb44496dc1b50cd85dfa0fef5656ddb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148663"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtenha o processo em que este programa está sendo executado.  
  
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
 fora Retorna a interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa o processo.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A menos que um mecanismo DE depuração (DE) implemente a interface [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , a implementação de de desse método sempre deve retornar `E_NOTIMPL` porque um de não pode determinar qual processo está sendo executado e, portanto, não pode atender a uma implementação desse método.  
  
 Implementar a `IDebugEngineLaunch2` interface significa que o de deve saber como criar um processo; portanto, a implementação de de da interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) é capaz de saber em qual processo ele está sendo executado.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
