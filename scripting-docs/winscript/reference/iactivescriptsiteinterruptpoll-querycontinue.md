---
title: 'IActiveScriptSiteInterruptPoll:: QueryContinue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 7ce2ad61b54dce510035dd8e97d0dfb2accbf7a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572230"
---
# <a name="iactivescriptsiteinterruptpollquerycontinue"></a>IActiveScriptSiteInterruptPoll::QueryContinue
Permite que um host especifique que um script deve ser encerrado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT QueryContinue();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|A chamada foi bem-sucedida e o host permite que o script continue em execução.|  
|`S_FALSE`|A chamada foi bem-sucedida e o host solicita que o script seja encerrado.|  
  
## <a name="remarks"></a>Comentários  
 O script hospedado deve terminar, a menos que o valor de retorno do método de `QueryContinue` seja `S_OK`. Um valor de retorno de `S_FALSE` indica que o host solicita explicitamente que o script seja encerrado.  
  
 Um host multithread pode usar o método `IActiveScript::InterruptScriptThread` para encerrar um script.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptSiteInterruptPoll](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)  
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)