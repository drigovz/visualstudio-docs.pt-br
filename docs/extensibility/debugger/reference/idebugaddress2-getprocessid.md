---
title: IDebugAddress2::GetProcessID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79cff8c6e0dea1ae4b954a4592debdb3ba8331c2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001128"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Recupera a ID do processo que possui o objeto representado por este [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```csharp  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProcID`  
 [out] A ID de processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)