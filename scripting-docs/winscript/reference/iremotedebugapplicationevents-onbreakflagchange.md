---
title: IRemoteDebugApplicationEvents::OnBreakFlagChange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnBreakFlagChange
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnBreakFlagChange
ms.assetid: 25684454-a0d8-47e0-85f5-2217069a9f45
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb19b6cfc423a1305276441305ef854c70f2d896
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150468"
---
# <a name="iremotedebugapplicationeventsonbreakflagchange"></a>IRemoteDebugApplicationEvents::OnBreakFlagChange
Manipula um evento quando alterar os sinalizadores de quebra.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT OnBreakFlagChange(  
   APPBREAKFLAGS                   abf,  
   IRemoteDebugApplicationThread*  prdatSteppingThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `abf`  
 [in] Os sinalizadores de interrupção atual para o aplicativo.  
  
 `prdatSteppingThread`  
 [in] O thread em execução no momento.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método manipula o evento quando o sinalizador de interrupção são alterados.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)   
 [APPBREAKFLAGS Enumeration](../../winscript/reference/appbreakflags-enumeration.md)