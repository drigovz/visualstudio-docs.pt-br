---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838702"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método obtém os utilitários de máquina para um servidor.  
  
> [!NOTE]
> Este método é obsoleto: não use ( [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] sempre retorna `E_NOTIMPL` se esse método for chamado). Ele é retido por motivos históricos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 fora Retorna uma `IDebugMDMUtil2_V7` interface que representa as informações de utilitários de computador.  
  
## <a name="return-value"></a>Valor Retornado  
 Sempre retorna `E_NOTIMPL` , indicando que o método não está implementado.  
  
## <a name="remarks"></a>Comentários  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] sempre retorna `E_NOTIMPL` se esse método for chamado.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
