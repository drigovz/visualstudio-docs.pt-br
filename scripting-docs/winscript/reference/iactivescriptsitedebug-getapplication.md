---
title: 'IActiveScriptSiteDebug:: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2ad81e3b6b1707f5a23271cf0abe3832266c07f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570129"
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
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
 @No__t_1 de [interface IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)  
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)