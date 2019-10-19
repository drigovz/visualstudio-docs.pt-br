---
title: 'IMachineDebugManagerEvents:: onRemoveApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerEvents.onRemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerEvents::onRemoveApplication
ms.assetid: 3ba71bd8-fd69-4a41-99c6-c736c416f227
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b50d91a75a8f251ad04b456b179fdd0ba0d1dc32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571483"
---
# <a name="imachinedebugmanagereventsonremoveapplication"></a>IMachineDebugManagerEvents::onRemoveApplication
Manipula o evento quando um aplicativo é removido da lista de aplicativos em execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT onRemoveApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pda`  
 no Aplicativo que foi removido da lista de aplicativos em execução.  
  
 `dwAppCookie`  
 no O cookie fornecido quando o aplicativo foi adicionado da lista de aplicativos.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método indica que um aplicativo foi removido da lista de aplicativos em execução.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IMachineDebugManagerEvents](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
 [IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)