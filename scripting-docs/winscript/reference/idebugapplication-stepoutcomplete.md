---
title: 'IDebugApplication:: StepOutComplete | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f50d7e8a8936e52f4177450e7d163c4cfeaa55df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571043"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Notifica o Gerenciador de depuração de processo que um mecanismo de linguagem em modo de etapa única está prestes a retornar ao chamador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Os mecanismos de linguagem chamam esse método em modo de etapa única antes de retornar ao chamador. O Gerenciador de depuração de processos usa essa oportunidade para notificar todos os outros mecanismos de script que eles devem interromper na primeira oportunidade. Essa técnica é a forma como os modos de etapa em idioma cruzado são implementados.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplication Interface](../../winscript/reference/idebugapplication-interface.md)