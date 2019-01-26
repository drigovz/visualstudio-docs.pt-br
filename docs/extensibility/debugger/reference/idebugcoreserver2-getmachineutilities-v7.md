---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 977c7157ade60afe57b3564934319a34d140d81c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027653"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Esse método obtém os utilitários de máquina para um servidor.  
  
> [!NOTE]
>  Este método é obsoleto: não use ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] sempre retorna `E_NOTIMPL` se esse método é chamado). Ele é retido por razões históricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppUtil`  
 [out] Retorna um `IDebugMDMUtil2_V7` interface que representa as informações de utilitários do computador.  
  
## <a name="return-value"></a>Valor de retorno  
 Sempre retorna `E_NOTIMPL`, indicando que o método não está implementado.  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] sempre retorna `E_NOTIMPL` se esse método é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)