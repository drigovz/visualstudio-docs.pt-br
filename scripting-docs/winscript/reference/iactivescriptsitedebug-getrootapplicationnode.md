---
title: IActiveScriptSiteDebug::GetRootApplicationNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetRootApplicationNode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetRootApplicationNode
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 18e603289931115bcaac4d6bb7707b7886f506d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992471"
---
# <a name="iactivescriptsitedebuggetrootapplicationnode"></a>IActiveScriptSiteDebug::GetRootApplicationNode
Obtém o nó de aplicativo sob a qual script documentos devem ser adicionados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppdanRoot`  
 [out] O nó de aplicativo de depuração que mantém os documentos de script. Pode ser `NULL`.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o nó do aplicativo sob a qual os documentos de script devem ser adicionados. O método pode retornar `NULL` para `ppdanRoot` se documentos de script devem ser de nível superior.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptSiteDebug Interface](../../winscript/reference/iactivescriptsitedebug-interface.md)