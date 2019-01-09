---
title: IDebugExpressionContext::ParseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a55dc9ae2ae92a76c2b426d1f36949573b37a265
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087718"
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
 [in] Fornece o texto da expressão ou comando (s).  
  
 `nRadix`  
 [in] Raiz a ser usada.  
  
 `pstrDelimiter`  
 [in] O delimitador de fim do bloco de script. Quando `pstrCode` é analisado de um fluxo de texto, o host normalmente usa um delimitador, como duas aspas ("), para detectar o fim do bloco de script. Esse parâmetro especifica o delimitador que o host usou, permitindo que o mecanismo de script forneça algum pré-processamento primitivo condicional (por exemplo, substituindo uma aspa simples ['] por duas aspas simples para uso como um delimitador). Exatamente como (e se) o mecanismo de script usa essas informações dependem o mecanismo de script. Definir esse parâmetro como `NULL` se o host não usou um delimitador para marcar o fim do bloco de script.  
  
 `dwFlags`  
 [in] Combinação dos seguintes sinalizadores de texto de depuração:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Indica que o texto é uma expressão em vez de uma instrução. Este sinalizador pode afetar a maneira na qual o texto é analisado por alguns idiomas.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Se um valor de retorno estiver disponível, ele será usado pelo chamador.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Não permitir que os efeitos colaterais. Se esse sinalizador estiver definido, a avaliação da expressão não deve alterar nenhum estado de tempo de execução.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Permite que os pontos de interrupção durante a avaliação do texto. Se este sinalizador não for definido, em seguida, os pontos de interrupção são ignorados durante a avaliação do texto.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Permite que os relatórios de erro durante a avaliação do texto. Se este sinalizador não for definido, em seguida, erros não são relatados para o host durante a avaliação.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indica a expressão será avaliada para um contexto de código em vez de executar a própria expressão|  
  
 `ppe`  
 [out] Retorna a expressão de depuração para o texto especificado.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método cria uma expressão de depuração para o texto especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)