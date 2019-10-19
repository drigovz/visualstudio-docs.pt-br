---
title: Constantes DEBUG_TEXT | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: facbdc1258b3fca72a239d9d5cc41772cf577f13
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577363"
---
# <a name="debug_text-constants"></a>Constantes DEBUG_TEXT
Usado durante [IDebugExpressionContext::P arselanguagetext](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION DWORD|0x00000001|Indica que o texto é uma expressão, em oposição a uma instrução. Esse sinalizador pode afetar a maneira como o texto é analisado por alguns idiomas.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Se um valor de retorno estiver disponível, ele será usado pelo chamador.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Não permitir efeitos colaterais. Se esse sinalizador for definido, a avaliação da expressão deverá alterar nenhum estado de tempo de execução.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Permitir pontos de interrupção durante a avaliação do texto. Se esse sinalizador não for definido, os pontos de interrupção serão ignorados durante a avaliação do texto.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Permitir relatórios de erros durante a avaliação do texto. Se esse sinalizador não for definido, os erros não serão relatados ao host durante a avaliação.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica que a expressão deve ser avaliada para um contexto de código em vez de executar a própria expressão.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)