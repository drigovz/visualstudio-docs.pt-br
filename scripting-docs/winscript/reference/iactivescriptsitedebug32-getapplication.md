---
title: 'IActiveScriptSiteDebug32:: GetApplication | Microsoft Docs'
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
ms.openlocfilehash: 93c4a8fe6e5c2aac8b07f896810dcd03060b46d0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572189"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32:: GetApplication
Retorna o objeto de aplicativo de depuração associado a este site de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppda`  
 fora Ponteiro para o objeto de aplicativo de depuração associado ao site de script.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|O host não dá suporte diretamente à depuração.|  
  
## <a name="remarks"></a>Comentários  
 O método `GetApplication` fornece uma maneira para um host inteligente definir o objeto de aplicativo ao qual cada script pertence. Os mecanismos de script devem tentar chamar esse método para obter seu aplicativo de contenção e recorrer a `IProcessDebugManager::GetDefaultApplication` se isso falhar.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)