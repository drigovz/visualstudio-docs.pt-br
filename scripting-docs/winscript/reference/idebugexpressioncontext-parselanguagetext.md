---
title: IDebugExpressionContext::P arseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573159"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Cria uma expressão de depuração para o texto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrCode`  
 no Fornece o texto da expressão ou da (s) instrução (ões).  
  
 `nRadix`  
 no Radix a ser usado.  
  
 `pstrDelimiter`  
 no O delimitador de bloco de fim de script. Quando `pstrCode` é analisada a partir de um fluxo de texto, o host geralmente usa um delimitador, como duas aspas simples (' '), para detectar o final do bloco de script. Esse parâmetro especifica o delimitador usado pelo host, permitindo que o mecanismo de script forneça algum pré-processamento primitivo condicional (por exemplo, substituindo uma aspa simples ['] por duas aspas simples para uso como um delimitador). Exatamente como (e se) o mecanismo de script usa essas informações depende do mecanismo de script. Defina esse parâmetro como `NULL` se o host não usou um delimitador para marcar o final do bloco de script.  
  
 `dwFlags`  
 no Combinação dos seguintes sinalizadores de texto de depuração:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica que o texto é uma expressão, em oposição a uma instrução. Esse sinalizador pode afetar a maneira como o texto é analisado por alguns idiomas.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Se um valor de retorno estiver disponível, ele será usado pelo chamador.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Não permitir efeitos colaterais. Se esse sinalizador for definido, a avaliação da expressão deverá alterar nenhum estado de tempo de execução.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Permite pontos de interrupção durante a avaliação do texto. Se esse sinalizador não for definido, os pontos de interrupção serão ignorados durante a avaliação do texto.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Permite relatórios de erros durante a avaliação do texto. Se esse sinalizador não for definido, os erros não serão relatados ao host durante a avaliação.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica que a expressão deve ser avaliada para um contexto de código em vez de executar a própria expressão|  
  
 `ppe`  
 fora Retorna a expressão de depuração para o texto especificado.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método cria uma expressão de depuração para o texto especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)