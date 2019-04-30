---
title: IActiveScriptSiteDebug32::GetApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: c71e33445db7745f71e374c586d079a9665776b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992491"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Retorna o objeto de aplicativo de depuração associado a este site de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppda`  
 [out] Ponteiro para o objeto de aplicativo de depuração associado com o site de script.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|O host não suporta diretamente de depuração.|  
  
## <a name="remarks"></a>Comentários  
 O `GetApplication` método fornece uma maneira para um host inteligente definir o objeto de aplicativo ao qual pertence cada script. Mecanismos de script devem tentar chamar esse método para obter o seu aplicativo de contenção e recorrer a `IProcessDebugManager::GetDefaultApplication` no caso de falha.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteDebug32 Interface](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)