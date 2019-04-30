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
ms.openlocfilehash: 2342555c4ee92b403aa01cc0ca15bb805f2b002e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955244"
---
# <a name="debugtext-constants"></a>Constantes DEBUG_TEXT
Usado durante [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica que o texto é uma expressão em vez de uma instrução. Este sinalizador pode afetar a maneira na qual o texto é analisado por alguns idiomas.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Se um valor de retorno estiver disponível, ele será usado pelo chamador.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Não permita que os efeitos colaterais. Se esse sinalizador estiver definido, a avaliação da expressão não deve alterar nenhum estado de tempo de execução.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Permitir que os pontos de interrupção durante a avaliação do texto. Se este sinalizador não for definido, os pontos de interrupção serão ignorados durante a avaliação do texto.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Permitir que os relatórios de erros durante a avaliação do texto. Se este sinalizador não for definido, erros serão não relatados ao host durante a avaliação.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica que a expressão será avaliada para um contexto de código em vez de executar a expressão em si.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)