---
title: IDebugProcessEx2::Detach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b79f1f80f9b6849c37fc9b6c4c8669f1397f0227
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "62538129"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método informa o processo que uma sessão não está depurando o processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
