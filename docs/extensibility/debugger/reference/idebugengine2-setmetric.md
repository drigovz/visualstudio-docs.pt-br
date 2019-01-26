---
title: IDebugEngine2::SetMetric | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f50732b6e271ac3bf51eb2cde4549cd7396fb4b8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998190"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Esse método define um valor de registro, conhecido como uma métrica.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```csharp  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszMetric`  
 [in] O nome da métrica.  
  
 `varValue`  
 [in] Especifica o valor da métrica.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Uma métrica é um valor do registro usado para alterar o comportamento de um mecanismo de depuração ou para anunciar a funcionalidade com suporte. Esse método pode encaminhar a chamada para o formulário apropriado do [auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) função, `SetMetric`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)