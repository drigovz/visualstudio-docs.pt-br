---
title: IDebugProcessEx2::Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fbeb303b925cdbe6ca7e96c56fe58a7fc203ea8e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839064"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
Esse método informa o processo que uma sessão não está depurando o processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pSession`  
 [in] Um valor que identifica exclusivamente a sessão para desanexar esse processo de.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A interface passado `pSession` é para ser tratada apenas como um cookie, um valor que identifica exclusivamente o Gerenciador de sessão de depuração que originalmente anexado a esse processo; nenhum dos métodos na interface fornecida é funcional.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)