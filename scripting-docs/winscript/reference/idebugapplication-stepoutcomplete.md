---
title: IDebugApplication::StepOutComplete | Microsoft Docs
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
ms.openlocfilehash: 04f8ecfb835199afa0a60f3fde3c8fbdc8812240
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990610"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Notifica o Gerenciador de depuração do processo que um mecanismo de linguagem no modo passo a passo está prestes a retornar a seu chamador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Mecanismos de linguagem chamar este método no modo de etapa única antes que eles retornarem ao seu chamador. O Gerenciador de depuração do processo usa esta oportunidade para notificar todos os outros mecanismos de script deve ser interrompido na primeira oportunidade. Essa técnica é a etapa de qualquer idioma como modos são implementados.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplication Interface](../../winscript/reference/idebugapplication-interface.md)