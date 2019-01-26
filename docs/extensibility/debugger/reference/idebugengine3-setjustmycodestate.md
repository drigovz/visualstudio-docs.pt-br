---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180ef79d488585aa50eb19da6924c642340d0aa7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925988"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Esse método informa o mecanismo de depuração sobre as informações de estado de JustMyCode.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fUpdate`  
 [in] Diferente de zero (`TRUE`) para atualizar as informações atuais, zero (`FALSE`) para redefinir todas as informações (ignorando tudo definido anteriormente).  
  
 `dwModules`  
 [in] Número de estruturas de informações em `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Matriz de [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) estruturas para usar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 JustMyCode é o conceito de depuração somente o código que pertence a um usuário e ignorando todo o código intermediário, como o código do sistema — mesmo se o código-fonte está disponível para esse código do sistema.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)