---
title: IProcessDebugManager::RemoveApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.RemoveApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::RemoveApplication
ms.assetid: 334e869d-81ae-4d30-9e89-89763ad4f184
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c163f756e426cab9ce36c1c8343b142bf76aafd6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086509"
---
# <a name="iprocessdebugmanagerremoveapplication"></a>IProcessDebugManager::RemoveApplication
Remove um aplicativo de execução de lista de aplicativos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwAppCookie`  
 [in] O cookie fornecido pelo `IProcessDebugManager::AddApplication` quando o aplicativo foi adicionado à lista de aplicativos.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método Remove um aplicativo de execução de lista de aplicativos.  
  
## <a name="see-also"></a>Consulte também  
 [Iprocessdebugmanager:: Addapplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)   
 [Interface IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)