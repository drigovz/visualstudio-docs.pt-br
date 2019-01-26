---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cbce46afaa6227f5d15720be8aebd4c60f5f236
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015489"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Esse método permite que o fornecedor de porta exibir um aviso antes do usuário anexar a um processo que não é seguro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Os valores de retorno são da seguinte maneira:  
  
-   `S_OK`: Anexar a processo é seguro e nenhuma caixa de diálogo de aviso é exibida.  
  
-   `S_FALSE`: Anexando poderia ser um problema de segurança e uma caixa de diálogo com um aviso é exibida.  
  
-   `FAILURE`: Falha na anexação ao processo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)