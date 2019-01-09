---
title: IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteInterruptPoll.QueryContinue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteInterruptPoll::QueryContinue
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b43211dca57a404d5625cfc2d7ede67a70a0a40
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087978"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Permite que um host especificar um script deve ser interrompido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|A chamada foi bem-sucedida e o host permite que o script continue em execução.|  
|`S_FALSE`|A chamada foi bem-sucedida e o host solicita que o script Encerrar.|  
  
## <a name="remarks"></a>Comentários  
 O script hospedado deve ser terminada, a menos que o valor de retorno de `QueryContinue` método é `S_OK`. Um valor de retorno `S_FALSE` indica que o host solicita explicitamente que o script Encerrar.  
  
 Um host de vários threads pode usar o `IActiveScript::InterruptScriptThread` método para encerrar um script.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)